- CASA spectral line tutorial for the NRAO Synthesis Imaging Workshop (2026).

Installation
------------
This repository uses the Python package manager `uv` to ensure that the exact
same library dependency versions are installed. If you don't have it installed
already, you can install from the command line with:
```bash
# Install `uv` if itsnot already installed.
curl -LsSf https://astral.sh/uv/install.sh | sh
source $HOME/.local/bin/env
```
Now, clone the repository:
```bash
git clone https://github.com/autocorr/siw26_line_casa_guide
cd siw26_line_casa_guide
```
and use `uv` to create an environment and install the necessary dependencies:
```bash
uv venv --python=3.13
source .venv/bin/activate
uv sync  # install libraries and versions from `uv.lock`
```
and start the Jupyter notebook server:
```bash
uv run jupyter notebook
```
Open the notebook browser interface and select the file `siw26_line_casa_guide.ipynb`.

Note that the default cache directories for `uv` are in home (`~/.cache/uv`). If you
are using the NRAO network file system the home directory may fill up when
installing Python package depdencies. In that caase, add the following to your
shell configuration:
```bash
export UV_CACHE_DIR=<path>/<to>/uv-cache
export UV_DATA_DIR=<path>/<to>/uv-data
```

License
-------
Copyright Brian Svoboda (2026) under the General Public License (GPL) version 3 license.
