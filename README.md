# LeeMykland Jump Detection in Python

This Python code implements the jump detection method described in the paper "Jumps in Equilibrium Prices and Market Microstructure Noise" by Suzanne S. Lee and Per A. Mykland.

## Overview

The code provides two main functions:

-   `movmean(v, kb, kf)`:  Calculates a moving average with specified backward and forward window sizes.
-   `LeeMykland(S, sampling, significance_level=0.01)`: Implements the Lee-Mykland jump detection test.

## Functions

### `movmean(v, kb, kf)`

Computes the moving average of a list of values.

#### Arguments

-   `v` (list(float)): List of values.
-   `kb` (int): Number of elements to include before the current position.
-   `kf` (int): Number of elements to include after the current position.

#### Returns

-   list(float):  List of the same size as `v` containing the mean values. Non-existing elements at the edges are substituted with `NaN`.

### `LeeMykland(S, sampling, significance_level=0.01)`

Implements the Lee-Mykland jump detection test.

#### Arguments

-   `S` (list(float)): An array containing prices, where each entry corresponds to the price sampled every 'sampling' minutes.
-   `sampling` (int): Minutes between entries in `S`.
-   `significance_level` (float): Defaults to 1% (0.01).

#### Returns

-   `pandas.DataFrame`: A pandas DataFrame containing a row covering the interval \[t\_i, t\_i+sampling] with the following columns:
    -   `J`:   Binary value indicating a jump with direction (sign).
    -   `L`:   L statistics.
    -   `T`:   Test statistics.
    -   `sig`: Volatility estimate.

## Usage

1.  **Import the code:**

    ```python
    from leemykland import LeeMykland
    ```

2.  **Prepare your price data:**

    -   Ensure your price data is in a list or array format.
    -   Determine the sampling frequency of your data (in minutes).
