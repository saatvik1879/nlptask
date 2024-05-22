# NLP task
hugging face link - https://huggingface.co/spaces/saatvik1879/NLPtask

lucidchart link - https://lucid.app/lucidchart/1f8a351b-464d-4554-945d-a105f2827234/edit?viewport_loc=-11%2C-263%2C2214%2C1206%2C0_0&invitationId=inv_aeff731a-468c-438f-a991-8475fc563adf
## approach
I am going to use cosine similarity to find the top 5 paragraphs based on. To answer the queries I am using DistilBERT from the \hugging face question answering pipeline, where I will pass the above 5 paragraphs as context to the model. using the context and query the model would generate the answer. and then deploy the model using gradio.
## implementation
### data preprocessing
before applying cosine similarity to the paragraphs we need to convert the data in CSV into word embeddings and passage embeddings

I have converted the given dataset into CSV first. then I uploaded my data onto colab. then converted that into a Python list. to remove duplicate elements in paragraphs I used `list(set(paragraphs))`

after converting into the list. I have used nltk tokenizers to tokenize, stem and remove stopwords from my paragraphs
### vectorizing the paragraphs and query 
after the preprocessing, the tfidf vectorizer to construct a matrix `where the number of rows = number of unique words` and each row represents a paragraph and each entry is the tfidf score of the given word(column) in the given paragraph(row)
we similarly vectorize the query where the number of columns is the same as that of the paragraph matrix
### Implementing cosine similarity
here we perform matrix multiplication b/w query vector and paragraph matrix. then we get a similarity score for each row we find the highest 5 scores and the corresponding 5 paragraphs form the context for the BERT model
### Building a model to process the query and the context from the above
for the model, I have directly used the model from the hugging face Transformers
### deployment of model
the deployment of the model is done on gradio. I have hosted the model on hugging face spaces. the link to the space is https://huggingface.co/spaces/saatvik1879/NLPtask
to deploy the model I needed to add `scikit-learn`, `torch` and `transformers` to `requirements.txt`. 
## The 🤗 space is currently private and please message me if it's still private to turn the space public.

![Alt text](/img1.jpg?raw=true "Optional Title")
![Alt text](/img2.jpg?raw=true "Optional Title")
## to run this model, run the cells in ipynb file in order after uploading the files with paragraphs and queries files I have included in my drive link below(I have deployed my model to avoid this)
drive link for the files - https://drive.google.com/drive/folders/1uyInhqB9bz3w8EuHkVgoDtCzfclDmNHl?usp=sharing
