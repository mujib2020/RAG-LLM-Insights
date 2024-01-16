# RAG-LLM-Insights

RAG is a type of AI framework that enhances the capabilities of Large Language Models (LLMs). Usually, LLMs are great at answering questions based on the information they were trained on. However, they struggle with new or private data, like a company's internal documents on Confluence, Google Drive, or SharePoint. When asked about such data, LLMs might not know the answer or, worse, provide incorrect information.

Here's where RAG comes in. It allows an LLM to access and use private data to answer questions. The process is fairly straightforward:

- **Step 1:** When someone asks a question, this query is run against a database that contains the relevant private data. This data is often stored in a special format called vectorized data.
- **Step 2:** The database then provides a set of relevant documents based on the query.
- **Step 3:** The LLM receives these documents and uses them to understand the context of the query.
- **Step 4:** Finally, the LLM crafts an answer based on this new, specific information rather than relying solely on its original training data.
  
This approach helps LLMs provide accurate answers to queries about private or company-specific data, expanding their usefulness in real-world applications.

#### Loading data
LangChain offers superb capabilities for importing data from a range of sources including the Web, Wikipedia, Google Drive, and others. A comprehensive list of all the document loader integrations available with external data sources: https://python.langchain.com/docs/integrations/document_loaders/

**Document loaders** load documents from many different sources. LangChain provides over 100 different document loaders as well as integrations with other major providers in the space, like AirByte and Unstructured. LangChain provides integrations to load all types of documents (HTML, PDF, code) from all types of locations (private S3 buckets, public websites).

#### Splitting the Data into Manageable Chunks
Let's consider a scenario where we have a large file which could span over 20 or 30 pages. We start by loading all these pages into the application's memory.

The next step involves breaking down this extensive data into smaller, more manageable chunks. Each chunk consists of 512 characters. To achieve this, we employ a method named *get_splitted_chunks*. This method uses a tool called RecursiveCharacterTextSplitter, which is designed to divide the text into multiple sections.

The *RecursiveCharacterTextSplitter* is configured with a chunk_size of 512 and a chunk_overlap of 100. chunk_size determines the number of characters in each chunk, while chunk_overlap allows for a small overlap between consecutive chunks. This overlap ensures that no critical information is lost or misinterpreted during the splitting process.

The function *get_splitted_chunks(data)* takes the loaded data as input and uses the splitter to segment the data into chunks, each comprising 512 characters. This approach makes the handling of large texts more efficient, especially when processing or analyzing the data in subsequent steps.

#### Making Text Chunks Ready for a Vector Database
In this important part of the process, we turn text chunks into a form that fits into Chroma DB, a kind of vector database that's free for anyone to use. This change has two main steps: vectorization and embedding. Let's go over what these mean.

**Vectorization:** This is just a fancy way of saying we're turning text into numbers. It's the first thing we do to make words or sentences into a number format. A usual way to do this is with something called term frequency-inverse document frequency (TF-IDF).

**Embedding:** Once we've turned the text into numbers, we then 'embed' it. Embedding makes dense groups of numbers that show the deep meanings and connections between words or phrases. Tools like Word2Vec and FastText are often used for this. The goal is to arrange words so that those with similar meanings or used in similar ways are represented by similar groups of numbers.

#### Turning Text Chunks into Vectorized and Embedded Data
The function *get_db_retriever(chunks)* works with the chunks we've already made. It uses an embedding technique, specifically the OpenAIEmbeddings, to process these chunks. What it does is it applies this special algorithm to the chunks, which helps to translate and store them effectively. After this, the chunks are kept in the Chroma database. We then use this Chroma database for the next steps in our process.


**References:**
- https://python.langchain.com/docs/modules/data_connection/
- 
