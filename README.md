# Reinforcement Learning in Street Fighter

### Objective:

This project aims to develop a reinforcement learning agent using Proximal Policy Optimization (PPO) and Convolutional Neural Networks (CNN) to play Street Fighter II' - Special Champion Edition for the Genesis console. The agent is trained to compete in a tournament against a sequence of opponents, with a focus on training the character RYU to achieve optimal performance.

#### The key objectives of this project include
- Implementing PPO to train the agent through interactions with the game environment.
- Designing a CNN architecture to process game screen inputs and make action predictions.
- Fine-tuning hyperparameters using Optuna for improved training efficiency and performance.
- Evaluating the agent's performance against a variety of opponents in a tournament setting.


## Game Description
Street Fighter II' - Special Champion Edition is a classic 2D fighting game for the Genesis console. Players select one of 12 fighters to compete in a grand tournament to determine the best fighter. The game also offers multiplayer modes for added fun.

### Game Mechanics
- **Time Limit:** 99-second match or continue until there's a knockout.
- **Throws and Holds:** Characters can perform throws or holds by pressing towards the opponent and a medium/strong punch/kick button.
![BG_REMOVE](https://github.com/Rupeshwaran-Ravindrran/RYUforcement_Learning/assets/79376089/c587d1f8-e87c-439f-875d-150ef93a0643)

- **Controls:** Utilize the Genesis controller with a D-Pad (UP, DOWN, LEFT, RIGHT), buttons (A, B, C, X, Y, Z), and extra buttons (START, MODE).

## Agent Mechanics: RYU
**Special Moves:**
- **Fireball:** D, DR, R + any punch button.
- **Dragon Punch:** R, D, DR + any punch button.
- **Hurricane Kick:** D, DL, L + any kick button.
- **Air Hurricane Kick (Hyper mode):** D, DL, L + any kick button (while airborne).

#### Strategies for Success
- **Master Special Moves:** Learn and execute special moves effectively.
- **Counter-fighting:** Strategize to counter opponents' moves with suitable attacks.
- **Know Opponents' Moves:** Understand and exploit opponent patterns.
- **Combo Mastery:** Practice combos for increased damage and dizzying opponents.
- **Projectile Strategy:** Utilize projectiles defensively and offensively.


## **Setting Up the Environment**

1. Clone the repository to your local machine.
2. Create a virtual environment with python3.8
3. Install the required dependencies using `pip install -r requirements.txt`.
4. Download the Street Fighter II' - Special Champion Edition (USA) ROM from the repository into the virtual environment.

## Setting Up Custom gym-retro Environment for Training

### 1. Setting Up Custom gym-retro Environment

Install and set up a custom gym-retro environment for training your reinforcement learning agent.

### 2. Creating a Custom Environment `StreetFighter()`

#### 2.1. Observation Space
The observation space is defined as a grayscale image with dimensions (84, 84, 1) and data type `np.uint8`, representing pixel values ranging from 0 to 255.

#### 2.2. Action Space
The action space is defined as `MultiBinary(12)`, indicating a binary vector of length 12 representing possible actions for the agent.

#### 2.3. Preprocessing Images
Define a `preprocess()` function to grayscale the input image and resize it to (84, 84, 1) for efficient processing by the neural network.

#### 2.4. Defining a Custom Reward Function
Implement a custom `step(self, action)` function to calculate the agent's health delta (`agent_health_delta`) and enemy's health delta (`enemy_health_delta`). Penalize the agent for damage received and provide incentives for dealing damage, with bonus points for dealing damage without receiving damage.


## Contributions

Contributions to this project are welcome! Whether you're interested in adding new features, optimizing algorithms, or improving documentation, we appreciate any contributions that help advance the capabilities of our RL agents in Street Fighter.

## License

This project is licensed under the [MIT License](LICENSE), allowing for open collaboration and usage.
