# Entity-Recognition-Module

# Readme 

This is a Python script that matches and replaces entities from two different text based on their semantic similarity. It is a simple use case of natural language processing (NLP) and machine learning (ML), specifically TensorFlow and Spacy.

## Requirements

You'll need the following libraries:

- [Spacy](https://spacy.io)
- [TensorFlow](https://www.tensorflow.org)
- [TensorFlow Text](https://www.tensorflow.org/tutorials/tensorflow_text/intro)
- [Scikit-Learn](https://scikit-learn.org/stable/)
- [Scipy](https://www.scipy.org)
- [re](https://docs.python.org/3/library/re.html)-- a built-in Python library for regular expression. 

## Functionality

There are main three functions:

1. `replace_entities(original_text, replacement_text, user_replace=False)`: This function takes as input two text strings and an optional boolean flag. It replaces the named entities, defined terms, and cross references from the 'replacement_text' onto the 'original_text'. If 'user_replace' is set to true, it replaces them from 'original_text' onto the 'replacement_text.'
2. `extract_entities(text)`: This function extracts the named entities, defined terms, and cross references from the input text string. Named entities are recognized using the Spacy library, while defined terms and cross references are recognized by matching regular expression patterns.
3. `match_entities(original_entities, replacement_entities)`: This function takes as input two dictionaries of entities, and returns a list of pairs of entities. The pairing strategy is based on the cosine similarity between the Universal Sentence Encoder (USE) embeddings of the entities.

## Usage

To use the script, the TensorFlow model needs to be loaded first by running `similarity_model = tf.saved_model.load("https://tfhub.dev/google/universal-sentence-encoder/4")`, where `https://tfhub.dev/google/universal-sentence-encoder/4` is the path of the USE pretrained model.

After that you can call the `replace_entities(original_text, replacement_text, user_replace=False)` function with your text strings to get the replaced results. Here, `original_text` is the text from which entities are replaced, `replacement_text` is the text onto which entities are replaced, and `user_replace` is an optional boolean flag to control the direction of replacements.

## Note

This code depends heavily on the quality and specifics of the trained Universal Sentence Encoder (USE) model for the accuracy of entity matching. The regular expressions for identifying defined terms and cross references are also quite specific, and might need modification according to the content of the input text. The code also assumes that every named entity, defined term, and cross reference in the replacement text can be paired with a counterpart in the original text, but does not ensure that each entity in the original text has a counterpart in the replacement text. Hence, this code might not be suitable for all use cases.
