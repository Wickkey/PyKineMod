# Dual_Degree_Project

# PyKineMod

PyKineMod is a Python-based tool for kinetic model identification and parameter estimation using the Incremental Identification method proposed by Nirav et al. and Amrhein et al. This tool provides a flexible framework for defining chemical reactions, generating and specifying rate laws, and performing identification tasks to study the behavior of chemical systems using Concentration Data. It aims to determine the reaction mechanism of complex multiple reaction systems.

## Table of Contents

- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Examples](#examples)
- [Documentation] (#documentation)
<!-- - [Contributing](#contributing)
- [License](#license) -->

## Features

- Kinetic model identification: PyKineMod allows users to identify the kinetic model for chemical reactions by fitting experimental Concentration data to a set of potential reaction mechanisms.
- Parameter estimation: The tool enables estimation of the kinetic parameters of the identified model by minimizing the differences between the model predictions and experimental observations.
- Flexible reaction definition: Users can define the chemical reactions of interest using a user-friendly syntax, specifying the stoichiometry, reactants, products, and reaction rate expressions.
- Rate law generation: PyKineMod generates rate laws for the specified reactions by analyzing the stoichiometric matrix that can assist user in generating Candidate Ratelaws.
- Incremental Identification method: The tool employs the Incremental Identification method, which iteratively identifies and refines the kinetic model based on experimental data collected at different experimental conditions. This method is computationally effective.
- Fine Tunings with Simultaneous Method: This tool offers the flexibility to finetune the model with guesses obtained by Incremental Method. Simultaneous methods are computationally expensive. Having access to better guesses and lesser search space leads to effective estimates than the brute-force simultaneous approach.
- Simulation and prediction: PyKineMod allows users to simulate the behavior of chemical systems using the identified kinetic model and predict the response under different experimental conditions.

## Installation

To use this simulation tool, follow these steps:

1. Clone the repository:

   ```bash
   git clone https://github.com/Wickkey/Dual_Degree_Project.git
   ```

2. Install the required dependencies:

   ```bash
   pip install -r requirements.txt
   ```

3. You're ready to start using PyKineMod!

## Usage

To use PyKineMod, you need to define the chemical reactions of interest, specify the experimental data, and perform the model identification and parameter estimation steps. The tool provides a user-friendly API for these tasks.

Here's an example of how to use the simulation tool:

```python
import numpy as np
import Incremental, CandidateRateLaws

# Candidate rate laws for the first reaction
def cand_ratelaw11(y, K):
    Ca, Cb, _, _, _, _ = y
    return K[0] * np.ones(Ca.shape)

def cand_ratelaw12(y, K):
    Ca, Cb, _, _, _, _ = y
    return K[0] * Cb

# ... Add other candidate rate laws for the first reaction

def cand_ratelaw19(y, K):
    Ca, Cb, _, _, _, _ = y
    return K[0] * Ca * Ca * Cb * Ck

# Candidate rate laws for the second reaction
# ... Define candidate rate laws for the second reaction

# Candidate rate laws for the third reaction
# ... Define candidate rate laws for the third reaction

# Define other variables and data

candidates_list = [
    [cand_ratelaw11, cand_ratelaw12, ..., cand_ratelaw19],
    # Add candidate rate laws for the second reaction
    # Add candidate rate laws for the third reaction
]

# Candidate Ratelaws could also be generated through Ratelaw generator
# Define candidate rate laws
cand_ratelaws1 = CandidateRateLaws(N[0], type="Irreversible")
cand_ratelaws2 = CandidateRateLaws(N[1], type="Irreversible")
cand_ratelaws3 = CandidateRateLaws(N[2], type="Reversible")

candidates_list = [cand_ratelaws1, cand_ratelaws2, cand_ratelaws3]

# Create the Incremental object
inc = Incremental(N, Mw, V, Winhat, uin, uout, n0)

# Add concentration data
inc.add_concentration_data(c_normal, time)

# Estimate parameters
res = inc.estimate_parameters(candidates_list, method='rate_based', conf_int=False, metric='aicc', plot=True, bootstraps=100)
```

Please note that you'll need to complete the code by defining the candidate rate laws for the second and third reactions and providing the necessary variables and data for the model.


For more details on the available methods and data formats, please refer to the code documentation.

## Examples

The repository includes a set of examples that demonstrate the usage of the simulation tool in different scenarios. These examples cover different reactions , rate laws, and simulation settings. You can find the examples in the `Demonstration.ipynb` file of the repository. inside the PyKineMod folder

<!-- 
## Contributing

Contributions to this project are welcome! If you have any ideas, suggestions, or bug reports, please open an issue or submit a pull request. Your contributions will help improve the functionality and usability of the identification tool.

When contributing, please follow the existing coding style and ensure that your changes are well-documented. Also, make sure to run the tests and verify that everything is functioning correctly.

## License

This project is licensed under the [MIT License](LICENSE). You are free to use, modify, and distribute the code for both commercial and non-commercial purposes.

---

Thank you for using the Chemical Reactor Simulation tool! If you have any questions or need further assistance, please don't hesitate to reach out. -->

## Documentation

[Link to documentation](https://docs.google.com/document/d/1vthe8qXFL6YI4ObJa73sy7PPq03XgkrF21hnXM2UMtA/edit?usp=sharing)
