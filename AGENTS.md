> **First-time setup**: Hãy customize file này theo sản phẩm của bạn.

# Documentation project instructions

## About this project

- Đây là site tài liệu (MDX + YAML frontmatter)
- Cấu hình ở `docs.json`
- Chạy `mint dev` để preview
- Chạy `mint broken-links` để check link

## Generating images (logo, section art)

- Use **Stitch MCP** (server: `user-stitch`) to generate logo and section images.
- Call `generate_screen_from_text` with **`modelId`: `"GEMINI_3_PRO"`** (Pro model) for best quality. Required: `projectId`, `prompt`. Optional: `deviceType`.
- Download image from `screenshot.downloadUrl` (response or `get_screen`) and save to local (`logo/` or `images/`). Use only local paths in docs (e.g. `/logo/ammh-logo.png`), never embed HTTPS URL.
- Full flow: see **STITCH_MCP.md** in repo root.

## Terminology

{/* Add product-specific terms and preferred usage */}
{/* Example: Use "workspace" not "project", "member" not "user" */}

## Style preferences

{/* Add any project-specific style rules below */}

- Use active voice and second person ("you")
- Keep sentences concise — one idea per sentence
- Use sentence case for headings
- Bold for UI elements: Click **Settings**
- Code formatting for file names, commands, paths, and code references

## Content boundaries

{/* Define what should and shouldn't be documented */}
{/* Example: Don't document internal admin features */}
