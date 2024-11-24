# IndLegal - Advance Legal Summarizer

* * *

**About the Project**
---------------------

This project focuses on automating the summarization of legal documents by transitioning from the **Indian Penal Code (IPC)** to the newly introduced **Bhartiya Nayay Sanhita (BNS)**. The primary objective is to generate concise, legally accurate summaries while adapting references from IPC to BNS, reflecting the latest provisions, punishments, and changes in the legal framework.

We leverage the **Hugging Face BART-base** model for abstractive summarization, customized for the legal domain. The project also includes a robust pipeline to preprocess, train, and evaluate the model efficiently without requiring extensive manual intervention.

* * *

**Key Features**
----------------

1.  **Legal Summarization Pipeline**
    
    *   Automatically summarizes legal texts into concise representations, tailored to the BNS framework.
    *   Handles long texts by splitting and merging outputs while preserving context.
2.  **IPC-to-BNS Mapping**
    
    *   Seamlessly replaces IPC references with equivalent BNS provisions using a JSON-based mapping.
    *   Ensures legal accuracy by including updated terminologies, added provisions, and changes in punishments.
3.  **Custom Tokenization and Preprocessing**
    
    *   Tokenizes input legal documents and processes them to fit within BART's 1024-token limit.
    *   Efficient data handling using Hugging Face’s `datasets` library.
4.  **Beam Search Optimization**
    
    *   Uses beam search decoding to generate the best possible summaries with parameters tuned for high accuracy.
5.  **Metrics and Evaluation**
    
    *   Includes evaluation using ROUGE scores, ensuring summaries meet linguistic and legal standards.

* * *

**How to Run the Project**
--------------------------

### **Prerequisites**

*   Python 3.8 or higher.
*   Install the required Python libraries:
    
    ```bash
    pip install transformers datasets torch rouge_score absl-py evaluate
    ```
    

### **Steps to Run**

        
3.  **Run the Prebuilt Pipeline**
    
    *   The project includes a preconfigured pipeline to streamline the summarization process.
    *   To preprocess the data, tokenize, and train the model:
    *   Just provide the `custom_sen` as your legal case content. 

    ![pipeline](images/pipeline.png)

        
4.  **Generate Summaries**
    
    *   You can generate summaries using the fine-tuned model, just run pipeline and you can also see the rouge score.
        

* * *

**Project Pipeline**
--------------------

Our project includes a prebuilt pipeline, so you don’t need to implement everything from scratch. The pipeline automatically handles the following steps:

1.  **Data Preprocessing**
    
    *   Tokenizes and formats the data for the BART model using a data collator.
    *   Manages truncation and splitting for long texts.
2.  **Model Training and Fine-Tuning**
    
    *   Fine-tunes the BART model on legal datasets, using IPC-to-BNS mappings and summaries.
3.  **Evaluation**
    
    *   Evaluates the model using metrics like ROUGE and BLEU, ensuring the output meets required standards.
4.  **Summarization Generation**
    
    *   Generates summaries for new legal texts with the trained model.

* * *

**Project Structure**
---------------------

```graphql
├── bart_legal_summ/            # Saved BART Trained Model
├── mapping/                    # JSON file for IPC-to-BNS mapping
├── main_model.ipynb/           # Python scripts for pipeline             
├── README.md                   # Documentation
├── Project_Report.pdf          # Project Report
└── Project_Presentation.pdf    # Project Presentation 
```

* * *

**Customization**
-----------------

*   **Change Model Parameters:** Modify parameters like `num_beams`, `length_penalty`, and `max_length` in the `pipeline.py` script to optimize summaries.
*   **Adjust Mapping:** Update the IPC-to-BNS mapping JSON file (`mapping/ipc_to_bns.json`) to include new sections or custom mappings.

* * *

**Future Scope**
----------------

1.  Extend support for multilingual summarization (e.g., Hindi and regional languages).
2.  Integrate into a web platform for real-time legal text summarization.
3.  Improve accuracy by training on a larger, domain-specific legal corpus.
4.  Implement the lightRAG for the better low level and high level context.
