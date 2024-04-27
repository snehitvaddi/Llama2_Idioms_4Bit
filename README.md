## Llama2_Idioms_4Bit - Idiom Suggestor Using LLaMA2

Fine-tuned LLaMA2 7B model on idioms datasets, employing quantization and parameter-efficient fine-tuning (PEFT) techniques to suggest contextually relevant idioms, enhancing communication naturalness and engagement. Explored 4-bit quantization and parameter-efficient fine-tuning (PEFT) to enhance the model's efficiency and performance.

## Overview
The Idiom Suggestor project involves three main stages:
1. **[LLM_Synth_Data_Gen_Langchain.ipynb](https://github.com/snehitvaddi/Llama2_Idioms_4Bit/blob/main/LLM_Synth_Data_Gen_Langchain.ipynb)**:
   - Extracting and preparing idiom data from a comprehensive English idiom dictionary.
   - Idioms are extracted from a PDF containing an English idiom dictionary using PyPDF2.
   - The text is split and processed into manageable chunks, which are then embedded and indexed using OpenAI's embeddings and FAISS for efficient retrieval during training.
3. **[Llama2_Data_Tamplating.ipynb](https://github.com/snehitvaddi/Llama2_Idioms_4Bit/blob/main/Llama2_Data_Tamplating.ipynb)**:
   - Formatting the data to align with LLaMA's training requirements.
   - `"<s>[INST] {context} [/INST] {response}</s>\"`
   - Data is transformed into LLaMA-compatible formats using pandas and sklearn, ensuring that idioms and their contexts are properly formatted.
   - This step is crucial for effective learning during the model training phase.
5. **[Fine_tune_Llama_2.ipynb](https://github.com/snehitvaddi/Llama2_Idioms_4Bit/blob/main/Fine_tune_Llama_2.ipynb)**:
   - Training the model using quantization and PEFT to effectively learn idiomatic expressions.
   - Fine-tuning is conducted on a pre-trained LLaMA model using advanced techniques such as LoRA and QLoRA for efficient training.
   - Specific attention is paid to managing GPU resources, especially in environments with limited hardware capabilities like Google Colab.
## Files
- [Idioms-Dictionary.pdf](https://github.com/snehitvaddi/Llama2_Idioms_4Bit/blob/main/Idioms-Dictonary.pdf) - Source dictonary file for idioms.
- [final_Idioms_test_Evaluation.xlsx](https://github.com/snehitvaddi/Llama2_Idioms_4Bit/blob/main/final_Idioms_test_Evaluation.xlsx) - LLM validation resulsts and Rogue scored
  
## Installation

Before you start, ensure you have Python 3.x installed. Then, clone this repository and install the required packages.

```bash
git clone https://github.com/yourusername/idiom-suggestor.git
cd idiom-suggestor
# Execute Each cell in Jupyter files
```
## Fine-Tuning Configurations
- Model: NousResearch/Llama-2-7b-chat-hf
- Quantization: 4-bit precision using BitsAndBytes
- PEFT: LoRA with an attention dimension of 64 and an alpha scaling parameter of 16
- Training Epochs: 5
- Optimizer: AdamW with a cosine learning rate scheduler.

## Model Evaluation Using ROUGE Scores

To assess the quality of the generated idiomatic expressions, we use the ROUGE (Recall-Oriented Understudy for Gisting Evaluation) metric. 
Ensure you have the `rouge-score` library installed to use the ROUGE metrics:

```bash
pip install rouge-score
```
