---

# TOPSIS Method Implementation

This Python program implements the **TOPSIS (Technique for Order Preference by Similarity to Ideal Solution)** method, which is used for multi-criteria decision analysis. It helps in evaluating and ranking alternatives based on several criteria and weights.

## Requirements

- Python 3.x
- Required libraries:
  - `pandas`
  - `numpy`

You can install the necessary libraries using:

```bash
pip install pandas numpy
```

## Functionality

The program performs the following tasks:
1. **Input Validation**: It validates the input CSV file, the weights, and the impacts.
2. **Normalization**: It normalizes the decision matrix using vector normalization.
3. **Weighted Normalization**: Each attribute of the normalized decision matrix is multiplied by its corresponding weight.
4. **Ideal and Negative Ideal Solutions**: It computes the ideal and negative ideal solutions based on the given impacts (`+` for beneficial, `-` for non-beneficial).
5. **Distance Calculation**: The program calculates the distance of each alternative from the ideal and negative ideal solutions.
6. **TOPSIS Score Calculation**: A score is computed for each alternative, which indicates its closeness to the ideal solution.
7. **Ranking**: The alternatives are ranked based on their scores, with the best alternative ranked 1.
8. **Output**: The results (scores and rankings) are saved in a CSV file.

## Usage

### Command-Line Usage

The program is run through the command line with the following parameters:

```
topsis <inputFileName> <Weights> <Impacts> <resultFileName>
```

### Parameters

- `<inputFileName>`: Path to the input CSV file containing the decision matrix. The first column should contain the alternatives, and the subsequent columns should contain the criteria.
- `<Weights>`: Comma-separated list of weights for each criterion (e.g., `0.25,0.35,0.4`).
- `<Impacts>`: Comma-separated list of impacts for each criterion (either `+` for beneficial or `-` for non-beneficial, e.g., `+, -, +`).
- `<resultFileName>`: Path to the output CSV file where the results will be saved. This file will contain the score and rank for each alternative.

### Example

```bash
python topsis.py data.csv "0.4,0.3,0.3" "+,-,+" result.csv
```

This will:
1. Read data from `data.csv`
2. Use weights `0.4, 0.3, 0.3` for the criteria
3. Apply impacts `+, -, +` to the criteria
4. Save the results (including the calculated scores and ranks) to `result.csv`

### Input File Format

The input CSV file should have the following format:

| Alternative | Criterion 1 | Criterion 2 | Criterion 3 |
|-------------|-------------|-------------|-------------|
| A1          | 3.5         | 2.1         | 8.4         |
| A2          | 4.2         | 1.9         | 7.5         |
| A3          | 5.1         | 2.8         | 6.2         |

- The first column should contain the names of the alternatives.
- The remaining columns should contain the values of the criteria for each alternative.

### Output File Format

The output CSV file will contain the following columns:

| Alternative | Criterion 1 | Criterion 2 | Criterion 3 | Score   | Rank |
|-------------|-------------|-------------|-------------|---------|------|
| A1          | 3.5         | 2.1         | 8.4         | 0.825   | 1    |
| A2          | 4.2         | 1.9         | 7.5         | 0.713   | 2    |
| A3          | 5.1         | 2.8         | 6.2         | 0.665   | 3    |

- `Score`: The computed score indicating the proximity to the ideal solution.
- `Rank`: The rank based on the score.
