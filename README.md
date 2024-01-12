# RAG-LLM-Insights

RAG is a type of AI framework that enhances the capabilities of Large Language Models (LLMs). Usually, LLMs are great at answering questions based on the information they were trained on. However, they struggle with new or private data, like a company's internal documents on Confluence, Google Drive, or SharePoint. When asked about such data, LLMs might not know the answer or, worse, provide incorrect information.

Here's where RAG comes in. It allows an LLM to access and use private data to answer questions. The process is fairly straightforward:

- **Step 1:** When someone asks a question, this query is run against a database that contains the relevant private data. This data is often stored in a special format called vectorized data.
- **Step 2:** The database then provides a set of relevant documents based on the query.
- **Step 3:** The LLM receives these documents and uses them to understand the context of the query.
- **Step 4:** Finally, the LLM crafts an answer based on this new, specific information rather than relying solely on its original training data.
  
This approach helps LLMs provide accurate answers to queries about private or company-specific data, expanding their usefulness in real-world applications.
