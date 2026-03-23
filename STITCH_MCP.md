# Stitch MCP – Generate images for docs

Use the **Stitch MCP** (server: `user-stitch`) to generate logo and section images with the **Pro model** for best quality.

## Image generation flow

1. **Project**
   - Use an existing project from `list_projects`, or create one with `create_project`.
   - For **image-only** outputs, a **TEXT_TO_UI** or **TEXT_TO_UI_PRO** project works (e.g. projectId `3286376044318738792`).

2. **Generate screen (image)**
   - Tool: `generate_screen_from_text`
   - **Required:** `projectId` (string, no `projects/` prefix), `prompt` (string).
   - **Recommended for quality:** `modelId`: `"GEMINI_3_PRO"` (Pro model).
   - Optional: `deviceType` (`DESKTOP` | `MOBILE` | `TABLET` | `AGNOSTIC`).

   Example:

   ```json
   {
     "projectId": "3286376044318738792",
     "prompt": "A single standalone image: minimal app logo for Algo Market Making & Hedge. Icon only, no text. Dark background, accent color green #16A34A. Geometric mark combining candlestick chart with shield outline. Square, centered, professional fintech.",
     "modelId": "GEMINI_3_PRO",
     "deviceType": "DESKTOP"
   }
   ```

3. **Download image to local**
   - Response includes `outputComponents[].design.screens[]` with `screenshot.downloadUrl`.
   - **Luôn tải về và lưu local** — không dùng HTTPS URL trực tiếp trong docs.
   - Ví dụ: `curl -sL -o logo/ammh-logo.png "<downloadUrl>"` hoặc lưu vào `images/` (vd: `images/section-hedge.png`).

4. **Dùng trong docs**
   - Chỉ dùng **đường dẫn local**: `/logo/xxx.png`, `/images/xxx.png`.
   - Logo site: cấu hình `docs.json` → `logo.light` / `logo.dark` trỏ tới `/logo/...`.
   - Ảnh trong trang: `<img src="/images/xxx.png" alt="..." />` hoặc `![alt](/images/xxx.png)`.

## Model IDs (Stitch)

| modelId            | Use case        |
|--------------------|-----------------|
| `GEMINI_3_PRO`     | Higher quality (recommended for logos/images) |
| `GEMINI_3_FLASH`   | Faster, lighter |
| Omit or `MODEL_ID_UNSPECIFIED` | Server default |

There is no "banana" model in the schema; use **GEMINI_3_PRO** for the Pro model.

## Notes

- Generation can take 1–2 minutes. Do not retry on connection errors; check with `list_screens` or `get_screen` later.
- Screens with `screenType`: `"IMAGE"` are image-only outputs.
