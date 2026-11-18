[README.md](https://github.com/user-attachments/files/35042191/README.md)
# QHurst
Estimating Hurst Ecponent with Quantum Wavelets
# Hurst Exponent Estimation with Quantum Wavelets

Research code by **Brani Vidakovic**, Department of Statistics, Texas A&M University.

QHurst estimates the Hurst exponent $H$ of fractional Brownian motion from repeated preparations of a **single amplitude-encoded path**. Each preparation encodes the same realization. A one-qubit mirror extension removes the endpoint jump before the wavelet transform, and wavelet energy shares across the fine scales are used to estimate $H$.

The code covers decimated and nondecimated quantum wavelet transforms, direct computational-basis readout, ancilla-based Hadamard level tests, and maximum-likelihood amplitude estimation (MLAE). The numerical study compares the readouts on the same records at equal preparation-query budgets. MLAE uses coherent access to both the preparation circuit and its inverse.

## Quick start

Place the Python scripts and the notebook in the repository root. From that directory, set up a Python 3 environment with NumPy, SciPy, Matplotlib, PyWavelets, JupyterLab, and Qiskit 2.x. Install Qiskit Aer if you plan to run the finite-shot Aer checks.

```bash
python -m pip install numpy scipy matplotlib PyWavelets jupyterlab "qiskit>=2,<3"
python qwt.py
python -m jupyter lab
```

`qwt.py` runs the gate-list checks described in Appendix A of the manuscript. In JupyterLab, open the `.ipynb` companion notebook and run it from top to bottom. The notebook illustrates Hurst estimation from simulated ancilla counts using the nondecimated transform with the Symmlet 4 (sym4) filter. The main readout comparison in the paper uses Daubechies 2 (db2).

For Aer checks, install the simulator in the same environment:

```bash
python -m pip install qiskit-aer
```

## Reproducing the paper

| Files | Experiment or output |
| --- | --- |
| `qwt.py` | Wavelet circuits, gate-list checks, and Qiskit circuit generation |
| `bench.py` | Gate-count calculations for Table 1 |
| `boundary.py`, `hurst.py` | Boundary energy and Hurst estimation results for Tables 2 and 3 |
| `lengths.py` | Record-length experiment for Figure 5 |
| `readout2.py`, `readout3.py`, `countfit2.py`, `mlae.py`, `analyze3.py`, `ischeck.py` | Readout comparisons, sparse-count fits, and the importance-sampling check for Tables 4 and 5 |
| `fig_*.py` | Scripts for assembling the manuscript figures |

The main simulation uses paths of length 512, mirrored to length 1,024, and a six-level fitting window. The reported readout comparisons use ideal simulation. The gate counts in Table 1 use the decomposition specified in the manuscript and exclude preparation of the input path.

## Citation

Brani Vidakovic. *Hurst Exponent Estimation with Quantum Wavelets*. Preprint.

<!-- Add the arXiv URL when the preprint is posted. -->
