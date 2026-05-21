This repository contains a Jupyter notebook tutorial for manual calibration and
imaging of VLA Ka-band (36 GHz) spectral line data, created for the NRAO
Synthesis Imaging Workshop (SIW) in 2026. The tutorial walks through reduction
of a D-array observation of the the SiS J=2-1 and HC3N J=4-3 rotational
transitions toward the AGB star IRC+10216 (CW Leo). It covers all steps of
manual calibration from importing the data, bandpass and gain calibration,
continuum subtraction, and imaging the spectral line data cubes with
`tclean`/`iclean`.

Installation
------------
First, either (1) download the repository by clicking the green "**Code**" button
in the upper right corner of the GitHub page and selecting "Download ZIP" or (2)
clone the repository directly using the commands below:

```bash
git clone https://github.com/autocorr/siw26_line_casa_guide
cd siw26_line_casa_guide
```

This repository uses the Python environment manager
[`uv`](https://docs.astral.sh/uv/) to ensure that the exact same library
dependency versions are installed.

Before you install it, however, please note that *if you are running this
tutorial on the NRAO cluster with an NRAO user account*, you should first set
the following pathes in your shell configuration file (e.g., `~/.bashrc` for
Bash). In that case, make two directories `uv-cache` and `uv-data` somewhere on
the Lustre filesystem and then add the following pathes to your shell
configuration file (e.g., `~/.bashrc`):

```bash
export UV_CACHE_DIR=<path>/<to>/uv-cache
export UV_DATA_DIR=<path>/<to>/uv-data
```

and then run:

```
source $HOME/.bashrc
```

If you don't have `uv` installed already, you can install from the command line
by running:

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
source $HOME/.local/bin/env
```

You can now use use `uv` to create an environment and install the necessary
dependencies:

```bash
uv venv --python=3.12
source .venv/bin/activate
uv sync  # install libraries and versions from `uv.lock`
```

and start the Jupyter notebook server:

```bash
uv run jupyter notebook
```

Open the notebook browser interface and select the file `siw26_line_casa_guide.ipynb`.

License
-------
Copyright Brian Svoboda (2026) under the GNU General Public License (GPL)
version 3 license. A copy of the license can be found in the file `LICENSE`.
