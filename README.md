# Hangman Player

This project implements a Hangman-playing system that combines a Hidden Markov Model (HMM) with a Q-learning agent. The HMM models positional letter emission probabilities trained on a word corpus (Baum–Welch / forward-backward), and the RL agent (Q-learning) uses the HMM plus word-filtering strategies to choose letters during gameplay.

The notebook `hangman_HMM_RL.ipynb` contains the full implementation: HMM training, a Hangman environment, a Q-learning agent, training loop, plots, and evaluation on a test set.

## Key Components

- `hangman_HMM_RL.ipynb` — Main notebook implementing everything (HMM training, Hangman environment, Q-learning agent, training loop, evaluation, and visualizations).
- `data/corpus.txt` — Raw corpus of 50000 words used for training.
- `data/test.txt` — Test set used for final evaluation.
- `models/` — Directory used by the notebook to save trained models (`hangman_hmm_cleaned.pkl`, `hangman_agent.pkl`).

## Features

- HMM trained per word length with K-means initialization and Baum–Welch iterations.
- Position-specific emission probabilities P(letter | state, position).
- Hangman environment with configurable max wrong guesses and reward structure.
- Q-learning agent that blends HMM predictions, word-filtering frequencies, and learned Q-values.
- Training metrics and evaluation on a held-out test set with plots.

## Dependencies

The notebook requires the following Python packages (tested on Python 3.8+):

- numpy
- scikit-learn
- matplotlib
- pickle (standard library)

You can install the main packages with pip:

```bash
python -m venv .venv
source .venv/bin/activate
pip install --upgrade pip
pip install numpy scikit-learn matplotlib
```

## How to run

1. Open the notebook in JupyterLab / Jupyter Notebook or VS Code's Jupyter interface:

   - jupyter notebook hangman_HMM_RL.ipynb

2. Run cells sequentially. Typical workflow in the notebook:
   - Clean the corpus (the notebook writes `cleaned_corpus.txt`).
   - Train the HMM (this may take some time depending on corpus size and HMM parameters).
   - Train the Q-learning agent (notebook includes a training loop with progress prints and saves the agent to `models/hangman_agent.pkl`).
   - Evaluate the agent on `data/test.txt` and view plots.