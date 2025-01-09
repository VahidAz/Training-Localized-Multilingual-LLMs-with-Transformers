# Training Localized Multilingual LLMs with Transformers

This tutorial provides a sample code similar to the [NVIDIA NeMo tutorial](https://developer.nvidia.com/blog/training-localized-multilingual-llms-with-nvidia-nemo-part-1/) (links in references) for adding new language support to a base LLM using the Transformers library.

In this tutorial, **Tiny-LLama** is used as the base LLM, and **Japanese** is the selected new language. However, the code is designed to be extendable to other base LLMs and languages.

## Step 1: Tokenizer Training and Merging

The first step is to train and merge the tokenizer. We need to augment the base LLM tokenizer with the new language's tokens and rules. There are two options for this:

1. **Train a new tokenizer** for the new language.
2. **Use an existing tokenizer** from a pre-trained LLM that supports the new language.

- The sample code for **training a new tokenizer** can be found in [training_tokenizer.ipynb](training_tokenizer.ipynb).
- The sample code for **merging an already trained tokenizer** from the new language is available in [merging_two_trained_tokenizers.ipynb](merging_two_trained_tokenizers.ipynb).

## Step 2: Modifying the Base LLM Model

Once the tokenizer has been updated to support the new language, we need to modify the base LLM model's embedding and head layers. This modification is required because the vocabulary size has increased due to the additional tokens in the new language. Consequently, the model's layers must be adjusted to accommodate the larger vocabulary.
- The sample code for **model modification** can be found in [model_modification_new_tokenizer.ipynb](model_modification_new_tokenizer.ipynb).

## References

- [Training Localized Multilingual LLMs with NVIDIA NeMo – Part 1](https://developer.nvidia.com/blog/training-localized-multilingual-llms-with-nvidia-nemo-part-1/)
- [Training Localized Multilingual LLMs with NVIDIA NeMo – Part 2](https://developer.nvidia.com/blog/training-localized-multilingual-llms-with-nvidia-nemo-part-2/)
- [TinyLlama/TinyLlama-1.1B-Chat-v1.0](https://huggingface.co/TinyLlama/TinyLlama-1.1B-Chat-v1.0)
- [TinyLlama-1.1B](https://github.com/jzhang38/TinyLlama)
