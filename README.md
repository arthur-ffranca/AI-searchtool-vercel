# AI-Assisted Product Data Extraction & Matching Pipeline

A full-stack data extraction system designed to collect, process, deduplicate and structure product-related information from multiple web sources.

The project was originally created to replace a Streamlit prototype with a more scalable and production-oriented architecture using **Next.js**, **FastAPI**, **Neon/PostgreSQL**, **Exa** and **Tavily**.

## Overview

This application receives a list of products through a web interface, processes searches in batches, retrieves information from external web sources, removes duplicated URLs, extracts relevant fields from the returned content and stores structured results in a PostgreSQL database.

The main goal is to transform messy and fragmented web data into structured outputs that can support business analysis, competitive monitoring and data integration workflows.

## Key Use Cases

* Product data extraction
* Competitor monitoring
* Price tracking
* Technical specification collection
* Market intelligence
* Data standardisation
* Source deduplication
* Product matching support
* Data quality validation

## Tech Stack

| Layer           | Technology                              |
| --------------- | --------------------------------------- |
| Frontend        | Next.js                                 |
| Backend         | FastAPI                                 |
| Database        | Neon / PostgreSQL                       |
| Web Search APIs | Exa, Tavily                             |
| Processing      | Python                                  |
| Deployment      | Vercel-compatible frontend architecture |
| Data Storage    | Structured relational tables            |

## How It Works

1. The user submits a list of products through the web interface.
2. The frontend sends the product list to the backend search endpoint.
3. The backend processes the products in batches.
4. Exa and Tavily are queried in parallel to retrieve relevant web results.
5. Returned URLs are deduplicated to avoid repeated sources.
6. A local extraction layer analyses the returned content and identifies relevant fields.
7. Extracted values are standardised and organised.
8. Results are stored in Neon/PostgreSQL for later analysis and reuse.

## Core Features

### Batch Product Processing

The system can process multiple products in a single workflow, making it suitable for repetitive research tasks and scalable data collection.

### Parallel Web Search

The backend uses Exa and Tavily as external retrieval APIs to collect product-related information from different sources.

### URL Deduplication

Search results are deduplicated by URL before extraction, reducing repeated sources and improving output quality.

### Structured Field Extraction

The extraction layer identifies and organises fields such as:

* Product name
* Price
* Competitor information
* Technical specifications
* Source URL
* Extracted values
* Search timestamp

### Database Storage

Results are stored in Neon/PostgreSQL, allowing historical searches, future comparisons and structured analysis.

### Data Quality Logic

The project includes logic focused on:

* Removing duplicated sources
* Standardising extracted fields
* Preserving source references
* Separating raw results from processed outputs
* Supporting review of uncertain or incomplete data

## Architecture

```text
User Interface
     |
     v
Next.js Frontend
     |
     v
FastAPI Backend
     |
     |----> Exa API
     |
     |----> Tavily API
     |
     v
Deduplication Layer
     |
     v
Local Extraction Logic
     |
     v
Neon / PostgreSQL Database
     |
     v
Structured Results
```

## Environment Variables

Create a `.env` file with the required API keys and database connection string.

```env
EXA_API_KEY=your_exa_api_key
TAVILY_API_KEY=your_tavily_api_key
DATABASE_URL=your_neon_postgresql_connection_string
```

Depending on the deployment setup, these variables should also be configured in the hosting platform environment settings.

## Why This Project Matters

This project demonstrates practical experience with real-world data integration challenges.

Although the system is focused on product data extraction, it involves several concepts that are directly relevant to data engineering and record-linkage workflows:

* Collecting data from inconsistent external sources
* Deduplicating repeated records
* Extracting structured fields from unstructured content
* Standardising messy data
* Preserving source traceability
* Creating a backend pipeline for repeatable processing
* Preparing data for matching, comparison and validation

The same principles can be applied to entity resolution, product matching, customer matching, supplier matching and other record-linkage problems.

## Relevance to Record Linkage

Record linkage requires identifying whether different records refer to the same real-world entity. This project supports similar logic by dealing with inconsistent product information gathered from multiple sources.

Relevant capabilities include:

* Source deduplication
* Attribute extraction
* Field normalisation
* Product comparison
* Structured storage
* Confidence-oriented validation
* Handling incomplete or inconsistent data

## Example Workflow

```text
Input:
- Product A
- Product B
- Product C

Processing:
- Search external sources
- Retrieve URLs and content
- Remove duplicated URLs
- Extract relevant fields
- Store structured outputs

Output:
- Product attributes
- Competitor references
- Price information
- Source links
- Search history
```

## Potential Improvements

Future improvements could include:

* Fuzzy matching between similar product names
* Confidence scores for extracted fields
* Human review queue for uncertain matches
* Scheduled monitoring jobs
* Dashboard for price and competitor tracking
* API authentication
* Export to CSV or Excel
* Integration with BI tools
* LLM-based extraction validation

## Project Status

Functional prototype.

The system is able to receive product inputs, query external sources, deduplicate URLs, extract structured information and store results in a database.

## Author

Developed by **Arthur Fermino Franca**

Focused on data engineering, business intelligence, automation, data quality and AI-assisted data workflows.
