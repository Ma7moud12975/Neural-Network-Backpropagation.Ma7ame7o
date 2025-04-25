
![image imageformat 1286 1106067734](https://github.com/user-attachments/assets/ca87858c-b828-4fab-9370-f6fbab85ff9a)
# Simple Neural Network Backpropagation Example

This repository contains a basic Python script demonstrating the fundamental concepts of a feedforward neural network, including the forward pass, error calculation (Mean Squared Error), and the backpropagation algorithm for updating weights based on a single training example.

## Purpose

The primary goal of this code is to provide a clear, step-by-step illustration of how backpropagation works in a simple neural network setting. It's designed for educational purposes to help understand the underlying mathematics and implementation details without the complexity of larger libraries.

## Network Architecture

The script implements a simple neural network with the following structure:

*   **Input Layer:** 2 neurons
*   **Hidden Layer:** 2 neurons (using sigmoid activation)
*   **Output Layer:** 2 neurons (using sigmoid activation)
*   **Biases:** A bias term is added to the net input calculation for each neuron in the hidden and output layers.

The specific architecture and initial values are:
*   Inputs: `[0.05, 0.1]`
*   Targets: `[0.01, 0.99]`
*   Weights (Initial): `w1` to `w8` are initialized with specific values.
*   Biases (Initial): `b1` (for hidden layer), `b2` (for output layer).
*   Learning Rate (`eta`): `0.5`

## Key Concepts Demonstrated

*   **Feedforward Propagation:** Calculating the network's output based on the inputs, weights, and biases.
*   **Sigmoid Activation Function:** Used to introduce non-linearity.
*   **Mean Squared Error (MSE) Loss Function:** Calculating the difference between the predicted output and the target output.
*   **Backpropagation Algorithm:** Calculating the gradient of the loss function with respect to each weight in the network using the chain rule.
*   **Gradient Descent:** Updating the weights in the direction that minimizes the error, scaled by the learning rate.

## How it Works (Single Iteration)

1.  **Initialization:** Network parameters (weights `w1`-`w8`, biases `b1`, `b2`), inputs, targets, and the learning rate (`eta`) are defined.
2.  **Forward Pass:**
    *   The net input to each hidden neuron (`net_h1`, `net_h2`) is calculated (weighted sum of inputs + bias).
    *   The output of each hidden neuron (`out_h1`, `out_h2`) is calculated by applying the sigmoid function.
    *   The net input to each output neuron (`net_o1`, `net_o2`) is calculated (weighted sum of hidden outputs + bias).
    *   The final output of the network (`out_o1`, `out_o2`) is calculated by applying the sigmoid function.
3.  **Error Calculation:** The total error (`E_total`) is calculated using the Mean Squared Error formula between the network's outputs (`out_o1`, `out_o2`) and the target values.
4.  **Backpropagation:**
    *   The partial derivative of the total error with respect to each output neuron's output (`dE_total_out_o1`, `dE_total_out_o2`) is calculated.
    *   Using the chain rule, the derivative is propagated back to the net input of the output neurons (`dE_total_net_o1`, `dE_total_net_o2`). This involves multiplying by the derivative of the sigmoid function.
    *   The error is further propagated back to the hidden layer's outputs (`dE_total_out_h1`, `dE_total_out_h2`) by considering the weights connecting the hidden and output layers (`w5` through `w8`).
    *   Finally, the derivative is propagated to the net input of the hidden neurons (`dE_total_net_h1`, `dE_total_net_h2`), again using the chain rule and the sigmoid derivative.
5.  **Weight Update:**
    *   Each weight (`w1` through `w8`) is updated using the gradient descent rule: `weight = weight - learning_rate * gradient`. The specific gradient used depends on which connection the weight represents (e.g., `dE_total_net_h1` for weights connected *to* hidden neuron 1, multiplied by the corresponding input or hidden output).
    *   *(Note: This script updates the weights `w1`-`w8` but does not include the update steps for the biases `b1` and `b2` in the backpropagation phase).*
6.  **Output:** The script prints the updated values of the weights after this single iteration.

## How to Run

1.  Ensure you have Python installed.
2.  Install the NumPy library if you haven't already:
    ```bash
    pip install numpy
    ```
3.  Save the code as a Python file (e.g., `nn_backprop.py`).
4.  Run the script from your terminal:
    ```bash
    python nn_backprop.py
    ```
    The output will show the updated weights after one training step.

## Dependencies

*   Python 3.x
*   NumPy

## Future Improvements / Next Steps

*   Implement training over multiple epochs (iterations) using a loop.
*   Encapsulate the network logic within a class structure.
*   Implement bias updates during backpropagation.
*   Use matrix operations for more efficient calculations, especially for larger networks.
*   Handle multiple training examples (batch or mini-batch gradient descent).
*   Add options for different activation functions (e.g., ReLU, Tanh).
*   Implement more sophisticated optimization algorithms (e.g., Adam, RMSprop).
![Untitled-3](https://github.com/user-attachments/assets/1a3e4ad3-c12b-4cd3-b0af-fd417795abd7)
