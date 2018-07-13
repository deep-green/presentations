class: center, middle
# Künstliche Intelligenz 1

---

## Technologie
### Künstliche Intelligenz 1

__Programmiersprache(n):__
- Python

__Framework(s) & Bibliothek(en):__
- Tensorflow
- python-chess
- socket.io

__Methode(n) und Algorithmen:__
- Supervised Learning 
- Neuronale Netze

---

## Klassisches neurales Netz
### Künstliche Intelligenz 1

<img src="images/neuro1.png" width="95%" />

---

## Code-Snippets
### Künstliche Intelligenz 1

```python
# Network Parameters
n_hidden_1 = 500 # 1st layer number of neurons
n_hidden_2 = 500 # 2nd layer number of neurons
n_hidden_3 = 500 # 3rd layer number of neurons
num_input = 64 # Chess-Tiles
num_classes = 4032 # Moves in Chess

# tf Graph input
X = tf.placeholder("float", [None, num_input])
Y = tf.placeholder("float", [None, num_classes])

# Store layers weight & bias
weights = {
    'h1': tf.Variable(tf.random_normal([num_input, n_hidden_1])),
    'h2': tf.Variable(tf.random_normal([n_hidden_1, n_hidden_2])),
    'h3': tf.Variable(tf.random_normal([n_hidden_2, n_hidden_3])),
    'out': tf.Variable(tf.random_normal([n_hidden_3, num_classes]))
}
biases = {
    'b1': tf.Variable(tf.random_normal([n_hidden_1])),
    'b2': tf.Variable(tf.random_normal([n_hidden_2])),
    'b3': tf.Variable(tf.random_normal([n_hidden_3])),
    'out': tf.Variable(tf.random_normal([num_classes]))
}

```

---

## Code-Snippets
### Künstliche Intelligenz 1

```python
# Create model
def neural_net(x):
    # Hidden fully connected layer with 500 neurons
    layer_1 = tf.add(tf.matmul(x, weights['h1']), biases['b1'])
    tf.nn.relu(layer_1)
    # Hidden fully connected layer with 500 neurons
    layer_2 = tf.add(tf.matmul(layer_1, weights['h2']), biases['b2'])
    tf.nn.relu(layer_2)
    # Hidden fully connected layer with 500 neurons
    layer_3 = tf.add(tf.matmul(layer_2, weights['h3']), biases['b3'])
    tf.nn.relu(layer_3)
    # Output fully connected layer with a neuron for each class
    out_layer = tf.matmul(layer_3, weights['out']) + biases['out']
    tf.nn.relu(out_layer)
    return out_layer

```

---

## Code-Snippets
### Künstliche Intelligenz 1

```python
def train_neural_network(x):
    #Number of simultaneously read games
    batch_size = 512
    pgn = readpgn()
    ses = tf.Session()
    inputlist = pgn.getInput()
    outputlist = pgn.getOutput()
    prediction = neural_net(x)
    #Calculated costfunction
    cost = tf.reduce_mean( tf.nn.softmax_cross_entropy_with_logits(logits=prediction, labels=Y) )
    #Init Optimizer
    optimizer = tf.train.AdamOptimizer().minimize(cost)
    #Number of repeats
    hm_epochs = 100
    ses.run(tf.global_variables_initializer())
    for epoch in range(hm_epochs):
        epoch_loss = 0
        for _ in range(int(len(inlist)/batch_size)):
             epoch_x = inputlist[(_*batch_size):(batch_size*_+batch_size)]
             epoch_y = outputlist[(_*batch_size):(batch_size*_+batch_size)]
             _, c = ses.run([optimizer, cost], feed_dict={X: epoch_x, Y: epoch_y})
             epoch_loss += c
        print('Epoch', epoch, 'completed out of',hm_epochs,'loss:',epoch_loss)
        correct = tf.equal(tf.argmax(prediction, 1), tf.argmax(Y, 1))
        accuracy = tf.reduce_mean(tf.cast(correct, 'float'))

```

---

## Code-Snippets
### Künstliche Intelligenz 1

```python
@sio.on('receive')
def message(sid, data):
    print("receive", data)
    ret = Controller.init(data)
    sio.emit('makeMove', ret, room=sid)

```
