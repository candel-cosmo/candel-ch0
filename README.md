# candel-ch0

Cepheid-calibrated H0 forward model for CANDEL. A probe package for
[CANDEL](https://github.com/candel-cosmo/CANDEL), part of the
[candel-cosmo](https://github.com/candel-cosmo) organisation. It imports the
core `candel` library; the core never imports it. See the
[CANDEL README](https://github.com/candel-cosmo/CANDEL#how-the-repositories-fit-together)
for how the repositories fit together.

## What it provides

Forward model of the SH0ES Cepheid host galaxies with a rigorous
selection-function treatment and reconstructed peculiar velocities
(`model.which_run = "CH0"`). Also includes peculiar-velocity covariance
matrices (`pv_covariance.py`), mocks (`mock.py`) and JWST forecast mocks
(`scripts/JWST_mock/`).

## Install

Clone this repository next to the CANDEL core and install both, core first:

```bash
git clone https://github.com/candel-cosmo/CANDEL.git
git clone https://github.com/candel-cosmo/candel-ch0.git
cd CANDEL
python -m venv venv_candel && source venv_candel/bin/activate
pip install -e .
pip install --no-deps -e ../candel-ch0
```

Data, results and the machine-local `local_config.toml` live in the CANDEL
checkout. Python code finds it through the installed `candel`
(`candel.util.CANDEL_ROOT`); shell scripts use `$CANDEL_ROOT`, defaulting to
`../candel`.

## Layout

- `candel_ch0/` — the package
- `configs/` — run configurations
- `scripts/` — preprocessing, mocks and submission helpers
- `papers/` — scripts and notebooks behind each paper
- `tests/` — tests (`pytest`)

## Papers

- `papers/CH0/` — A 1.8 per cent measurement of $H_0$ from Cepheids alone, [arXiv:2509.09665](https://arxiv.org/abs/2509.09665)

## Run

```bash
python ../candel/scripts/runs/main.py --config configs/config_CH0.toml
```

Batch grids are defined in `candel_ch0/specs.py` and built with the core's
`scripts/runs/generate_tasks.py`.

## License

MIT; see `LICENSE`.
