# PyRun

> Write. Run. Done.

A browser-based Python sandbox — no installs, no server, no setup. Just open the page and run Python instantly, powered by [Pyodide](https://pyodide.org) (WebAssembly).

---

## What it does

- **Run Python in the browser** — full CPython 3.12 via WebAssembly
- **Live output** — stdout, stderr, and exceptions displayed in a terminal-style console
- **Matplotlib plots** — rendered inline as images automatically
- **NumPy & Pandas** — preloaded and ready to use
- **Code editor** — syntax highlighting, line numbers, bracket matching, auto-indent (CodeMirror 6)
- **Snippets** — 6 presets to get started fast (NumPy, Pandas, Matplotlib, Fibonacci, and more)
- **Resizable panels** — drag the divider to adjust editor/console split
- **Zero dependencies** — single `index.html` file, deployable anywhere

---

## Included libraries

| Library | Version |
|---|---|
| Python | 3.12 (Pyodide 0.27) |
| NumPy | latest |
| Pandas | latest |
| Matplotlib | latest |

---

## Deploy

Upload `index.html` and `_headers` to any static host:

```bash
# Cloudflare Pages
npx wrangler pages deploy . --project-name pyrun

# Or drag-and-drop the folder into Cloudflare Pages dashboard
```

The `_headers` file sets the required COOP/COEP headers for Pyodide to work correctly.

---

## Run locally

```bash
python -m http.server 8080
```

Then open `http://localhost:8080`.

> **Note:** Do not open `index.html` directly via `file://` — browsers block the cross-origin requests that Pyodide requires.

---

## Sandbox constraints

User code runs inside the Pyodide WebAssembly sandbox. The following modules are blocked for security:

`requests` · `socket` · `subprocess` · `multiprocessing` · `urllib.request`

`input()` is also disabled as it would hang the browser tab.

---

## Files

```
pyrun/
├── index.html   # entire app — editor, runtime, UI
└── _headers     # COOP/COEP headers for Cloudflare Pages
```
