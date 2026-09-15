# AstroVigil

Quality-Aware Exoplanet Transit Detection from Stellar Light Curves.

## Overview

AstroVigil is an automated pipeline for detecting possible exoplanet transit signals in stellar light-curve data.

The system combines quality checks, iterative detrending, BLS/TLS transit search, scientific candidate validation, confidence scoring, and submission CSV generation.

## Features

* Stellar light-curve processing
* Quality-aware preprocessing
* Iterative detrending
* BLS transit detection
* TLS detection when available
* BLS fallback when TLS is unavailable or fails
* Transit feature validation
* Candidate confidence ranking
* Period, depth, and duration estimation
* Automated submission CSV generation
* Scientific validation tests

## Pipeline

```text
Light Curve
    ↓
Quality Checks
    ↓
Iterative Detrending
    ↓
BLS / TLS Search
    ↓
Transit Validation
    ↓
Confidence Ranking
    ↓
Submission CSV
```

## Validation Features

The validation layer checks:

* Observed transit count
* Odd/even transit depth consistency
* Duration plausibility
* Possible secondary eclipse
* Out-of-transit variability
* Quality-flag overlap
* Systematic-period proximity
* Data limitations

The system reports evidence and warnings transparently instead of rejecting a candidate using only one feature.

## Technologies

* Python
* NumPy
* Pandas
* SciPy
* Matplotlib
* BLS
* TLS
* Pytest
* Git and GitHub

## Project Structure

```text
backend/
    scientific/
        transit_features.py
        validation.py
        tls_search.py

tests/
    test_validation.py
    test_tls_search.py

README.md
```

## Testing

The project includes automated tests for scientific validation and TLS/BLS search behaviour.

Run the tests using:

```bash
pytest
```

## Output

The final submission contains:

* star_id
* prediction
* confidence
* period
* depth_ppm
* duration_hours

## Limitations

The quality of the final result depends on the available light-curve data, sampling, noise level, and the reliability of the detected transit candidate.

Future work includes improved single-transit detection, better uncertainty estimation, and more advanced stellar variability modelling.
