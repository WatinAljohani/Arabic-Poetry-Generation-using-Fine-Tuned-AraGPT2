# Arabic Poetry Generation using Fine-Tuned AraGPT2

This project explores the generation of Arabic poetry using a fine-tuned version of the [AraGPT2](https://huggingface.co/aubmindlab/aragpt2-base) language model. We systematically experiment with different training configurations and evaluate the generated poems using both **quantitative metrics** (loss, perplexity) and **qualitative human ratings** (fluency, coherence, emotion, and structure).

> This work was developed as part of the **ARTI 557 | Selected Topics in AI (Generative AI)** course.

---

## Project Objectives

- Fine-tune the AraGPT2 model on an Arabic poetry dataset  
- Evaluate model performance across multiple training configurations  
- Analyze the impact of hyperparameter tuning on poetry generation quality  

---

## Dataset

- **Source**: [arbml/ashaar](https://huggingface.co/datasets/arbml/ashaar)  
- **Type**: Classical Arabic poetry dataset  
- **Attributes**:  
  - `poem title`, `poem verses`, `poem theme`, `poem meter`  
  - Poet metadata: name, era, location  
- **Preprocessing**:  
  - Removed diacritics and extra whitespace  
  - Cleaned verses and added prompts like `[قصيدة حزينة]`  
  - Tokenized with AraGPT2's tokenizer (max length: 256)  

---

## Experimental Setup

Six experiments were conducted with variations in:  
- **Sample Size**: from 5K to 50K  
- **Epochs**: 2 or 3  
- **Learning Rate**: 5e-5 or 1e-4  

---

## Experiment Results

| Experiment | Sample Size | Epochs | Learning Rate | Evaluation Loss | Perplexity     | Human Score (/5) |
|------------|-------------|--------|----------------|------------------|----------------|------------------|
| 1          | 5K          | 2      | 5e-5           | 7.7391           | 2,296.43       | 2.5              |
| 2          | 10K         | 2      | 5e-5           | 8.5515           | 5,174.41       | 3.2              |
| 3          | 50K         | 2      | 5e-5           | 10.3921          | 32,599.92      | **3.8** ✅ Best   |
| 4          | 50K         | 3      | 5e-5           | 11.0192          | 61,033.32      | 2.4              |
| 5          | 50K         | 2      | 1e-4           | 10.7590          | 47,049.80      | 3.2              |
| 6          | 50K         | 3      | 1e-4           | 11.6218          | 111,505.75     | 2.2              |

---

## Key Findings

- **Experiment 3** achieved the best balance of fluency, emotion, and coherence in generated poems.  
- Loss and perplexity values did not always correlate with poetic quality—human judgment was essential.  
- Increasing epochs or learning rate didn't consistently lead to better outcomes.  

---

## Project Contributors

- **Watin Aljohani**  
- **Mayyan Alharbi**   

---

