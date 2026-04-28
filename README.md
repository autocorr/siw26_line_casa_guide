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
```
git clone https://github.com/autocorr/siw26_line_casa_guide
cd siw26_line_casa_guide
```
and use `uv` to create an environment and install the necessary dependencies:
```
uv venv --python=3.13
source .venv/bin/activate
uv sync  # install libraries and versions from `uv.lock`
```
and start the Jupyter notebook server:
```
uv run jupyter notebook
```
Open the notebook browser interface and select the file `siw26_line_casa_guide.ipynb`.

License
-------
Copyright Brian Svoboda (2026) under the General Public License (GPL) version 3 license.
