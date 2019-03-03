## Word Vector Representations: word2vec

### WordNet
- Synonyms miss nuances
- missing new words (e.g. deep learning ninja)
- subjective
- requires human labor to create and adapt

This is a general problem with **discrete representation**! This is equivalent to very sparce vectors due to atomic representation (one-hot representation).

We need similarity relations between words. We can build that

OR

Use a representation where vectors encode the similarity between words.

### Word2Vec ([video](https://www.youtube.com/watch?v=64qSgA66P-8))
Example sentence: "hello, whats up?"

- **Encoding**: Convert text to number. {hello:0, whats:1, up:2}
- **One Hot Encoding**: Every word is a vocabulary_size vector. {hello:[1,0,0], whats: [0,1,0], up:[0,0,1]}

One Hot encoding doesn't have similarity. Cosine similarity also 0 since angle is 90 degree in n-dimensional space.

- **Embedding**: Dense vector with similarity.

king [1,2]
man [1,3]
woman [5,3]
queen [5,1]

- **Word2Vec**: is a embedding and similarity comes from neighboring words.

- Skipgram: window size 1
"king brave man" 

training data: word: king [x], neighbor: brave [target]

one_hot_encoding for training data and labels (neighbours): Cross entropy.


Input layer - hidden layer - output(softmax) --- crossentropy ----- target.

Extract Hidden layer to make it like a lookup table.


