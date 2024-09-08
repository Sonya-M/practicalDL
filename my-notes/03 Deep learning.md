### layers
- can stack neurons into layers
- multiple neurons processing simultaneously in single layer![[dl-layers.png]]
-  fully connected neural networks (all neurons from prev layer connected to all neurons in next layer)![[fully-connected-nn.png]]

### weight & bias selection: training
- how are those weights and biases selected?
- no one is selecting them - result of training
- how is the model trained?
- need training data set (e.g. annotated imgs) - e.g. 1000 imgs with hotdog, 1000 imgs with anything but hotdog
-   in the first pass, all weights and biases are assigned randomly, usu. around 0, btw -1 and 1 in normal distribution 
- *forward propagation:* model takes the input (img of hotdog) and does the calculations with initially random weights and biases
- some neurons will be activated, and will propagate the signal forward, to the next layer, and so on for each layer, until we get to the last layer, the classifier, which can also be activated or not (hotdog or not hotdog) - in the first pass, everything is random
- then the randomness stops and we do *backward propagation* (back prop)
- if model's prediction was correct, we go back and strengthen all previously made correct decisions, reinforcing connections btw neurons by *slightly increasing weights*, going back layer by layer
- change in weights is always small, calculated using derivatives
- if the prediction was incorrect, we go back thru all activated channels and slightly decrease the weights
- reinforce correct predictions, penalize incorrect ones, repeat with multiple inputs (imgs)

### training models
- typical compute process: algoritm+input -> computer/cpu/gpu -> output:
  ![[algorithm-input-compute-output.png]]
- ML: input(imgs)/output(class/label/category/spam/not-spam) -> computer/cpu/gpu -> algorithm/model
![[input-output-compute-algorithm.png]]
(provided input data & corresponding labels, it will adapt weights and biases to get a model that returns correct result)
- with a trained model, data (weights+biases) is frozen, and the model can predict the label of an input it has never seen before


