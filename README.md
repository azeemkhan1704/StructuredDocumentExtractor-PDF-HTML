# Bid Extraction Tool using LLMs

## Project Overview
This project aims to extract structured information from Request for Proposal (RFP) documents in both PDF and HTML formats. The extracted information is mapped into a predefined JSON structure using a combination of PDF/HTML parsing, text extraction, and Language Models (LLMs) for accurate data interpretation.

## Objective
The primary objective of this project is to automate the extraction of critical bid information from unstructured documents. The key fields to be extracted include:

- **Bid Number**
- **Title**
- **Due Date**
- **Bid Submission Type**
- **Term of Bid**
- **Pre Bid Meeting**
- **Installation**
- **Bid Bond Requirement**
- **Delivery Date**
- **Payment Terms**
- **Additional Documentation**
- **MFG Registration**
- **Contract Cooperative**
- **Model Number**
- **Part Number**
- **Product**
- **Contact Information**
- **Company Name**
- **Bid Summary**
- **Product Specification**

## Features
- **File Parsing:** Handles both PDF and HTML formats.
- **Text Extraction:** Extracts relevant text sections from documents.
- **Information Structuring:** Uses LLMs to accurately map extracted information to a predefined JSON format.
- **Output:** Saves the structured information in a JSON file for each processed document.

## Folder Structure
```
project-directory/
├── Bid1/            # Contains input PDF/HTML files
├── Bid2/            # Contains input PDF/HTML files
├── ProcessedBids/   # Contains processed JSON files
├── emplay.ipynb     # Main script to run the project
├── .env             # Environment variables
├── requirements.txt # Project dependencies
├── .gitignore       # Files to ignore in Git
└── README.md        # Project documentation
```

## Setup Instructions
### Prerequisites
- Python 3.8+
- OpenAI API Key

### Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/azeemkhan1704/StructuredDocumentExtractor-PDF-HTML.git
   cd project-directory
   ```

2. Create a virtual environment and activate it:
   ```bash
   python -m venv venv
   source venv/bin/activate   # On Windows, use venv\Scripts\activate
   ```

3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

4. Create a `.env` file in the root directory and add your OpenAI API key:
   ```env
   OPENAI_API_KEY=your_openai_api_key_here
   ```

### Running the Project
1. Place your input files (PDF/HTML) in the `Bid1` and `Bid2` folders.
2. Run the main script:
   ```bash
   python emplay.ipynb
   ```
3. Processed JSON files will be saved in the `ProcessedBids` folder.

## Code Description
The main script performs the following steps:
1. **Load environment variables:** Loads the OpenAI API key from the `.env` file.
2. **Initialize the LLM model:** Uses the `ChatOpenAI` model from the `langchain` library.
3. **Define templates and prompts:** Uses templates to structure the prompts sent to the LLM.
4. **Text extraction:** Extracts text from PDF/HTML files using `PyPDF2` and `RecursiveCharacterTextSplitter`.
5. **Data processing:** Processes text chunks through LLM chains to extract and map information.
6. **Output:** Saves the structured information in JSON format.

## Example Output
```json
[
  {
    "bid_number": "Request For Proposal 168884",
    "title": "JA-207652 Student and Staff Computing Devices",
    "due_date": "27-JUN-2024 14:00:00",
    "bid_submission_type": "Online submission preferred, manual submission accepted",
    "term_of_bid": "3-year agreement with two successive one-year extensions, not to exceed 5 years total",
    "pre_bid_meeting": "June 10, 2024 at 2:00 PM via TEAMS video conference",
    "installation": "Deployment services include software installation, asset tagging, etching, device setup, and asset control reporting",
    "bid_bond_requirement": "Insurance, bid bond, or liability requirements as noted in the solicitation document",
    "delivery_date": "Within 5 business days of reporting an issue",
    "payment_terms": "Not specified",
    "additional_documentation": "Credit application or similar documentation may be required post-award",
    "mfg_registration": "Manufacturer or Authorized Reseller Qualifications required",
    "contract_cooperative": "May be used with local, state, federal, and grant-funded programs",
    "model_no": "Various models specified in the document",
    "part_no": "Various parts specified in the document",
    "product": "Student and Staff Computing Devices",
    "contact_info": "ALZATE, JASMINE, Email: JALZATE@dallasisd.org, Phone: (972)925-4100",
    "company_name": "Dallas Independent School District (Dallas ISD)",
    "bid_summary": "Request for Proposal for student and staff computing devices including laptops, desktops, tablet devices, and display monitors. Vendors can submit proposals for one or more categories of devices. Specifications and requirements detailed in the document.",
    "product_specification": "Detailed specifications provided for Student and Staff Computing Devices including minimum requirements for different tiers of devices such as Chromebook Laptops, Windows Laptops, Tablets, Desktops, and Display Monitors."
  }
]
```

## Dependencies
- dotenv
- os
- json
- PyPDF2
- langchain

## Requirements File
A `requirements.txt` file is provided to install the necessary dependencies using:
```bash
pip install -r requirements.txt
```

