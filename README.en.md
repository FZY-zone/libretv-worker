# LibreTV · Cloudflare Workers Single-File Edition

A **self-contained `worker.js`**: no installation, no build step, no static asset upload.
Copy the entire `worker.js`, paste it into the Cloudflare Worker online editor, and it runs.

> This project is based on [LibreTV](https://github.com/LibreSpark/LibreTV) (Next.js rewrite, **AGPL-3.0**),
> originally by LibreSpark. This repository only repackages it into a single paste-ready file; the license remains AGPL-3.0.
>
> 中文说明见 [README.md](README.md).

> **⚠️ This file is large (8.66 MB), so GitHub cannot preview it online (it shows "we can't show files that are this big"). This is normal.**
> Get the code in either way:
> - **Easiest**: open the `worker.js` page → click the **download (⬇) icon** (top right) to save it → open in any text editor → `Ctrl+A`, `Ctrl+C`.
> - **Raw**: click the **Raw** button → the raw code opens in the browser → `Ctrl+A`, `Ctrl+C` (or right-click "Save as").

## Size

- Raw `worker.js`: ~8.7 MB, **gzip ~2.24 MB**
- Below the Cloudflare **free plan Worker limit of 3 MB (gzip)** — deployable on a free account
- 61 static assets (JS/CSS/icons, etc.) are inlined, so no external files are needed

## Deploy (~1 minute, all in the browser)

1. Sign in to the Cloudflare dashboard → **Workers & Pages** → **Create** → **Create Worker**
2. Give it a name (e.g. `libretv`) → click **Deploy**
3. After deploying, click **Edit code**
4. Select and delete the default code, then paste the **entire contents of `worker.js`**
   (GitHub can't preview this large file; see the "⚠️" note above to get the code via the download icon or Raw)
5. Click **Deploy** (top right)
6. Open the assigned `xxx.workers.dev` URL to see the LibreTV search page

> To use your own domain: Workers → your Worker → **Settings → Domains & Routes → Add → Custom Domain**, and pick a domain already in your account.

## Optional: Environment variables (under "Settings → Variables and Secrets")

| Variable | Type | Description |
|---|---|---|
| `PASSWORD` | **Secret** | Access password; if unset, the site is open without a password |
| `DEFAULT_SOURCES` | **Text** | Preset VOD sources; new visitors get them automatically with no manual setup |
| `60S_API_BASE` | Text | Homepage trending/recommendation source (unset shows "failed to load recommendations"; search still works) |
| `REQUEST_TIMEOUT` | Text | Upstream request timeout (ms), default 8000 |

`DEFAULT_SOURCES` is a JSON array. The example below shows the **format only; the URL is a placeholder and does not work**:

```json
[
  {"name":"Example Source","url":"https://demo.example.com/api.php/provide/vod/from/demo","isAdult":false}
]
```

> Please find and fill in a legal, working API yourself. This project does not provide any video content or collection sources.

## Disclaimer

- This project is a front-end aggregation tool for technical learning only; it **does not include or provide any video content**.
- The copyright, availability, and compliance of third-party APIs you configure are entirely your responsibility.
- Do not use for commercial purposes; for personal learning and research only.

## License

AGPL-3.0 (see upstream LibreTV).
