# LLM Tokenizer

This project demonstrates the creation of a basic tokenizer for large language models (LLMs) using *Moby-Dick* by Herman Melville as a text corpus. The notebook provides two versions of a custom tokenizer class, `LLMBasicTokenizerV1` and `LLMBasicTokenizerV2`, each with encoding and decoding capabilities tailored to tokenizing words and punctuation.

## Table of Contents
- [Overview](#overview)
- [Installation](#installation)
- [Usage](#usage)
- [Tokenizer Versions](#tokenizer-versions)
  - [LLMBasicTokenizerV1](#llmbasictokenizerv1)
  - [LLMBasicTokenizerV2](#llmbasictokenizerv2)
  - [BytePairTokenizer](#bytepairtokenizer)
- [Example](#example)
- [Contributing](#contributing)
- [License](#license)

## Overview
Tokenization is a key component of text processing in natural language processing (NLP) and LLMs. This project showcases how to build a tokenizer from scratch, using regular expressions to split text into words and punctuation tokens. The tokenizer is tested on an example text to demonstrate encoding (text-to-ID conversion) and decoding (ID-to-text reconstruction). Also, this project shows how the Byte-Pair Encoding can be used.

## Installation
Install the required libraries:
```bash
!pip install datasets
!pip install tiktoken
!pip install gutenbergpy
```

## Usage
Run the notebook to:

1. **Download the text corpus** of *Moby-Dick* from Project Gutenberg.
2. **Process the corpus** using either the basic or advanced tokenizer.
3. **Test tokenization** by encoding and decoding example text.

### Notebook Sections
- **Library Imports**: Loads essential libraries for dataset management, tokenization, and HTTP requests.
- **Corpus Download**: Fetches the full text of *Moby-Dick* from Project Gutenberg.
- **Tokenizers**: Implements `LLMBasicTokenizerV1` and `LLMBasicTokenizerV2`.
- **Testing**: Encodes and decodes sample text to demonstrate tokenizer functionality.

## Tokenizer Versions

### LLMBasicTokenizerV1
A straightforward tokenizer that:
- Splits text by words and punctuation using regular expressions.
- Creates a vocabulary based on unique tokens in the corpus.
- Encodes text into token IDs and decodes token IDs back into text.

**Limitations**: Does not handle unknown words or special cases for end-of-text markers.

### LLMBasicTokenizerV2
An enhanced tokenizer that:
- Builds on `LLMBasicTokenizerV1`.
- Adds special tokens `<|endoftext|>` and `<|unk|>` to handle text boundaries and unknown tokens.
- Improves flexibility for inputs with out-of-vocabulary tokens.

### BytePairTokenizer
An enhanced tokenizer that:
- Builds on `LLMBasicTokenizerV1` and `LLMBasicTokenizerV2`.
- This is the tokenizer that is used by the GPT family models!

## Example

Here's how you can use the tokenizers to encode and decode text:

```python
tokenizer = LLMBasicTokenizerV2(corpus)

text = "Can you please, please give me your name so I can see who you actually are."
token_ids = tokenizer.encode(text)
decoded_text = tokenizer.decode(token_ids)

print("Encoded IDs:", token_ids)
print("Decoded Text:", decoded_text)
```

## Contributing
Feel free to fork the repository and submit pull requests if you have improvements or new features to add to the tokenizer.

## License
This project is licensed under the MIT License.


