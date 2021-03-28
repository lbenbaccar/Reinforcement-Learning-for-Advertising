# Reinforcement Learning for Advertising

### Files
Before explaining the project, here are the description of each file. 
| Files | Description |
| ------ | ------ |
| `Reinforcement Learning for Advertising.ipynb` | The notebook project |

### Use case : deploying ads
Every B2C Company needs to roll out ads to sell it's newest features to their potential clients. Much effort goes into designing advertising campaigns and their posts, but we can never know before starting the campaign what is the best way to sell our brand to our potential clients. This is why most of the time many versions of the same ad are designed, then put in competition against each other during the campaign before the best strategy stabilizes.

<img src="https://github.com/lbenbaccar/Reinforcement-Learning-for-Advertising/blob/main/example.jfif"/>

For reasons that can be explained (or not) with statistical modeling, one of the ads may be consistently better than the other. As a result, we need a quantitative method to track which ad brings more value as the advertising campaign is happening. This is clearly a Multi-Armed-Bandit Problem.

### Project goals
This notebook will be comparing 5 strategies to adress the advertising use case.

Each of the section has a goal :
- Section 1 : Comparing Regret Upper Bounds
- Section 2 : Coding a very famous Multi-Armed-Bandit Algorithm
- Section 3 : Playing around with UCB's hyperparameters to find interesting situations
- Section 4 : Outperforming the UCB with another algorithm : Thompson Sampling
- Section 5 : Testing EXP3

All of the 5 MAB Algorithms get the same kind of inputs and return the same kind of outputs

Inputs :
- Simulated Bernoulli rewards dataset
- Hyperparameter of the algorithm

Outputs :
- The rewards for each arm (list of lists)
- The list of selected arms for each round

### Data description
For the sake of simplicity, we will working with simulated data. The dataset has  N  rows which will be the rounds given to our different solutions to guess which ad is the best. It will have  K  columns where each column represents an arm (or ad).

Each observation of the dataset represents the vector of rewards, each component representing the reward that would be observed when playing the corresponding arm.

The reward here represents whether a person has clicked or not on the ad as it was presented to him : it's a Bernoulli experience

The average reward of each arm in this context is called the Click-Through-Rate (CTR), it's probably the most famous KPI in the advertising industry.

The generate_bernoulli_simulation function generates the dateset by giving it as an input the number of rounds and the click-through rates. You can force specific values of click-through-rates if you want, or use the generate_bernouilli_variables function to generate it for you.
