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
![BG_REMOVE](https://github.com/Rupeshwaran-Ravindrran/RYUforcement_Learning/assets/79376089/c587d1f8-e87c-439f-875d-150ef93a0643)<br />
- **Time Limit:** 99-second match or continue until there's a knockout.
- **Throws and Holds:** Characters can perform throws or holds by pressing towards the opponent and a medium/strong punch/kick button.
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
The observation space is defined as a grayscale image with dimensions (149, 256, 1) and data type `np.uint8`, representing pixel values ranging from 0 to 255.

#### 2.2. Action Space
The action space is defined as `MultiBinary(12)`, indicating a binary vector of length 12 representing possible actions for the agent.

#### 2.3. Preprocessing Images
The preprocessing step involves converting the game screen into a format suitable for the neural network to process efficiently. The code below resizes, grayscales, and reshapes the image.

1. Cropping: The region of interest is extracted from the original image (from row 41 to row 190).
2. Grayscaling: The color image is converted to grayscale.
3. Resizing: The image is resized to (256, 149) using nearest-neighbor interpolation.
4. Reshaping: The image is reshaped to have one channel, resulting in dimensions (149, 256, 1).
   
Original vs. Preprocessed Image
Below are the examples of the original and preprocessed images:

Original Image (200x256)

![original_png](https://github.com/Rupeshwaran-Ravindrran/RYUforcement/assets/79376089/231cee5d-f8f5-4f29-9d56-7e59925e5e82)

Preprocessed Image (149x256)

![preprocessed_png](https://github.com/Rupeshwaran-Ravindrran/RYUforcement/assets/79376089/820bcc14-e1d7-4f45-976d-8d3bf8737c31)


The preprocessed image is greyscaled with the concatenated game ui elements. This ensures the neural network processes a standardized input, improving training efficiency and performance.

#### 2.4. Defining a Custom Reward Function
Implement a custom `step(self, action)` function to calculate the agent's health delta (`agent_health_delta`) and enemy's health delta (`enemy_health_delta`). Penalize the agent for damage received and provide incentives for dealing damage, with bonus points for dealing damage without receiving damage.

In the context of reinforcement learning, a reward function is a crucial component that defines the objective or goal that the agent aims to achieve. The reward function assigns a numerical value (reward) to each state and action taken by the agent, guiding its learning process towards desirable outcomes. The provided code snippet appears to be defining a custom reward function for a game environment, where the agent's goal is to maximize its score while inflicting damage on the enemy and minimizing its own health loss.

The custom reward function in this code calculates the reward based on several factors:

1. **Score Difference**: The reward includes the difference between the current score and the previous score, encouraging the agent to increase its score.

2. **Enemy Damage**: The agent receives a positive reward proportional to the amount of damage inflicted on the enemy. The reward is calculated based on the change in the enemy's health, with a higher reward for greater damage.

3. **Agent's Health Loss**: The agent receives a negative reward (penalty) proportional to the amount of health it has lost. This penalty discourages the agent from taking actions that result in significant health loss.

4. **Damage Multipliers**: The code includes additional multipliers or bonuses for specific situations:
  - If the agent inflicts damage on the enemy without losing any health, the damage reward is doubled.
  - If the agent loses a small amount of health (less than 5), it receives a fixed reward of 500, potentially encouraging more aggressive behavior.

The custom reward function combines these components to create an overall reward signal that guides the agent's learning process. By adjusting the weights or coefficients associated with each component, the reward function can be tuned to prioritize different objectives or behaviors.



## Contributions

Contributions to this project are welcome! Whether you're interested in adding new features, optimizing algorithms, or improving documentation, we appreciate any contributions that help advance the capabilities of our RL agents in Street Fighter.

## License

This project is licensed under the [MIT License](LICENSE), allowing for open collaboration and usage.
