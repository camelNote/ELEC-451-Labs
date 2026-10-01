# AGENTS.md

ELEC 451 (Power Electronics) homework report — Assignment 1. There is no software to
build; the deliverable is a LaTeX report plus PSIM simulation evidence. The formatting
and answer conventions below were negotiated with the user in earlier sessions — follow
them instead of inventing a style.

## Layout and sources of truth

- `Assignment01.pdf` (root) — the assignment handout. Get question text with
  `pdftotext -layout`. Never overwrite it; the compiled report is `LateX/Assignment01.pdf`.
- `GBJ15005_GBJ1510(GBJ).pdf` — diode datasheet used for Q1(e).
- `LateX/Assignment01.tex` — the whole report; all final answers go here.
- `LateX/Q1.md`, `Q2.md`, `Q3.md` — per-question drafts. `Q1.md` and `Q2.md` are
  fully mirrored into the tex; `Q3.md` covers parts (a)--(b); Q4 has no draft yet.
- `LateX/figures/` — every `\includegraphics` image, referenced as `figures/...`, so
  always compile from `LateX/`.
- `Simulation/` — PSIM artifacts. `Q1.psimsch` is the schematic; `Q1.smv` is a 32 MB
  binary waveform file (never read it as text); `Q1_Circuit.png` / `Q1c.png` are the
  captures copied into `LateX/figures/`.

## Build and verify

`latexmk` does not work here (MiKTeX cannot find Perl). From `LateX/`, run `pdflatex`
twice, check the log, then remove artifacts:

```powershell
pdflatex -enable-installer -interaction=nonstopmode -halt-on-error Assignment01.tex
pdflatex -enable-installer -interaction=nonstopmode -halt-on-error Assignment01.tex 2>&1 | Select-String "Warning|Error|Output written"
Remove-Item *.aux, *.log, *.out, *.toc -ErrorAction SilentlyContinue
```

To eyeball a page, render it as PNG and delete the preview afterwards (do not leave
`preview*.png` or `.aux`/`.log` files behind):

```powershell
pdftoppm -png -r 100 -f 3 -l 3 Assignment01.pdf preview   # then view preview-3.png
Remove-Item preview*.png -ErrorAction SilentlyContinue
```

## Answer conventions

- Draft each answer in `LateX/Qn.md` and mirror it into `Assignment01.tex`; keep both in
  sync after every edit — the user expects both updated.
- Final answers: one line with the calculation, then the boxed result as a separate
  equation (`\boxed{}`). In the `.md` drafts use a `(box)` line.
- Output variables use a lowercase `o`: `v_o`, `V_o`, `I_o`, `P_o`, `V_{o,\text{avg}}` —
  never `V_O`. Applies to prose and equations; the `\Vo`/`\VoRipple` macros are defined
  to render the lowercase form.
- Figure captions are one short sentence. Wide waveforms use `width=\textwidth`,
  schematics `0.85\textwidth`.
- Body-text paragraphs are separated by a vertical gap (`\parskip`), with no first-line
  indent; set once in the preamble (`\parindent=0pt`, `\parskip=0.5\baselineskip plus
  2pt minus 1pt`). Don't add manual `\vspace` between paragraphs. Display equations keep
  their normal spacing.
- Keep answers concise: don't describe components or add unrequested considerations.
  Commentary the user wants is phrased explicitly, e.g. `Comment: ...`.
- Cite datasheet values by page/section, e.g. "(p.~2, Thermal characteristics)".
- Title block and header are settled: course name only in the header, `Assignment #1` in
  `\Huge\bfseries`, no due date, tight name/student-number/date. Don't restyle them.
- Q1, Q2, and Q3 parts (a)--(b) are done, while the remaining Q3/Q4 parts still
  contain `% --- Your solution here ---` placeholders.
- Assignment circuit figures were extracted from the handout with `pdfimages -png`
  (lossless), not screenshots; PSIM captures are copied from `Simulation/` into
  `LateX/figures/`.
- `python` works for quick numeric checks; `python3` does not.
