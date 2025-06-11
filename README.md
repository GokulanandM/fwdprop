📚 Documentation:[[View here](https://heartfelt-starship-a1c3e5.netlify.app/)]

# fwdprop

[![CI](https://github.com/GokulanandM/fwdprop/actions/workflows/ci.yml/badge.svg)](https://github.com/GokulanandM/fwdprop/actions)
[![PyPI](https://img.shields.io/pypi/v/fwdprop)](https://pypi.org/project/fwdprop/)

# fwdprop

Title: In-Depth Technical Breakdown of the Python Package (v0.1.0 – v0.1.7)
________________________________________
Overview
The fwdprop package is a lightweight Python module designed to simulate forward propagation in neural networks. Created for educational, prototyping, and exploratory use, it allows users to build and run both single-layer and multi-layer neural networks using basic Python and NumPy, with minimal overhead.
This document explores:
•	The purpose and scope of fwdprop
•	Its architecture and core components
•	Feature evolution from v0.1.0 to v0.1.7
•	Comparison with existing frameworks (e.g., TensorFlow, PyTorch)
•	Design choices and their technical implications
________________________________________
Purpose & Intent
While large frameworks like TensorFlow and PyTorch are designed for scalable, production-grade deep learning, they often obscure foundational logic beneath abstraction layers. The purpose of fwdprop is to:
•	Make forward propagation logic transparent and hackable
•	Be ideal for learners, educators, and tinkerers
•	Serve as a customizable foundation for building custom networks without heavyweight dependencies
________________________________________
Core Architecture
1. Layer Class
•	Encapsulates weight matrix, bias vector, and activation function
•	Handles computation: output = activation(weights * inputs + bias)
•	Modularized so multiple layers can be chained
2. NeuralNetwork Class
•	Stores a sequence of Layer instances
•	Supports:
o	Single-layer use: simple networks
o	Multi-layer configs via layers_config
•	Exposes .forward(inputs) for end-to-end propagation
3. Activation Functions
•	Implemented separately in activations.py
•	Supported:
o	Sigmoid
o	ReLU
o	Identity (linear)
•	Easily extendable
________________________________________
Version-by-Version Deep Dive
▶ v0.1.0: The Genesis
•	Flat function-based logic
•	No classes, no object state
•	Could handle only a single neuron
•	Hard-coded activations (if any)
•	Drawback: Not scalable, no reusability
▶ v0.1.2: Enter ForwardPropagator
•	Introduced a class for stateful propagation
•	Allowed bias/weight customization and activation control
•	Still single-layered
•	Deprecated later: Not compatible with multi-layer evolution
▶ v0.1.4: True OOP with NeuralNetwork
•	Added layer stacking via layers_config
•	Abstracted layers as objects
•	Clean forward pass pipeline
•	Supported Activations: sigmoid, relu, identity
•	Design Impact: Clear separation of logic, extensible and testable
▶ v0.1.6: Simplification
•	Removed legacy ForwardPropagator
•	Lean interface: One class, one purpose
•	Better validation for incorrect configs
•	Solidified modular pattern
▶ v0.1.7: User-Facing & Interactive
•	Focused on making the package demo- and input-friendly
•	Compatible with notebooks and CLI-based user input
•	Ready for visualization or educational environments
________________________________________
Comparison to Existing Solutions
Feature	fwdprop	PyTorch / TensorFlow
Use Case	Learning, Demos	Research, Production
Installation Size	Tiny (<10KB)	Hundreds of MB
Layers/Abstraction	Manual, Custom	Automatic, High-level APIs
Backpropagation	❌ Not supported	✅ Yes
Training Loop	Manual/None	Built-in
Optimizers	Not included	SGD, Adam, etc.
Visualizations	DIY	TensorBoard, etc.
Key Difference: fwdprop is explicit and minimal. You see every dot product, every activation, and every shape. It prioritizes understanding over performance.
________________________________________
Why This Design Works
•	Clarity over Abstraction: Learners can trace exactly what happens at each layer
•	Low barrier to entry: Requires only Python + NumPy
•	Customizability: Easy to build unconventional layer structures
•	Controlled complexity: You decide how many layers, neurons, and what functions to use
________________________________________
Example Use (v0.1.7)
from fwdprop import NeuralNetwork

model = NeuralNetwork(
    weights=[[0.2, 0.4, 0.6], [0.1, 0.3, 0.6]],
    bias=[0.5, 0.6],
    activation='sigmoid'
)

output = model.forward([1, 2, 3])
print("Output:", output)
Multi-layer Setup
model = NeuralNetwork(layers_config=[
    {
        "weights": [[0.2, 0.4, 0.6], [0.5, 0.3, 0.7], [0.8, 0.2, 0.9], [0.1, 0.5, 0.3]],
        "bias": [0.1, 0.2, 0.3, 0.4],
        "activation": "relu"
    },
    {
        "weights": [[0.4, 0.6, 0.5, 0.7]],
        "bias": [0.3],
        "activation": "sigmoid"
    }
])

output = model.forward([1, 2, 3])
print("Output:", output)
________________________________________
Final Thoughts
fwdprop is not meant to replace PyTorch, but to teach why PyTorch works. It builds intuition. Each layer, activation, and input flows exactly as you’d write on paper. Ideal for classroom use, presentations, or even as a base for custom AI experiments.
In a world of black-box ML, fwdprop is a glass box.
________________________________________
Next Steps for the Package
•	Add support for training (backpropagation)
•	Visualization tools
•	Serialization (saving/loading networks)
•	CLI mode or Web UI for interactive demos
________________________________________
Author: [Gokulanand]
Package: fwdprop
Latest Version: 0.1.7


## Installation


pip install fwdprop
