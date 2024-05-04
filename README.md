Tetris AI Overview:

Functionality:
This Tetris-playing bot employs deep reinforcement learning. Initially, it makes random moves, storing states and rewards in a limited queue (replay memory). After each game, it trains itself using a random sample from the replay memory. Over time, through more games, it improves its performance and achieves higher scores.

Reinforcement Learning:
The agent's learning process involves exploration and exploitation. It starts with random moves but gradually shifts towards more strategic actions. It uses Q Learning to determine the best possible score, considering future rewards rather than just immediate gains. An exploration variable ensures occasional random actions to discover new strategies for higher scores.

Training:
Based on the Q Learning algorithm, the training considers transitions between states and future rewards. The neural network updates based on this data, incorporating reward and predicted future rewards to refine its strategy.

Best Action Selection:
Instead of directly selecting the action with the highest value, this AI explores all possible moves for a Tetris round. Each move's resulting state is evaluated using the neural network, and the action leading to the highest predicted score is chosen.

Game State Representation:
The AI considers various attributes to train the network, such as the number of lines cleared, number of holes, and the layout of the board. After experimentation, it was found that only a subset of these attributes significantly impacts training, such as line count, hole count, bumpiness, and total height.

Implementation:
The entire system is coded in Python, utilizing the Keras framework with TensorFlow backend for the neural network. Other requirements include TensorFlow/Jax/PyTorch, Tensorboard, OpenCV, NumPy, Pillow, and Tqdm.

Internal Structure:
The AI consists of a deep neural network, with customizable parameters such as layer size, activation functions, loss function, and optimizer. By default, it uses a neural network with two hidden layers, ReLU activation for inner layers, and linear activation for the last layer.

Training Details:
During training, a replay queue of size 20,000 is used, with 512 samples selected randomly for training in each episode. The training process employs one epoch per episode.

Results and Evaluation:
The AI's performance is evaluated through episodes, with a decreasing exploration factor. Results are visualized using Tensorboard. Adjusting hyperparameters, such as the end of the exploration phase, can influence the speed and efficiency of training.
