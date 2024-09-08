 - ml -> deep learning
	- also data transformation and reduction: e.g. inputs are imgs -> output is shrunk to a single bit: spam or not spam, or limited number of bits (when training a model to recognize e.g. 1,000 imgs)
- ai
	- turing test: ability to create
	- what we do with DL
	- forward propagation: triangle - layers with multiple neurons on the left gradually reduced to a e.g. single neuron (we can also end up with a 1,000 or more at the end of the triangle, if the model is trained to recognize 1000 entities)
	- we can go further, and recreate sth on the other end, e.g. to redraw an img (e.g. stylized img 0)
	  ![[ml-dl.png]]
	  ![[create-stylized-img.png]]

- transforming/reducing data by figuring out weights/biases and connections btw neurons

- Combining Neural Networks & AI
	- CNN & RNN https://stanford.edu/~shervine/teaching/cs-230/cheatsheet-convolutional-neural-networks
	- combining the two into a system using an "aggregator" to get a complex model that can analyze a question about an img, for instance
	- training of such systems is similar to regular training: provide a lot of questions (for RNN - text/sound), corresponding imgs (for CNN) and corresponding answer/output; thru back propagation, we retrain CNN, RNN and the aggregator to figure out the answer/output