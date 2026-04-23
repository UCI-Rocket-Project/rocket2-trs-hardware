# rocket2-trs-hardware

**TRS (Telemetry Radio System) hardware design files for MOCH4**, UCI Rocket Project's bi-propellant liquid methalox rocket.

This repository contains the KiCad schematics, PCB layouts, and other files, along with full hardware documentation.

---

## 📄 Documentation

Full hardware documentation is hosted at:

> **[INSERT MKDOCS LINK HERE]**

---

## 📁 Repository Structure

```
rocket2-trs-hardware/
├── trs-docs/               # MkDocs documentation source
│   ├── mkdocs.yml
│   └── docs/
├── production/             # Fabrication outputs (Gerbers, BOM, CPL)
├── UCIRP-KiCAD-Lib/        # Shared KiCad library (submodule)
├── rocket2-trs-hardware.kicad_pcb
├── rocket2-trs-hardware.kicad_sch
└── rocket2-trs-hardware.kicad_pro
```

---

## 🛠 Tools

- **KiCad** for schematic capture and PCB layout
- **MkDocs** with Material theme for documentation

---

## 🔧 Getting Started

### Cloning with submodules

```bash
git clone --recurse-submodules https://github.com/UCI-Rocket-Project/rocket2-trs-hardware.git
```

If you already cloned without submodules:

```bash
git submodule update --init --recursive
```

### Building docs locally

```bash
cd trs-docs
pip install mkdocs mkdocs-material
mkdocs serve
```

Then open `http://127.0.0.1:8000` in your browser.

---

## 👥 Team

UCI Rocket Project — Liquids Team, Avionics

[uciRocketProject.org](https://www.ucirocketproject.org) · [GitHub Org](https://github.com/UCI-Rocket-Project)
