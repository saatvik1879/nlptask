# NLP task
## approach
I am going to use cosine similarity to find the top 5 paragraphs based on . To answer the queries I am using DistilBERT from hugging face question answering pipeline, where I will pass the above 5 paragraphs as context to the model. using the context and query the model would generate the answer.and then deploy the model using gradio.
## implentation
### data prepocessing
before applying cosine similarity on the paragraphs we need to convert the data in csv into word embeddings and passage embeddings

I have converted the given dataset into csv first.then I uploaded my data onto colab. then converted that into a python list. to remove duplicate elements in paragraphs i used`list(set(paragraphs))`

after converting into list . I have used nltk tokenizers to tokenize , stem and remove stopwords from my paragraphs
### vectorizing the paragraphs and query 
after the preprocessing, tfidf vectorizer to construct a matix `where the number of rows = number of unique words` and each row represents a paragraph and each entry is the tfdif score of the given word(column) in the given paragraph(row)
we similarly vectorize the query where the number of columns is the same as that of paragraph matrix
### implementing cosine similarity
here we perform matrix multiplication b/w query vector and paragraph matrix. then we get a similarity score for each row we find the highest 5 scores and the corressponding 5 paragraphs form the context for the BERT model
### building model to process the query and the context from above
for the model I have directly used the model from hugging face transformers
### deployment of model
the deployment of model is done on gradio.I have hosted the model on hugging face spaces. the link to the space is https://huggingface.co/spaces/saatvik1879/NLPtask
to deploy the model I neede to add `scikit-learn`,`torch` and `transformers` to `requirements.txt`. 
## the 🤗 space is currently private and please messege me to turn the space public.

![Alt text](/img1.jpg?raw=true "Optional Title")
![Alt text](/img2.jpg?raw=true "Optional Title")
