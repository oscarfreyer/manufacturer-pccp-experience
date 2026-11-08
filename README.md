# Run the PCCP analyses

Use Python 3.12. Run these commands from this folder.

## Set up the environment

```bash
python3.12 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements-public.txt
python -m ipykernel install --prefix "$VIRTUAL_ENV" --name python3 --display-name "Python 3"
```

## Run all five notebooks

```bash
python -m jupyter nbconvert --to notebook --execute --inplace \
  --ExecutePreprocessor.kernel_name=python3 \
  notebooks/post_submission_analysis.ipynb \
  notebooks/pre_submission_analysis.ipynb \
  notebooks/survey_irr_analysis.ipynb \
  notebooks/interview_analysis.ipynb \
  notebooks/census_analysis.ipynb
```

The notebooks run independently. To use Jupyter interactively, open a notebook with the Python 3 kernel, restart the kernel and run all cells in order. The working directory may be this folder or `notebooks/`.

Inputs are read from `data/`. Twelve result CSVs are written to `outputs/`, replacing earlier results with the same names. Plots appear in the executed notebooks. The input files are not modified.
