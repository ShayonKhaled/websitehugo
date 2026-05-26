# SKILL: Replace WordPress image URLs with local `static/img/posts` links

Summary
- Convert image links in Markdown files that point to https://www.shayonkhaled.com (WordPress uploads) into local paths under `/img/posts/<post-folder>/<filename>`.
- Assumes the user will download images and place them under `static/img/posts/<post-folder>/` where `<post-folder>` corresponds to the post's slug or folder name.

Intent / When to use
- Use this skill when migrating posts from WordPress to Hugo and you want images to be served from the Hugo `static` folder instead of the original WordPress domain.

Inputs
- Workspace with Markdown files (Hugo content files).
- Knowledge of the target `post-folder` for each post (usually the Markdown filename or URL slug).
- Images copied into `static/img/posts/<post-folder>/` with reasonable filenames (same names as on WordPress preferred).

Outputs
- Updated Markdown files where external image URLs pointing to `www.shayonkhaled.com` are replaced with local paths such as `/img/posts/<post-folder>/<filename>`.

Step-by-step workflow (agent-friendly)
1. Locate target Markdown files:
   - Search `content/**` for image links that contain `www.shayonkhaled.com` or the WordPress uploads path. Example patterns to search for:
     - `https://www.shayonkhaled.com/wp-content/uploads/`
     - `https://shayonkhaled.com/wp-content/uploads/`
2. For each Markdown file found, determine the `post-folder` where its images will live. Common heuristics:
   - If the file is `content/blogs/2021/boiboi.md`, use `boiboi` as `post-folder`.
   - If the file is in a folder (e.g., `content/blogs/2024/my-post/index.md`), use the folder name `my-post`.
   - If post slug is ambiguous, ask the user for the desired folder name.
3. Extract the remote image filename from the URL. Example source URL:
   - `https://www.shayonkhaled.com/wp-content/uploads/2021/10/boiboidrop.jpg` → filename `boiboidrop.jpg`
4. Build the replacement path: `/img/posts/<post-folder>/<filename>`.
5. Replace the occurrence in the Markdown file. Replace variants:
   - Markdown image: `![](https://www.shayonkhaled.com/...)` → `![](/img/posts/<post-folder>/filename)`
   - HTML `<img src="https://...">` → `<img src="/img/posts/<post-folder>/filename">`
   - Hugo shortcodes like `{{< figure src="https://..." caption="..." >}}` → `{{< figure src="/img/posts/<post-folder>/filename" caption="..." >}}`
6. Save the file and repeat.

Regex patterns (capture examples)
- Match full WP uploads URL and capture filename:
  - Regex: `https?://(?:www\.)?shayonkhaled\.com/wp-content/uploads/[^)"']*/([^)"'\\s]+)`
  - Capture group 1 contains the filename (or path tail).
- Match Markdown image syntax:
  - `!\[[^\]]*\]\((https?://(?:www\.)?shayonkhaled\.com/wp-content/uploads/[^)]+)\)`

Automation examples
- Quick `perl` (POSIX / Git Bash / WSL) example that replaces URLs with a fixed `post-folder` name (replace `POSTFOLDER` with the folder):

```bash
# from repo root; backups are created with .bak
perl -0777 -pe "s_https?://(?:www\.)?shayonkhaled\.com/wp-content/uploads/(?:[^")]+/)?([^\)\"']+)_/img/posts/POSTFOLDER/$1_g" -i.bak content/**/*.md
```

- PowerShell replace (recursively for Windows PowerShell):

```powershell
Get-ChildItem -Path content -Recurse -Filter *.md | ForEach-Object {
  $text = Get-Content -Raw -Path $_.FullName
  $new = [regex]::Replace($text, 'https?://(?:www\.)?shayonkhaled\.com/wp-content/uploads/(?:[^\)"'']+/)?([^\)"'']+)', '/img/posts/POSTFOLDER/$1')
  if ($new -ne $text) { Set-Content -Path $_.FullName -Value $new }
}
```

Notes about automation
- These commands assume a single `POSTFOLDER` per run. If different posts need different folders, script must determine `post-folder` per file (see below).
- Safer approach: produce a per-file mapping (CSV or JSON) from Markdown file → post-folder, then apply replacements file-by-file using the filename capture.

Per-file scripted approach (pseudo-code)
1. Build a mapping of Markdown file → post-folder (heuristics or user input).
2. For each file:
   - Read contents
   - Replace matches of WP uploads URLs with `/img/posts/<post-folder>/$1`
   - Save changes

Edge cases & decision points
- If remote filename conflicts (same filename across posts), store them in distinct post folders to avoid overwrite.
- If image filenames changed during download, update replacements to the new filename.
- If images are referenced with query params (e.g., `?ver=123`), strip query params in replacement or include them as needed.
- If theme uses special shortcodes or attributes (e.g., `figure` with `src` param named differently), adapt replacement to that shortcode syntax.

Testing & verification
- Run `hugo server` locally and load the post pages to verify images load from `/img/posts/...` paths.
- Search for remaining external references:

```bash
grep -R "shayonkhaled.com/wp-content/uploads" -n content || echo "no external img links found"
```

- Confirm files exist under `static/img/posts/<post-folder>/` and filenames match the replaced paths.

Example prompts to use this skill
- "Replace all WordPress image links in `content/blogs/2021/boiboi.md` using post-folder `boiboi`."
- "Scan `content/blogs` for external images and generate a proposed mapping file (Markdown file → post-folder)."
- "Run replacements for files listed in mapping.csv where column A is markdown path and column B is post-folder."

Follow-ups the agent should ask the user (if ambiguous)
- Should I assume the `post-folder` is the Markdown filename (without extension)?
- Do you want me to create missing `static/img/posts/<post-folder>/` directories or only update Markdown after you place images?
- Do you want backups of files before modifications? (default: yes, create `.bak` files)

Implementation notes for authoring the skill
- Keep replacements idempotent: if a file already points to `/img/posts/...` do not change it.
- Prefer per-file replace when possible to avoid wrong folder assignments.

Done — save this SKILL.md and run your chosen automation with careful backups.
