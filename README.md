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


