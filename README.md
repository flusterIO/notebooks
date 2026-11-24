# Absolute Time in Higher-Dimensional Geometry: notebooks

[![Paper on Zenodo](https://img.shields.io/badge/paper-Zenodo-1682D4)](https://zenodo.org/records/24504695)
[![DOI](https://img.shields.io/badge/DOI-10.5281%2Fzenodo.24504695-blue)](https://doi.org/10.5281/zenodo.24504695)
[![macOS app](https://img.shields.io/badge/macOS%20app-aog__explorer%200.0.4-black)](https://github.com/flusterIO/aog_explorer/releases/tag/0.0.4)
[![PyPI](https://img.shields.io/badge/PyPI-alpha--omega--gravity-3775A9)](https://pypi.org/project/alpha-omega-gravity/)

Companion notebooks for the paper
**[Absolute Time in Higher-Dimensional Geometry: Classically Simultaneous Relativity via an Unwrapped Kaluza–Klein Dimension](https://zenodo.org/records/24504695)**
by Andrew Mueller. Every result in the notebook is computed with the same functions that check the manuscript, from the `paper` subpackage of [`alpha-omega-gravity`](https://pypi.org/project/alpha-omega-gravity/) (imported as `physics`).

| Resource | Link |
|---|---|
| Paper (preprint, CC BY 4.0) | <https://zenodo.org/records/24504695> |
| macOS app (`aog_explorer`, release 0.0.4) | <https://github.com/flusterIO/aog_explorer/releases/tag/0.0.4> |
| Python package | <https://pypi.org/project/alpha-omega-gravity/> |

## The theory in brief

Special relativity is usually written with time as a fourth dimension. The paper instead writes relativistic kinematics with an additional, **non-compact spatial coordinate** $y$, in the spirit of an unwrapped Kaluza–Klein dimension:

- A body moving at speed $v$ is displaced along $y$ with slope $\partial_x y = \beta\gamma$, so the Lorentz factor is the hypotenuse of a right triangle: $\gamma = \sqrt{1 + (\partial_x y)^2}$.
- Time is not a dimension. It is a ratio of distances, carried as the length $w = c\tau$.
- Every inertial observer can recover **one absolute time** $\tau$. The relativity of simultaneity becomes a displacement along $y$, and moving clocks run at $1/\gamma$ without inserting time dilation by hand.
- Applied to gravity, space flows outward from a mass with $\beta^2 = 2Gm(R)/(c^2R)$. The $y$-graph is the Flamm paraboloid, and orbits, light bending and perihelion advance follow.

**What is and isn't claimed.** Where the construction is developed it is equivalent to special and general relativity, so those results are *consistency checks, not new predictions*. The one explicit step beyond general relativity, **Hypothesis M** (inertial resistance cut off at the cosmic horizon, giving an acceleration scale $g_0 = \kappa' c H_0$), is stated as a hypothesis and compared with the Milky Way and the SPARC galaxy sample in sections 10–11. Section 14 of the notebook lists what is established, assumed and open.

## What's in this repository

```
src/paper_walkthrough/
├── paper_walkthrough.ipynb      # the guided walkthrough (14 sections)
├── walkthrough_narration.txt    # script for the audio walkthrough
└── walkthrough_narration.m4a    # the narration, ~5 minutes
```

The notebook follows the paper section by section: the extra coordinate as a slope, classical simultaneity, the synchronization gauge, the Flamm embedding, one relation from planets to the Hubble radius, interiors (Buchdahl and Tolman VII), the scalar sector and the Cassini bound, rotation, orbits, Hypothesis M, co-scaling with $\gamma$, and a dimensional audit with a full consistency dashboard.

## Running the notebooks

You need Python 3.10 or newer.

```bash
git clone https://github.com/flusterIO/notebooks.git
cd notebooks

python3 -m venv .venv
source .venv/bin/activate          # Windows: .venv\Scripts\activate
pip install -r requirements.txt

jupyter lab src/paper_walkthrough/paper_walkthrough.ipynb
```

Then **Run → Run All Cells**. Open the notebook from its own folder (JupyterLab does this for you); the data paths in the settings cell are relative to it.

### Settings cell

The second code cell holds every setting you might change:

| Setting | Purpose |
|---|---|
| `LOCAL_PACKAGE_PATH` | Set to a local checkout of the package if you are not using the PyPI release. |
| `VIDEO_URL` | Optional YouTube link for a companion video. Leave empty to skip. |
| `ROTATION_CURVE_DATA` | Milky Way rotation-curve file (`rc_results.npz`) used in section 10. |
| `SPARC_DATA_DIR` | Folder with SPARC data for section 11. |
| `TTS_ENGINE`, `TTS_VOICE` | Speech engine for regenerating the narration. |

### Optional data

- **SPARC (section 11).** Download `SPARC_Lelli2016c.mrt` and `Rotmod_LTG.zip` from <https://astroweb.case.edu/SPARC/>, unzip the latter into `Rotmod_LTG/`, and point `SPARC_DATA_DIR` at the folder (default `~/sparc_cache`). Without the data, section 11 prints a notice and skips; everything else still runs.
- **Milky Way curve (section 10).** The notebook loads `rc_results.npz` from `ROTATION_CURVE_DATA`. This file is not in this repository yet, so add it or update the path before running section 10.

### Audio walkthrough

The notebook generates narration from `walkthrough_narration.txt` the first time it runs (macOS built-in `say`, or `pip install kokoro soundfile` elsewhere) and reuses the audio afterwards. To change the wording, edit the text file and delete the `.m4a`.

## Viewing on GitHub

GitHub renders notebooks, including the LaTeX in the text cells. Two limits apply:

- **Figures appear only if outputs are saved in the file.** To refresh them after changing the notebook, run it and save:
  ```bash
  jupyter nbconvert --to notebook --execute --inplace src/paper_walkthrough/paper_walkthrough.ipynb
  ```
- **Embedded audio and video do not play on GitHub.** Use the [`.m4a` file](src/paper_walkthrough/walkthrough_narration.m4a) directly, or run the notebook locally.

## Citation

> Mueller, A. *Absolute Time in Higher-Dimensional Geometry: Classically Simultaneous Relativity via an Unwrapped Kaluza–Klein Dimension.* Zenodo. <https://doi.org/10.5281/zenodo.24504695>
