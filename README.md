# tesse-gym

Provides a Python interface for reinforcement learning using the TESSE Unity environment and the OpenAI Gym toolkit.


Treasure Hunt |  Navigation
:----------:|:---------------:
![](docs/hunt-1.gif) | ![](docs/nav-1.gif)

## Installation

### From Source
Using [Anaconda](https://www.anaconda.com/distribution/#download-section) or [miniconda](https://docs.conda.io/en/latest/miniconda.html) is highly recommended. Python 3.7 is required.

1. If using conda, create a new environment

```sh
conda create -n tess_gym python=3.7
conda activate tess_gym
```

2. Clone this Repository
```sh
git clone git@github.mit.edu:TESS/tesse-gym.git
cd tesse-gym
```

3. Install Dependencies. *NOTE*: This requires access to [tesse-interface](https://github.mit.edu/TESS/tesse-interface). 

```sh
# install requirements
pip install -r requirements.txt
```


4. Install tesse-gym

```sh
python setup.py install
```

## Getting Started

### Treasure Hunt Training

Treasures (fruits) are randomly placed throughout a TESSE environment. The agent must collect as many of these treasures as possible within the alloted time (default is 100 timesteps). A treasure is considered found when it is within `success_dist` (default is 2m) of the agent and within it's feild of view. The agent acts on a first-person RGB, depth, and semantic segmentation images as well as relative pose from starting location.

See the [example notebook](baselines/stable-baselines-ppo.ipynb) to get started.

### Evaluation

See the [GOSEEK Challenge](https://github.mit.edu/TESS/goseek-challenge) landing page for details on evaluation and submission.


## Other Tasks

### Navigation

The agent must move throughout it's environment without collisions. See  the [example notebook](baselines/navigation-training.ipynb) to get started.

### New Tasks
At a minimum, a new task will inherit `tess_gym.TesseGym` and impliment the following:

```python
class CustomTask(TesseGym):
    @property
    def action_space(self):
        pass
    
    def apply_action(self, action):
        pass
    
    def compute_reward(self, observation, action):
        pass
```

### Disclaimer

DISTRIBUTION STATEMENT A. Approved for public release. Distribution is unlimited.

This material is based upon work supported by the Under Secretary of Defense for Research and Engineering under Air Force Contract No. FA8702-15-D-0001. Any opinions, findings, conclusions or recommendations expressed in this material are those of the author(s) and do not necessarily reflect the views of the Under Secretary of Defense for Research and Engineering.

© 2020 Massachusetts Institute of Technology.

MIT Proprietary, Subject to FAR52.227-11 Patent Rights - Ownership by the contractor (May 2014)

The software/firmware is provided to you on an As-Is basis

Delivered to the U.S. Government with Unlimited Rights, as defined in DFARS Part 252.227-7013 or 7014 (Feb 2014). Notwithstanding any copyright notice, U.S. Government rights in this work are defined by DFARS 252.227-7013 or DFARS 252.227-7014 as detailed above. Use of this work other than as specifically authorized by the U.S. Government may violate any copyrights that exist in this work.
