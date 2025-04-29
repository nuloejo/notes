# AWS DeepDoc Scan

<a href="https://awscommunityday.cz/2025/sessions/acd950/">AWS DeepDoc Scan</a>
by <a href='https://www.linkedin.com/in/romanceresnak/'> Roman Ceresnak </a>
***by DevOpsGroup***

## Search for data

1. The user asks a question
2. The intelligent solution retrieves the required information and presents it as text.

> The intelligent solution provides the source of the information

### Use Case 1:

> Elimination of manual work and of error

* Asked Question
* Finding information across multiple documents
* Combining text into a response
* Answer to the given question

### Use Case 2.

* Asked Question
* Connecting to a data source via a connector
* Browsing sources
* Answer to the given question

### Use Case 3.

> Increased efficiently through audibility and traceability

* Asked Question
* Request logging
* Role verification
* Logging the entry

## Assigning permissions

> AWS -> External system (Confluence / Google Cloud)

* Creating connector connecting to the Principal Service -> Read

## Available Connectors

* 46 Defined
* 36 Cloud
* 10 On-prem
* Possibility to write custom connectors

## Crawling

> A **Crawler** is responsible for scanning and extracting data from Google Drive to build an up-to-date index.

* Connecting to Google Drive
* Discovery content
* Fetching Permissions & Access Control

## Indexing

> After a crawler fetches files from Google drive, the **Indexing** process

## Pre-processing in Amazon-Q Indexing

* Data Extraction
* COntent Normalization
* Stopword Removal & Tokenization
* Stemming & Lemmatization
* Metadate Enrichment
* Access Control Pre-processing

## Post-processing in Amazon Q Indexing

* Query Understanding & Expansion
* Re-ranking & Relevancy Scoring
* Semantic Search & NLP Enhancements
* Permission Enforcement and Filtering
* Post-retrieval After

### What is under the hood

* User Question
* Query processing
    * Understanding query
    * Context Management
* Indexing
    * Engine
    * Neural Language Processing
        * Full-text INdex
        * Vector Index
        * Metadata Index
* Data sources
    * Amazon s3
    * Confluence (Knowledge base)
    * Google Drive (Documents, Sheets)
    * Web Content (Public Sites)
* Data Processing
* Indexing
* Lambda post-processing

---









