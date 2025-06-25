# Language Learning for Grammar Feedback

An intelligent, real-time grammar correction system designed to enhance writing proficiency by providing accurate and context-aware feedback on grammatical errors. This project leverages an ensemble of state-of-the-art NLP models to deliver highly reliable corrections.

## 🌟 Abstract

 This project introduces an advanced grammar correction system that significantly improves writing proficiency by delivering real-time feedback on a variety of grammatical errors.  The system integrates three powerful sequence-to-sequence (seq2seq) models—T5, GECToR, and Coedit—and utilizes a BERT-based classification model to validate the generated corrections.  By employing a unique ensemble strategy, the system evaluates multiple correction candidates and selects the most reliable one based on classification confidence scores.  Trained on a large and diverse dataset of incorrect and corrected sentences, our system effectively addresses issues like subject-verb agreement, verb tense errors, and preposition misuse.  The project not only demonstrates a scalable and effective NLP solution but also lays the groundwork for future enhancements, including multilingual support and domain-specific adaptations.

## ✨ Key Features

-  **High Accuracy:** Achieves an impressive **96% accuracy** through a unique ensemble strategy.
-  **Multi-Model Ensemble:** Integrates T5, GECToR, and Coedit to leverage their individual strengths for more robust and nuanced corrections.
-  **Reliable Validation:** Employs a BERT-based classification model to score and validate the grammatical correctness of suggestions, ensuring high-quality feedback.
-  **Real-Time Feedback:** Designed to provide instantaneous corrections to help users improve their writing skills efficiently.
-  **Comprehensive Error Correction:** Effectively targets a wide range of common grammatical mistakes, including subject-verb agreement, verb tense, and preposition misuse.

## 🛠️ Technologies Used

The system is built using a powerful stack of modern NLP models and libraries:

- **Sequence-to-Sequence Models:**
    -  **T5 (Text-to-Text Transfer Transformer):** Used for generating fluent and coherent corrected sentences.
    -  **GECToR (Grammar Error Correction Transformer):** Specifically designed for explicit grammar error identification and correction.
    -  **Coedit (Collaborative Editing Transformer):** Focuses on improving sentence fluency while addressing grammatical issues.
- **Classification Model:**
    -  **BERT (Bidirectional Encoder Representations from Transformers):** Functions as a classifier to validate the grammatical correctness of the outputs from the seq2seq models.
- **Core Technologies:**
    -  **Python:** The primary programming language used for implementation and model training.
    -  **HuggingFace Transformers:** Utilized for fine-tuning and training the deep learning models.

## ⚙️ System Architecture & Methodology

Our approach is centered around an innovative ensemble strategy that combines the outputs of the three seq2seq models and uses a classifier to select the best correction.

### 1. Dataset and Preprocessing

 The system was trained on a dataset of incorrect sentences paired with their corrected versions. Preprocessing steps included:
-  Removing duplicate and erroneous entries.
-  Tokenizing sentences to be compatible with model architectures.
-  Padding and truncating sentences to a maximum length of 64 tokens.
-  Labeling sentences for the classification task (1 for correct, 0 for incorrect).

### 2. Model Fine-Tuning

Each model was fine-tuned on the preprocessed dataset:
-  **T5:** Fine-tuned to reformulate NLP tasks as text-to-text problems, using the prefix `"fix grammar:"` to guide the correction task.
-  **GECToR:** Fine-tuned specifically to identify and correct grammatical errors in a seq2seq setup.
-  **Coedit:** Optimized to maintain sentence fluency while performing grammar refinements.
-  **BERT Classifier:** Trained to evaluate sentence correctness and assign a confidence score.

### 3. Ensemble Strategy

To ensure the highest accuracy, we developed a unique ensemble method:
1.   **Generate Combinations:** An input sentence is processed through six different sequential combinations of the T5, GECToR, and Coedit models.
2.   **Score Outputs:** Each of the six generated corrections is passed to the fine-tuned BERT classification model, which assigns a confidence score based on its grammatical correctness.
    ```python
    scores = [Classification(output) for output in combinations]
    ```
3.   **Select Best Correction:** The correction with the highest score from the BERT classifier is selected as the final output.  This dynamic selection process ensures the most reliable correction is chosen for any given sentence.
    ```python
    return combinations[scores.index(max(scores))]
    ```

 This multi-faceted approach reduces bias, provides an objective evaluation of each potential correction, and leverages the collective strengths of all models to maximize performance.

## 📊 Results

The ensemble strategy significantly outperformed the individual models, highlighting the power of our integrated approach.

| Model | Accuracy/F1-Score | Key Strength |
| :--- | :--- | :--- |
| T5 |  85% Accuracy  |  Excels in generating fluent and coherent corrections. |
| GECToR |  72% Accuracy  |  Effective at explicit, short-sentence grammar corrections. |
| Coedit |  70% Accuracy  |  Maintains sentence fluency and performs well on subtle refinements. |
| BERT Classifier |  90% Accuracy / 92% F1-Score  |  High accuracy in validating grammatically correct sentences. |
| **Final Ensemble System** |  **96% Accuracy**  |  **Optimal performance by leveraging the strengths of each model**. |

 These results affirm the effectiveness of combining multiple specialized models with a robust validation layer for complex NLP tasks.

## 🚀 Future Enhancements

We recommend the following areas for future development to further improve the system:

-  **Expand Training Data:** Incorporate larger and more diverse datasets to enhance the models' ability to handle complex and varied sentence structures.
-  **Domain-Specific Tuning:** Fine-tune the models for specialized contexts, such as academic, technical, or business writing, to improve performance for specific use cases.
-  **Add Multilingual Support:** Extend the system's capabilities to support and correct grammar in multiple languages, broadening its application and user base.

## 🤝 Contributors

-  Reem Hussin 
-  Mohanned Mahmoud 
-  Mahmoud Essa 
-  Abdelrahman Ahmed
