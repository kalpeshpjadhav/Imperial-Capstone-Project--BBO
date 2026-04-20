# BBO Capstone Project

Bayesian Optimization for black-box functions across 2D to 8D using Gaussian Process regression, Latin Hypercube Sampling, and UCB acquisition.

## Overview

This repository contains the code, logs, and documentation for a capstone project on black-box optimization. The goal is to search for the best solution to unknown objective functions using as few evaluations as possible.

## Why this project?

Black-box optimization is useful when the objective function is expensive, noisy, or difficult to model directly. This project explores how Bayesian Optimization can guide the search process across multiple rounds and across different dimensions.

## Approach

The optimisation pipeline uses:

- Gaussian Process regression as a surrogate model.
- Matérn kernel for flexible function fitting.
- StandardScaler for input and output scaling in higher dimensions.
- Latin Hypercube Sampling to generate candidate points.
- Upper Confidence Bound (UCB) to choose the next point to evaluate.

The strategy evolved over ten rounds. Early rounds used a simpler GP-UCB setup, while later rounds added better scaling, stronger regularization, more optimizer restarts, and larger candidate pools to improve stability in higher dimensions.

## Key Features

- Supports benchmark functions from 2D to 8D.
- Tracks optimisation progress across rounds.
- Records predicted mean, uncertainty, and UCB score.
- Includes diagnostic checks for overfitting.
- Designed for analysis, reflection, and reproducibility.

## How It Works

1. Fit a Gaussian Process model to the observed data.
2. Generate a candidate pool using Latin Hypercube Sampling.
3. Predict the mean and uncertainty for each candidate.
4. Compute the UCB score.
5. Select the highest-scoring point.
6. Add the new point to the dataset and repeat.

## Performance

Performance was evaluated using:
- Best objective value found.
- Round at which the best value was found.
- Training R² of the GP surrogate.
- Uncertainty range.
- Diagnostics for overfitting.

A results table for all eight benchmark functions can be added here once the final logs are complete.

## Repository Contents

- `README.md` — project overview.
- `datasheet.md` — dataset documentation.
- `model_card.md` — optimisation approach documentation.
- `notebooks/` — analysis and experimentation notebooks.
- `data/` — query logs and results.
- `src/` — source code for the optimisation workflow.

## Requirements

Typical dependencies include:
- Python 3.10+
- NumPy
- Pandas
- SciPy
- Scikit-learn
- Matplotlib or Plotly

## Installation

```bash
git clone https://github.com/your-username/bbo-capstone-project.git
cd bbo-capstone-project
pip install -r requirements.txt
```

## Usage

Run the optimisation notebook or script that fits the GP model, generates candidates, and selects the next query point.

```bash
python main.py
```

If using notebooks:

```bash
jupyter notebook
```

## Limitations

This project assumes the objective functions are smooth enough for a Gaussian Process surrogate. It may perform less well on discontinuous, highly noisy, or very high-dimensional problems.

The search is also limited by the sampled candidate set, so it may miss narrow optima outside the explored regions.

## Documentation

Additional documentation is available in:
- Datasheet for the dataset.
- Model card for the optimisation approach.
- Experimental logs and round summaries.


## Contact
Kalpesh Jadhav, kalpeshjadhav.jde@gmail.com
