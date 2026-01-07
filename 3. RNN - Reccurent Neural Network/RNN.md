# Recurrent Neural Networks (RNN)

https://www.analyticsvidhya.com/blog/2019/01/fundamentals-deep-learning-recurrent-neural-networks-scratch-python/

## What is RNN?

A **Recurrent Neural Network (RNN)** is a deep learning model that is trained to process and convert a **sequential data input** into a **sequential data output**.

Sequential data is data—such as **words, sentences, or time-series data**—where sequential components interrelate based on complex semantics and syntax rules.

An RNN is a software system that consists of many interconnected components mimicking how humans perform sequential data conversions, such as translating text from one language to another.

> ⚠️ Note: RNNs are largely being replaced by **transformer-based AI models** and **Large Language Models (LLMs)**, which are significantly more efficient at handling long-range dependencies and large-scale sequential data.

---

## How does a recurrent neural network work?

RNNs are made up of **neurons**, which are data-processing nodes that work together to perform complex tasks. These neurons are organized into:

- **Input layer** – receives the input data  
- **Hidden layer** – processes data and retains memory  
- **Output layer** – produces the final result  

The key feature of an RNN is its **recurrent (self-looping) connection**, which allows the hidden layer to store information from previous time steps.

### Hidden layer

The hidden layer acts as a **short-term memory**. It processes data one step at a time while retaining relevant information from previous inputs.

#### Example

Input sequence:  

Expected prediction:  

- When the model processes **Apple**, it stores this information in memory.
- When it processes **is**, it recalls **Apple** to understand context.
- This allows the RNN to correctly predict **red**.

Because of this memory mechanism, RNNs are effective for:
- Speech recognition
- Machine translation
- Language modeling

---

## How are recurrent neural networks trained?

Machine learning engineers train RNNs by feeding them labeled training data and iteratively refining their performance.

### Weight sharing

- All hidden layers in an RNN share the **same weights**
- This allows the model to generalize patterns across time steps

### Backpropagation Through Time (BPTT)

RNNs are trained using **Backpropagation Through Time (BPTT)**, which works by:

1. Unrolling the network across time steps  
2. Calculating prediction error  
3. Propagating the error backward through previous time steps  
4. Adjusting weights to minimize loss  

BPTT identifies which time step caused the error and updates the model accordingly.

---

## What are the types of recurrent neural networks?

RNNs can be structured in different ways depending on the input-output relationship.

### One-to-Many

- **Single input → multiple outputs**
- Used in tasks like **image captioning**

**Example:**  
Image → Sentence

---

### Many-to-Many

- **Multiple inputs → multiple outputs**
- Used in **machine translation**

**Example:**  
English sentence → Translated sentence

---

### Many-to-One

- **Multiple inputs → single output**
- Used in **sentiment analysis**

**Example:**  
Customer review → Positive / Negative / Neutral

---

## How do recurrent neural networks compare to other deep learning networks?

### Recurrent neural network vs. Feed-forward neural network

| Feature | Feed-forward NN | RNN |
|------|----------------|----|
| Memory | ❌ No | ✅ Yes |
| Sequential data | ❌ Poor | ✅ Strong |
| Context awareness | ❌ No | ✅ Yes |

Feed-forward networks process inputs independently and forget previous inputs, whereas RNNs maintain memory using hidden states.

---

### Recurrent neural network vs. Convolutional neural networks

| Feature | CNN | RNN |
|------|-----|----|
| Data type | Spatial (images, videos) | Sequential (text, time-series) |
| Core strength | Feature extraction | Long-term dependencies |
| Typical use | Computer vision | NLP & speech |

---

## What are some variants of recurrent neural network architecture?

### Bidirectional Recurrent Neural Networks (BRNN)

BRNNs process sequences in **both forward and backward directions**.

- Forward layer: uses past context
- Backward layer: uses future context

This dual context improves prediction accuracy.

**Example:**  
Sentence: *Apple trees are tall*  
BRNN helps predict **trees** by considering both past and future words.

---

### Long Short-Term Memory (LSTM)

LSTM is an RNN variant designed to remember information over **longer time periods**.

#### Why LSTM?

Standard RNNs struggle with long-term memory.

**Example:**
Tom is a cat.
Tom’s favorite food is fish.


- RNN forgets that *Tom is a cat*
- LSTM remembers it using special **memory cells**

#### LSTM Components

- Input gate
- Forget gate
- Output gate

These gates control what information to store, update, or discard.

---

### Gated Recurrent Units (GRU)

GRUs are a simplified version of LSTMs.

- Uses **update gate**
- Uses **forget gate**
- Faster and computationally efficient

GRUs selectively retain or discard information while maintaining performance.

---

## What are the limitations of recurrent neural networks?

### Exploding gradient problem

- Gradients grow exponentially during training
- Leads to unstable learning and overfitting
- Causes erratic model behavior

---

### Vanishing gradient problem

- Gradients approach zero
- Model fails to learn long-term dependencies
- Results in underfitting

---

### Slow training time

- RNNs process data **sequentially**
- Cannot fully leverage parallel computing
- Becomes inefficient for long sequences

---

## How do transformers overcome the limitations of recurrent neural networks?

Transformers are deep learning models based on **self-attention** and **parallel processing**.

### Self-attention

- Captures relationships between all tokens at once
- No hidden states required
- Handles long-range dependencies efficiently

---

### Parallelism

- All inputs processed simultaneously
- No time-step dependency
- Faster training on GPUs
- Better gradient flow

This makes transformers highly scalable and ideal for modern NLP tasks.
