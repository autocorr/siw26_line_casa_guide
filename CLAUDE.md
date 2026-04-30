# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with
code in this repository.

You are an expert in radio astronomy and the CASA software package for
calibrating and imaging interferometric radio astronomy observations, in
particular data taken with the Very Large Array (VLA). Always ask clarifying
questions before giving detailed answers.

## Project overview

This repository contains a Jupyter notebook CASA tutorial for spectral line
data reduction, created for the NRAO Synthesis Imaging Workshop (SIW26, 2026).
The tutorial walks through manual calibration and imaging of a VLA Ka-band
(36 GHz) observation of IRC+10216 (CW Leo), demonstrating reduction of SiS
J=2-1 and HC3N J=4-3 spectral lines.

The primary artifact is `siw26_line_casa_guide.ipynb`. The `docs/` directory
holds related reference wiki guides (gitignored, for local context only).
Pay special attention to the `docs/vla_irc10216_casa_guide.wiki` that the
Jupyter notebook is modeled after. The other `.wiki` files contain other
relevant examples of calibrating and imaging VLA data using CASA.

A human-readable summary of all five wiki files (content, key procedures, and
important caveats extracted from each) is at `docs/summary.txt`.

## Commands

To validate changes to the Jupyter notebook, use:

```bash
uv run nbqa pyflakes siw26_line_casa_guide.ipynb
```

## Environment setup

This project uses `uv` for dependency management with Python 3.12.

```bash
uv venv --python=3.12
source .venv/bin/activate
uv sync
```

To launch the notebook:
```bash
uv run jupyter notebook
```

## Notebook structure

The notebook (`siw26_line_casa_guide.ipynb`) follows this calibration/imaging
pipeline order:

1. Imports and CASA version check
2. SDM-BDF to MS conversion (`importasdm`)
3. Flagging known bad data (`flagdata`)
4. Split and time-average (`mstransform`)
5. Data inspection (`listobs`, `plotms`)
6. Prior calibrations (antenna positions, requantizer, Tsys, opacity)
7. Bandpass and delay calibration
8. Gain calibration (phase, amplitude)
9. Flux scale bootstrap and application (`fluxscale`, `applycal`)
10. Split calibrated target, continuum subtraction (`uvcontsub`)
11. Weight calculation (`statwt`)
12. Velocity regridding (`mstransform`)
13. Imaging and deconvolution (`tclean`): dirty image, interactive CLEAN, auto-multithresh
14. Continuum imaging
15. Moment maps and analysis

## CASA usage patterns

The notebook is written to run both inside a monolithic CASA shell and as a
standard Jupyter notebook using the modular `casatasks`/`casatools` packages.
The detection pattern is:

```python
try:
    casalog.version
    is_running_within_casa = True
except NameError:
    is_running_within_casa = False
```

Tasks are imported as `import casatasks as tasks` and called as `tasks.<taskname>(...)`.
Tools are accessed via `casatools.<ToolClass>()`.

## Key data files (not in repo)

- Raw SDM-BDF: project code `TDRW0001` from NRAO Science Archive
- Pre-processed MS: `TDRW0001_10s.ms` (~1 GB, time-averaged to 10s)
- Target MS variables defined in notebook: `vis_target = "irc10216.ms"`,
  `vis_contsub = "irc10216.ms.contsub"`
