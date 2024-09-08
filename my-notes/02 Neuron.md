- neurons & neural networks
- around mid 20th century, idea to reproduce human brain processes
- neurons are exposed to a lot of data, but they are able to figure out what's important and what isn't - they can be activated (and aplify/reduce signals), or they can just ignore signals
- chains of neurons connected to each other
- we are able to process all the data  we are exposed to, e.g. visual/audio signals etc.
- processing data: activation/deactivation in chains of neurons
- replicate that process in a machine/thru an algorithm

![[Neuron.png]]

- neuron: basic unit
- input to neuron: multiple channels of data (x1, x2, x3...) - in computer, that data is in the form of numbers (x1=3.2, x3=-4, x3=500...)
- neuron needs to aggregate all that data - amplify/reduce/ignore others:
	- assign weight to each channel: 
```
x1 * w1 
x2 * w2
...
// e.g.
x1 * 0  // ignore signal
x2 * 0.01 // reduce signal
x3 * 500 // amplify signal
```

- shrink all that data into a _single piece of information:_ adding it up: 
  `∑xi*wi+b` where b is a constant bias used to shift/normalize 
- is the neuron activated or not? output is  0 or 1
- activated neuron will pass signal down to next neuron in chain
- if neuron is not activated, the signal is ignored
- the result of `∑xi*wi+b` is anywhere btw `-∞...∞`
- to transform distributon of `-∞...∞` to `0..1`, we can use an activation func, e.g sigmoid

