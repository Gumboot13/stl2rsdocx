# stl2rsdocx

**Open STL / 3MF / OBJ / DXF / STEP files in the *free* tier of DesignSpark Mechanical — no subscription, no install.**

The free **Explorer** tier of DesignSpark Mechanical can only import its own `.rsdocx` files, point-curve `.txt`, PCB IDF, and images. STL, 3MF, OBJ, STEP and the rest are locked behind the paid **Creator** tier. This little tool bridges that gap: it converts the formats Explorer *won't* open into the ones it *will*, so you can view — and often rebuild as editable solids — parts you download or export, for free.

It's a single Windows program. Download it, double-click, done.

---

## Download & run

1. Download **`stl2rsdocx_gui.exe`** from the [Releases](../../releases) page.
2. Double-click it. No install, no dependencies.
3. (First run) Windows SmartScreen may warn about an unknown publisher — click **More info -> Run anyway**. This is normal for unsigned hobby tools.

---

## What you get

The tool produces two kinds of output, depending on what you need:

| Output | File | What it's for |
| --- | --- | --- |
| **Mesh view** | `.rsdocx` | A clean-looking mesh you can open, view, measure, and screenshot in free Explorer. **View only - not editable.** |
| **Rebuild curves** | `.txt` (point-curve) | Editable geometry you import into Explorer, then **Fill / Revolve / Blend** into a real solid and **Save As `.rsdocx`**. |

The rebuild path works because Explorer's modelling tools (Fill, Pull/Revolve, Blend) are free - so DSM's own kernel builds the solid from the curves this tool hands it.

---

## Supported files

| Drop in... | You get... | Notes |
| --- | --- | --- |
| **STL** (`.stl`) | mesh `.rsdocx` (+ optional rebuild curves) | binary & ASCII |
| **3MF** (`.3mf`) | mesh `.rsdocx` (+ optional rebuild curves) | reads its own units |
| **OBJ** (`.obj`) | mesh `.rsdocx` (+ optional rebuild curves) | |
| **DXF** (`.dxf`) | 2D profile `.txt` | import, Fill, Pull to thickness |
| **STEP** (`.stp`, `.step`) | exact face-loop `.txt` | flat/round parts only - no organic/B-spline shapes |

---

## How to use it

1. **Add files** - drag them onto the window, drop them on the `.exe` icon, or click **Add files... / Add folder...**.
2. **Set options** - every control has a hover tooltip explaining it. The main ones:
   - **Smooth seams below ... deg** - hides triangle lines for a clean view. *View only - not editable.*
   - **Rebuild curves** - pick a mode to export editable curves instead (see below).
   - **Weld tolerance** - leave at `0` (auto); fixes 3MF files that otherwise show stray triangles.
3. **Convert** - output appears next to your file (or in a folder you choose).

---

## Getting an *editable* part (free) in DesignSpark

Mesh imports are **view-only** - you can't edit them, and "Turn to Solid" is a paid feature. To get an editable part for free, use a **Rebuild curves** mode. It writes a `.txt` you import into Explorer (**File -> Open**, pick the point-curve text file), then build natively:

| Mode | Best for | In DesignSpark |
| --- | --- | --- |
| **Flat faces (Fill)** | flat / boxy parts | import -> **Fill** each loop -> stitch -> **Save As `.rsdocx`** |
| **Revolved (profile+axis)** | round / symmetric parts | Fill the profile -> **Pull -> Revolve** about the axis |
| **Freeform (cross-sections)** | varying / organic parts | **Blend / Loft** through the section loops |
| **DXF** | plates, brackets, panels | Fill the outline -> **Pull** to thickness |
| **STEP** | downloaded CAD solids | Fill the flats, Pull/Revolve the round faces -> stitch |

Closed loops Fill into faces; once the faces enclose a volume, DSM stitches them into a solid you save as `.rsdocx`.

---

## What it can and can't do (honest version)

- **Yes** - View any STL/3MF/OBJ cleanly in free Explorer.
- **Yes** - Rebuild flat, round, and prismatic parts into editable solids, free.
- **No** - Smooth seams isn't editable. It's a clean *picture*, not a solid. Use Rebuild curves to edit.
- **No** - Twisted / warped faces won't Fill. A genuinely tapered or twisted wall has no flat loop to fill - those parts aren't practical to rebuild this way.
- **No** - Organic / freeform STEP (B-spline surfaces) is skipped, not faked.

If you mostly need to edit complex or organic downloads inside DSM, the paid **Creator** tier (which opens STL/STEP directly and converts meshes to solids) is the right tool. For free editing *outside* DSM, FreeCAD / Fusion (personal) / Blender all handle meshes well. This tool is the free bridge *into DSM* for flat, round and prismatic parts.

---

## Notes

- **Windows only** (it's a Windows `.exe`). Nothing is installed and nothing phones home - it just reads your file and writes a converted one next to it.
- Always keep your original files.
- Not affiliated with, endorsed by, or supported by RS Group / DesignSpark or Ansys. The `.rsdocx` and point-curve formats were reverse-engineered for interoperability. "DesignSpark Mechanical" is a trademark of its respective owner. Use at your own risk.

