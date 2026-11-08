# Catch the Apple

A browser game where you move a basket to catch falling apples
and compare your score against a trained neural network.

## Play

https://kstejas08.github.io/flappy-lab/

No installation is needed. The saved AI loads automatically.

## Controls

- Hold Left/Right arrow keys to move.
- Practice mode gives you three lives.
- Press R after game over to restart practice.
- Click "Switch to AI" to watch the network play.
- Click "Play 20 apples against AI" to compete.

## Fair challenge

The game creates 20 new apple positions and evaluates the current
network on them. You then play those same positions, starting from
the same basket position and using the same movement speed.
Both players get all 20 attempts. The final scores determine the winner.

## Neural network

The network has three inputs:
- Apple horizontal position
- Apple vertical position
- Basket centre position

Positions are normalized relative to the canvas dimensions.

There are six hidden neurons and three outputs:
left, stay, and right. Hidden and output neurons use tanh.
The largest output selects the action.

The live visualizer shows the actual network weights and activations.
Green indicates positive values; red indicates negative values.
Neuron opacity reflects activation magnitude, and connection width
reflects weight magnitude.

## Training

I trained the network using neuroevolution.

Each generation evaluates the current champion, 14 mutated copies,
and two new random networks on the same 20 training apples.
Each weight and bias in a mutated copy has a 20% chance of changing
by a random amount between -0.3 and 0.3.

Fitness awards 100 points per catch, plus a small bonus based on
how close the basket finishes to each apple.
The best-performing network is retained.

The saved generation-5 network caught 20/20 training apples.
A separate random 100-apple test reported 100 catches.
That is one test result, not a guarantee for every possible sequence.

The saved weights, biases, generation number, and training positions
are stored in trained-brain.json.

## Training tools

- "Test current AI" evaluates the current training sequence.
- "Train one generation" changes and selects networks.
- "Test 100 new apples" evaluates a fresh random sequence.
- "Load saved AI" imports a compatible saved network.

Additional training changes the network in memory.
Refreshing reloads the saved network from the repository.

## Built with

HTML, JavaScript, and the Canvas 2D API. No external ML library is used.

## AI assistance and references

I used ChatGPT for explanations, code examples,
implementation guidance, and debugging. I entered and tested the code
and made changes with that assistance.

The Coding Train's Neuroevolution Flappy Bird guide was an early
reference for the neuroevolution approach:
https://thecodingtrain.com/challenges/100-neuroevolution-flappy-bird

The project began as Flappy Lab and later became Catch the Apple,
so the repository and Hackatime project retain their original names.