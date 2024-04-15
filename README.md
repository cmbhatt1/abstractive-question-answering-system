# abstractive-question-answering-system
This is a simple chatbot designed for the healthcare domain. It can be used to answer questions which a patient might have (i.e medical terms) and also for a fictional hospital to keep track of their patients.

## Key Features
Patient Support: The chatbot can answer common medical questions, provide information about symptoms and treatments, and offer guidance on when to seek professional medical advice.
Hospital management: Type in no when the website is launched and then type in any number between 1-1000 to retrieve data related to a patient.

## Model
This chatbot is built using the BART model for conditional generation with the help of Hugging Face.

## Data
Patients: Model has then been fine tuned on wikipedia articles and pages for Health and fitness category.
Management: Synthetic data generated using faker

## Working
The data is scraped, processed and then stored in a vector database in chromadb which is open source. When a patient enters a query, it is converted to a vector and based on cosine similarity some data is retrieved.
This data, with the help of BART, is converted to NLP. 

## Questions
**What is the difference between extractive and generative Question Answering systems?**
As the name suggests, an extractive question answering system extracts data from the provided context based on a question.
It does not try to understand the deeper semantics of the question but instead retrieves relevant data directly from the context.
On the other hand, generative question answering systems use a language model to understand the semantics of the question and deliver the output in natural language. 
This project is based on a generative QA model

**Explain the role of the Transformers library in building a QA system.**
Transformers library released by hugging face contains multiple models designed for specific tasks. For the QA task, there are models such BERT, distilBERT, roBERTa etc. These models are already hypertuned.
Each model has it's own tokenizer too. Transformers library reduce the need to develop a model from scratch. This saves a lot of time and effort.
These models can be fine tuned on specific domain(healthcare in out case) based on our requirements to improve the performance. 

**How does fine-tuning a pre-trained model improve its performance on a specific QA task?**
Fine-tuning a pre-trained model means providing the model with a lot of data to answer the questions based on a specific domain. If the model has more context, it will be easier for the model to answer questions better.

**Describe the trade-offs between different QA model architectures in terms of accuracy, speed, and resource requirements.**
If a model is expected to be more accurate, it would mean that it is loaded with a lot of data. Hence, may require more resources for computation and memory.
BERT is more accurate but slower and is resource intensive. 
distilBERT is smaller and lighter version but is a little less accurate.
ROBERTa is more accurate than BERT but is slower and more resource intensive than BERT

**What are the challenges of deploying a QA model in a production environment?**
1) Scalability to make it available to multiple users without it crashing
2) Resource requirements to improve accuracy and speed 
3) Reducing the latency of the response
4) Maintaining the model and regularly updating the knowledge base
5) Data bias
6) Legal and ethical concerns

**How would you evaluate the success of your QA system beyond accuracy metrics?**
Feedback from the users would be the most important success metric.

**Discuss strategies to handle ambiguous or unanswerable questions.**
We can give fall back responses like "I am not sure about that" or give the closest topics(vector similarity) as a response. 
Like chatgpt, we can give 2 responses and based on users feedback, one will be selected. This will also help us in the future.

**How can you collect feedback or data to continuously improve your QA system?**
I believe scraping the entire wiki page instead of the summary will be much helpful. Since this model is designed for patients, it doesn't have to be technical but has still has to be accurate.
So, we don't necessarily need data from medical journals or articles.

**How can QA systems be made more robust to handle noisy or unseen data?**
To make QA systems more robust against noisy or unseen data, use data augmentation, including generating synthetic data and perturbations, to expose the model to a variety of scenarios. Apply preprocessing for noise reduction, implement confidence scores or uncertainty measures, and create feedback loops for iterative improvement. Fine-tuning pre-trained models and using domain-specific training also enhance the system's ability to handle diverse inputs.

**What ethical considerations should be taken into account when building a QA system?**
When building a QA system, ensure data privacy and security, especially when handling sensitive information, and strive for fairness and transparency by avoiding biased outputs and making the model's decision-making process interpretable.
