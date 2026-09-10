# Development Guide & Commands Cheatsheet

A beginner-friendly guide to running, previewing, and editing the **The Shattered Pale** documentation and wiki site.

---

## 1. Quick Start: Previewing Your Site

MkDocs runs inside an isolated Python environment called a **virtual environment** (`venv`). This keeps dependencies isolated from your main operating system.

### Option A: The Standard Way (Activate `venv`)
Open your terminal in the project root (`the-shattered-pale`) and run:

```bash
# 1. Activate the Python virtual environment
source venv/bin/activate

# 2. Start the local development server
mkdocs serve
```

> **How to know it worked:** Your terminal prompt will show `(venv)` at the beginning.
> Open your web browser and go to: **[http://127.0.0.1:8000/](http://127.0.0.1:8000/)**
> 
> When done, press `Ctrl + C` in the terminal to stop the server, and type `deactivate` to exit the virtual environment.

---

### Option B: The One-Liner (Without Activating)
If you just want to run MkDocs directly without activating the virtual environment:

```bash
./venv/bin/mkdocs serve
```

---

## 2. Common MkDocs Commands

| Command | What It Does |
| :--- | :--- |
| `mkdocs serve` | Starts the local live-reload server at `http://127.0.0.1:8000`. Any edits you save in markdown files will automatically refresh in your browser! |
| `mkdocs serve -a 127.0.0.1:8080` | Starts the server on a different port (8080) if port 8000 is already in use. |
| `mkdocs build` | Generates the static production website files into the `public/` directory. |
| `mkdocs --help` | Displays help information and a list of all commands. |

---

## 3. Project Structure & Where Things Live

Here is an overview of key files and directories in this repository:

```text
the-shattered-pale/
├── mkdocs.yml             # Main MkDocs configuration (site name, theme, navigation menus)
├── content/
│   ├── setting/           # ALL active markdown pages live here! (docs_dir)
│   │   ├── index.md       # Homepage / Wiki overview
│   │   ├── history/       # History & lore markdown files
│   │   ├── species/       # Species documentation
│   │   ├── pantheons/     # Deities and pantheons
│   │   ├── geography/     # Continents, regions, and maps
│   │   └── factions/      # Organizations and factions
│   ├── raw_export/        # Raw exports from LegendKeeper (backup / source material)
│   └── modules/           # Adventure modules or supplementary documents
├── public/                # Auto-generated HTML output (created when running `mkdocs build`)
└── venv/                  # Python virtual environment containing MkDocs and plugins
```

---

## 4. Writing & Formatting Content

MkDocs Material supports enhanced Markdown features. Here are some useful tips:

### Callout Boxes (Admonitions)
Use these to highlight GM notes, lore snippets, or warnings:

```markdown
!!! note "GM Note"
    This is secret information or a special tip for game masters.

!!! info "Player Lore"
    Common knowledge available to characters native to this region.

!!! warning "Dangerous Terrain"
    Traveling through this area requires constitution checks.
```

### Adding New Pages
1. Create your new markdown file inside `content/setting/` (e.g. `content/setting/geography/new-region.md`).
2. Add the page to the navigation menu in `mkdocs.yml` under the `nav:` section:
   ```yaml
   nav:
     - Geography:
         - New Region: geography/new-region.md
   ```
3. Save `mkdocs.yml`—the live server will automatically reload with your new page in the menu!

---

## 5. Troubleshooting & FAQ

#### Q: `zsh: command not found: mkdocs`
**Cause:** The virtual environment is not activated, so your shell cannot find `mkdocs`.  
**Fix:** Run `source venv/bin/activate` first, or run `./venv/bin/mkdocs serve`.

#### Q: `Address already in use: ('127.0.0.1', 8000)`
**Cause:** Another process (or a previous MkDocs server) is already using port 8000.  
**Fix:** Run on a different port:
```bash
mkdocs serve -a 127.0.0.1:8001
```

#### Q: How do I install missing plugins or packages?
If a new MkDocs plugin or theme is needed:
```bash
source venv/bin/activate
pip install <package-name>
```

