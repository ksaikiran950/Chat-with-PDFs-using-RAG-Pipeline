Chat with PDF Using RAG Pipeline

Overview The objective of this task is to develop a Retrieval-Augmented Generation (RAG) pipeline that enables users to interact with semi-structured data in PDF files. The system will process these PDFs by extracting, chunking, embedding, and storing the data for efficient retrieval. Users can query the system in natural language to receive precise answers and perform comparisons using a Language Learning Model (LLM).

Functional Requirements

Data Ingestion
Input

PDF files containing semi-structured data.
Process

Extract Text: Use a PDF parser (e.g., PyPDF2, pdfplumber) to extract text and structured information.
Chunk Data: Segment the extracted text into logical chunks (e.g., paragraphs, tables) for improved granularity.
Embed Data: Convert chunks into vector embeddings using a pre-trained embedding model (e.g., Sentence Transformers, OpenAI embeddings).
Store Embeddings: Save the embeddings in a vector database (e.g., Pinecone, Weaviate, FAISS) for efficient similarity-based retrieval.
Query Handling
Input

A natural language question from the user.
Process

Convert Query: Transform the user's question into vector embeddings using the same embedding model used during data ingestion.
Similarity Search: Search the vector database to find the most relevant chunks based on the query embeddings.
Context Preparation: Pass the retrieved chunks and user query to the LLM along with a context or agentic prompt to generate a response.
Comparison Queries
Input

A user query requesting a comparison across data points in multiple PDFs.
Process

Extract Comparison Fields: Identify terms or fields from the query that require comparison (e.g., "unemployment rates by degree type").
Retrieve Data: Fetch relevant chunks from the vector database.
Aggregate Data: Process and aggregate the retrieved data for structured comparison.
Generate Comparison Response: Use the LLM to generate a comparison response in a structured format (e.g., table, bullet points).
Response Generation
Input

Relevant information retrieved from the vector database and the user’s query.
Process

RAG Prompting: Use the retrieved data and query to create retrieval-augmented prompts for the LLM.
Generate Response: Produce a detailed response with exact values and context, ensuring factual accuracy by incorporating the retrieved data.
Example Data and Usage

Example PDF

URL: [Tables, Charts, and Graphs](https://www.hunter.cuny.edu/dolciani/pdf_files/workshop-materials/mmc presentations/tables-charts-and-graphs-with-examples-from.pdf )
Queries Query 1: Extract unemployment information based on type of degree (Page 2)

Process: Retrieve and process data from Page 2. Extract and present the unemployment rates categorized by degree types.
Query 2: Extract tabular data (Page 6)

Process: Identify and retrieve tabular data from Page 6. Present the table accurately in the response.
