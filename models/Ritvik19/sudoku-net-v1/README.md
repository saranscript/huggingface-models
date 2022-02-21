## Overview
Sudoku Net V1 model solves sudoku puzzles. It was developed to see the performance of machine learning applications on solving sudokus.
This model is trained on [1 million Sudoku games](https://www.kaggle.com/bryanpark/sudoku) dataset provided on kaggle by [Kyubyong Park](https://www.kaggle.com/bryanpark)

## Usage
The Huggingface Hub architecture currently does not support inference from this model since it is unable to determine this model’s pipeline type. Thus, it is recommended to use as easy-to-use PyPI package [ai-sudoku-solver](https://pypi.org/project/ai-sudoku-solver/).
The package can also be found on [GitHub](https://github.com/Ritvik19/ai-Sudoku-Solver)

```bash
pip install ai-sudoku-solver
```

Instantiate a SudokuSolver object

```python
from ai_sudoku_solver import SudokuSolver

solver = SudokuSolver("Ritvik19/sudoku-net-v1")
```

Call the model on your puzzles

```python
puzzle = np.array([[
    [0, 0, 4, 3, 0, 0, 2, 0, 9],
    [0, 0, 5, 0, 0, 9, 0, 0, 1],
    [0, 7, 0, 0, 6, 0, 0, 4, 3],
    [0, 0, 6, 0, 0, 2, 0, 8, 7],
    [1, 9, 0, 0, 0, 7, 4, 0, 0],
    [0, 5, 0, 0, 8, 3, 0, 0, 0],
    [6, 0, 0, 0, 0, 0, 1, 0, 5],
    [0, 0, 3, 5, 0, 8, 6, 9, 0],
    [0, 4, 2, 9, 1, 0, 3, 0, 0]
]])
solution = solver(puzzle)
# array([[
#     [8, 6, 4, 3, 7, 1, 2, 5, 9],
#     [3, 2, 5, 8, 4, 9, 7, 6, 1],
#     [9, 7, 1, 2, 6, 5, 8, 4, 3],
#     [4, 3, 6, 1, 9, 2, 5, 8, 7],
#     [1, 9, 8, 6, 5, 7, 4, 3, 2],
#     [2, 5, 7, 4, 8, 3, 9, 1, 6],
#     [6, 8, 9, 7, 3, 4, 1, 2, 5],
#     [7, 1, 3, 5, 2, 8, 6, 9, 4],
#     [5, 4, 2, 9, 1, 6, 3, 7, 8]
# ]])
```