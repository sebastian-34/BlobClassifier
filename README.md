# BlobClassifier

Single-page front-end only visualizer for training a small Multi-Layer Perceptron (MLP) to classify synthetic 2D datasets and display decision regions live while training.

## Features
- Datasets: Moons (2 classes), Diagonal (3 classes), Quadrant (4 classes)
- Configurable hidden layer sizes (e.g. `32,32` or `64,32,16`)
- Adjustable learning rate, epochs, points per class, variance, and moon gap
- Live status badge: Running / Stopped / Done
- Epoch counter and cross-entropy (log) loss display
- Real-time decision region heatmap with optional boundary lines overlay
- Full-batch gradient descent with ReLU hidden layers & softmax output layer
- Reset network or regenerate data instantly

## Quick Start
Open `index.html` directly in a modern browser (Chrome, Firefox, Edge). No build step or dependencies required.

## Controls
| Control | Description |
|---------|-------------|
| Hidden Layers | Comma-separated neuron counts for hidden layers |
| Learning Rate | Step size for gradient descent |
| Epochs | Maximum epochs to train (animation runs until reached or stopped) |
| Points / Class | Number of points generated per class |
| Variance | Standard deviation for Gaussian noise around each class center |
| Dataset | Select dataset type (adjusts number of classes automatically) |
| Moon Gap | Vertical separation between moon arcs (Moons dataset only) |
| Boundary Lines | Toggle crisp boundary line overlay between predicted regions |

### Buttons
- Generate Data: Recreate dataset with current parameters
- Start Training: Begin animated training
- Stop: Pause training (can resume)
- Reset NN: Reinitialize weights (clears epoch & loss counters)

## Implementation Notes
The MLP is implemented from scratch in JavaScript with:
- He-style initialization (`sqrt(2 / fan_in)`) for hidden layers
- ReLU activations for hidden layers
- Softmax + cross-entropy for output & loss
- Full-batch updates each epoch (no mini-batches) for simplicity

Decision regions are drawn by sampling a grid across normalized data space ([-1,1]²) and coloring by argmax class probability. Boundary lines are inferred by detecting class changes between adjacent grid cells.

## Extending
Ideas for future enhancements:
- Add mini-batch & momentum / Adam optimizer options
- Add additional datasets (spiral, concentric circles)
- Add probability heatmap per class via selectable overlay
- Export / import trained weights
- Performance optimizations using WebGL for region rendering

## License
Internal / demo usage. (Add a proper license if distributing.)
