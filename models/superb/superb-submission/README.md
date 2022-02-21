# SUPERB Submission Template

Welcome to the [SUPERB Challenge](https://superbbenchmark.org/challenge)! SUPERB is a collection of benchmarking resources to evaluate the capability of a universal shared representation for speech processing. It comes with a benchmark on the publicly available datasets and a challenge on a secret/not released hidden dataset. In SUPERB Challenge, a challenging hidden dataset is newly recorded to evaluate the ultimate generaliziblity across various tasks and data.

You can participate the challenge by simply submitting your self-supervised (SSL) pretrained models (model definition & pretrained weights), and we benchmark it with the hidden dataset. This repository constains useful tools to let you easliy [submit](https://superbbenchmark.org/submit) your models ***privately*** for evaluation to [the challenge hidden-set leaderboard](https://superbbenchmark.org/leaderboard?track=constrained&subset=Hidden+Dev+Set).

1. Generate a submission template
2. Validate the format/interface correctness of your model
3. Upload to Huggingface's Hub (privately)
4. Submit the upload information to [SUPERB website](https://superbbenchmark.org/submit)

#### Note 1.

We accept pre-trained models in PyTorch by default. If you wish to submit upstreams in non-PyTorch frameworks, please [fill this form](https://docs.google.com/forms/d/e/1FAIpQLSe52jYL2Yk9oYqXfg_Bg0Sjp01a6HSLUhY5VohsZOE5sNmgsw/viewform)!

#### Note 2.

If you are not feasible to submit the pre-trained model, please [fill this form](https://docs.google.com/forms/d/e/1FAIpQLSdA44nArlIDfGV63WwtwXer4WAPQO1aBwEpAjDSNjbMQN-GJQ/viewform) for us to see how to help!

## Quickstart

### 1. Create an account and organization on the Hugging Face Hub

First create an account on the Hugging Face Hub and you can sign up [here](https://huggingface.co/join) if you haven't already! Next, create a new organization and invite the SUPERB Hidden Set Committee to join. You will upload your model to a repository under this organization so that members inside it can access the model which is not publicly available.

* [superb-hidden-set](https://huggingface.co/superb-hidden-set)

### 2. Create a template repository on your machine

The next step is to create a template repository on your local machine that contains various files and a CLI to help you validate and submit your pretrained models. The Hugging Face Hub uses [Git Large File Storage (LFS)](https://git-lfs.github.com) to manage large files, so first install it if you don't have it already. For example, on macOS you can run:

```bash
brew install git-lfs
git lfs install
```

Next, run the following commands to create the repository. We recommend creating a Python virtual environment for the project, e.g. with Anaconda:

```bash
# Create and activate a virtual environment
conda create -n superb-submit python=3.8 && conda activate superb-submit
# Install the following libraries
pip install cookiecutter huggingface-hub==0.0.16
# Create the template repository
cookiecutter git+https://huggingface.co/superb/superb-submission
```

This will ask you to specify your Hugging Face Hub username, password, organisation, and the name of the repository:

```
hf_hub_username [<huggingface>]:
hf_hub_password [<password>]:
hf_hub_organisation [superb-submissions]:
repo_name [<my-superb-submissions>]:
```

This will trigger the following steps:

1. Create a private dataset repository on the Hugging Face Hub under `{hf_hub_organisation}/{repo_name}`
2. Clone the repository to your local machine
3. Add various template files, commit them locally to the repository, and push them to the Hub

The resulting repository should have the following structure:

```
my-superb-submission
├── LICENSE
├── README.md               <- The README with submission instructions
├── cli.py                  <- The CLI for validating predictions etc
└── requirements.txt        <- The requirements packages for the submissions
├── expert.py               <- Your model definition
└── model.pt                <- Your model weights
```

### 3. Install the dependencies

The final step is to install the project's dependencies:

```bash
# Navigate to the template repository
cd my-superb-submission
# Install dependencies
python -m pip install -r requirements.txt
```

That's it! You're now all set to start pretraining your speech models - see the instructions below on how to submit them to the Hub.


## Submitting to the leaderboard

To make a submission to the [leaderboard](https://superbbenchmark.org/leaderboard?subset=Hidden+Dev+Set), there are 4 main steps:

1. Modify `expert.py` and change `model.pt` so we can initialize an upstream model following the [challenge policy](https://superbbenchmark.org/challenge#Upstream-Specification) by:

    ```python
    upstream = UpstreamExpert(ckpt="./model.pt")
    ```

    ***Package Dependency:*** Note that we only install `torch` package so far by following the above steps. If your model needs more packages, you can modify the `requirement.txt` to meet your need and install them inside the current conda environment. We will install the packages you list in the `requirement.txt` before initializing the upstream model.

2. Validate the upstream model's interface meets the requirements in the [challenge policy](https://superbbenchmark.org/challenge#Upstream-Specification). If everything is correct, you should see the following message: "All submission files validated! Now you can make a submission."

    ```
    python cli.py validate
    ```

3. Push the model to the Hub! If there are no errors, you should see the following message: "Upload successful!"

    ```
    python cli.py upload "commit message: my best model"
    ```

4. [Make a submission at SUPERB website](https://superbbenchmark.org/submit) by uniquely indentifying this uploaded model with the following information, which can be shown by:

    ```
    python cli.py info
    ```

    - Organization Name
    - Repository Name
    - Commit Hash (full 40 characters)

After you finish the above 4 steps. You will see a new entry in your [SUPERB profile page](https://superbbenchmark.org/profile) (need login) which does not have any benchmark numbers yet. Please wait for us to finetuned it on the hidden dataset and get the benchmark results. The results will be revealed within one week. Please stay tuned!
