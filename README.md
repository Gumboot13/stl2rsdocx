# stl2rsdocx

**Turn STL / 3MF / OBJ / DAE / STEP into editable solids in the *free* tier of DesignSpark Mechanical — no subscription, no install.**

Free **Explorer** can't *import* STL/3MF/OBJ — that's locked to the paid Creator tier. But once a mesh is already inside DSM as a native `.rsdocx`, free Explorer **can** open it, and its **Convert to Solid** command turns it into a real editable solid.

This tool supplies the missing piece: it converts your mesh into a `.rsdocx` body that Explorer opens. From there you right-click → **Convert to Solid**, and you've got an editable part — entirely free.

It's a single Windows program. Download it, double-click, done.

---

## The free workflow

1. **Convert** your `.stl` / `.3mf` / `.obj` to `.rsdocx` with this tool (leave *Smooth seams* **off**).
2. **Open** the `.rsdocx` in free DesignSpark Mechanical Explorer.
3. In the structure tree, **right-click the mesh body → Convert to Solid → Merge faces**.
4. You now have an **editable solid** — push/pull faces, cut holes, combine, save.

That's it. The converter is the bridge *in*; DSM's own free Convert to Solid does the rest.

> **Why this tool is needed:** free Explorer's import menu only accepts `.rsdocx`, point-curve `.txt`, PCB IDF, and images — not STL/3MF/OBJ. This tool writes the `.rsdocx` so you can skip the paid import.

---

## Download & run

1. Download **`stl2rsdocx_gui.exe`** from the [Releases](../../releases) page.
2. Double-click it. No install, no dependencies.
3. (First run) Windows SmartScreen may warn about an unknown publisher — click **More info -> Run anyway**. Normal for unsigned tools.

---

## Supported files

| Drop in... | You get... | Then in DSM |
| --- | --- | --- |
| **STL** (`.stl`) | mesh `.rsdocx` | open → Convert to Solid → editable solid |
| **3MF** (`.3mf`) | mesh `.rsdocx` | open → Convert to Solid → editable solid |
| **OBJ** (`.obj`) | mesh `.rsdocx` | open → Convert to Solid → editable solid |
| **DAE** (`.dae`) | mesh `.rsdocx` | open → Convert to Solid → editable solid |
| **STEP** (`.stp`, `.step`) | exact face curves `.txt` **+** mesh `.rsdocx` | Fill / Revolve the curves, **or** Convert to Solid the mesh |
| **DXF** (`.dxf`) | 2D profile `.txt` | open → Fill → Pull to thickness |
| **SVG** (`.svg`) | 2D profile `.txt` | open → Fill → Pull to thickness |

*IGES or 3DS? Re-export them as STEP / OBJ — the tool will tell you so when you try.*

STL/OBJ carry no units, so the tool auto-detects suspiciously tiny parts (saved in metres) and scales them, and recenters parts to the origin so they're visible on open.

---

## How to use it

1. **Add files** - drag onto the window, drop on the `.exe` icon, or **Add files... / Add folder...**.
2. **Set options** (every control has a hover tooltip):
   - **Smooth seams** - leave **OFF** if you're going to Convert to Solid (it needs the full triangle topology). It's only for a cleaner *view* when you just want to look.
   - **Weld tolerance** - leave at `0` (auto).
   - **Analyze** button - optional pre-flight: reports how cleanly a mesh will rebuild.
3. **Convert** - the output appears next to your file.

---

## Convert to Solid: Merge faces vs Do not merge

When you right-click the mesh in DSM:

- **Merge faces** ← use this. Combines coplanar triangles into single flat faces, so you get clean editable surfaces (one face per real surface) instead of thousands of triangle-faces.
- **Do not merge faces** - keeps every triangle as its own face. Messy; rarely wanted.


---

## What to expect (honest version)

- **Editable, but faceted.** Convert to Solid builds a solid from triangles, so a "round" hole is a many-sided polygon and there's no parametric "change this diameter." You can push/pull, cut and combine — it's just not the original smooth CAD. That's a limit of meshes (no curves or design history survive STL/3MF export), not of this tool.
- **Dense meshes are slow.** Lots of triangles = lots of faces. Use the **Reduce** slider first if Convert to Solid struggles.
- **Want true curves / parametric edits?** Use **STEP** (it keeps real geometry — the exact-curve export Fills into clean parametric faces), or Fusion/Blender for organic shapes.

### Alternative: rebuild curves (no Convert to Solid needed)
The tool can also export editable **rebuild curves** (`.txt`) from a mesh — Fill / Revolve / Blend them natively into a clean parametric solid. Handy for flat, round, and prismatic parts. **DXF, SVG, and STEP always export as curves**; STEP curves are exact CAD geometry.

---

## Notes

- **Windows only.** Nothing is installed and nothing phones home — it reads your file and writes a converted one next to it.
- Always keep your original files.
- Tested signed-out on free Explorer: opening a converted `.rsdocx` and Convert to Solid both work without a subscription. DSM versions/menus vary — if Convert to Solid isn't on your right-click menu, check you're on a current DSM build.
- Not affiliated with, endorsed by, or supported by RS Group / DesignSpark or Ansys. The `.rsdocx` and point-curve formats were reverse-engineered for interoperability. "DesignSpark Mechanical" is a trademark of its respective owner. Use at your own risk.
