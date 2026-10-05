
# Wordle Intelligent Agent: Information Gain & Strategy Comparison

This project investigates different strategies for solving Wordle and evaluates how effectively each strategy can identify the hidden word within the six-guess limit.

The project originally began as an attempt to build a **Reinforcement Learning (RL) agent** for Wordle. After experimenting with RL-based approaches, I found that they were not the most efficient approach for this particular problem. The project therefore shifted toward **information-gain-based strategies**, which can make more informed guesses by selecting words that are expected to reduce the remaining uncertainty.

The repository includes multiple agents and an evaluation framework for comparing their performance.

## How Wordle Works

Wordle is a sequential decision-making problem where the agent must identify a hidden five-letter word in at most six attempts.

After each guess, the environment returns feedback for each letter:

* `0` = gray — the letter is not in the target word
* `1` = yellow — the letter is in the target word but in the wrong position
* `2` = green — the letter is in the correct position

The agent uses this feedback to update its knowledge of the possible target words and select its next guess.

## Strategies

The project explores several approaches:

### Random Agent

Selects a valid word without using an information-based strategy. This provides a baseline for comparison.

### Entropy / Information Gain Agent

Selects guesses based on their expected information gain. The goal is to choose a word that is likely to produce feedback that eliminates a large portion of the remaining candidate words.

### Reinforcement Learning Agents

The project also includes RL-based implementations, including REINFORCE and DQN approaches.

These were explored as potential solutions to the sequential decision-making problem, but experimental results showed that RL was not the most efficient approach for this particular task compared with information-gain-based methods.

This comparison was an important part of the project: rather than assuming that a more complex learning-based approach would perform better, I evaluated different strategies and compared their results.

## Evaluation

Agents are evaluated using multiple metrics, including:

* **Win rate** — percentage of games solved within six guesses
* **Average guesses** — average number of guesses required to solve a game
* **Consistency** — variation in performance across games
* **Runtime** — computational cost of selecting guesses

The evaluation framework allows different agents to be tested under the same conditions and compared quantitatively.

## Repository Structure

```text
wordle-project/
│
├── wordle_env.py
├── valid-wordle-words.txt
│
├── agents/
│   ├── random_agent.py
│   ├── entropy_agent.py
│   ├── reinforce_agent.py
│   └── dqn_agent.py
│
├── evaluation/
│   ├── evaluate.py
│   └── metrics.py
│
├── utils/
│   ├── feedback.py
│   └── entropy.py
│
├── play.py
├── train_rl.py
└── README.md
```

## Key Takeaway

The main goal of the project was not simply to build the most complicated agent possible, but to **experiment with different approaches and determine which strategies were most effective for Wordle**.

The results demonstrated that information-gain-based strategies provided a more efficient approach than the RL methods explored in this project, highlighting the importance of choosing an appropriate method for the structure of the problem rather than relying on model complexity alone.
