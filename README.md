# Chat-with-Columnar-Database

---

## Overview

This is a tool designed to help users query and analyze advertising campaign data. It leverages advanced AI models to interpret user queries, identify relevant dataset columns, and generate SQL queries to extract meaningful insights from advertising data. This project integrates various technologies, including Google Generative AI and ClickHouse, to provide a seamless data analysis experience.

## Features

- **Query Interpretation:** Understands and enhances user queries related to advertising data.
- **Dynamic SQL Generation:** Automatically generates SQL queries based on user input and dataset schema.
- **Data Extraction:** Retrieves relevant data from a ClickHouse database.
- **Answer Framing:** Presents results in a user-friendly format.

## Technologies Used

- **Google Generative AI:** For query enhancement and text generation.
- **ClickHouse:** For querying and managing the advertising campaign data.
- **Pandas:** For data manipulation and analysis.
- **Python-dotenv:** For managing environment variables.

## Setup

1. **Clone the Repository:**

   ```bash
   git clone https://github.com/yourusername/advertising-data-analysis-agent.git
   cd advertising-data-analysis-agent
   ```

2. **Install Dependencies:**

   Create a virtual environment and install required packages:

   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows use `venv\Scripts\activate`
   pip install -r requirements.txt
   ```

3. **Environment Variables:**

   Create a `.env` file in the root directory with the following variables:

   ```plaintext
   GOOGLE_API_KEY=your_google_api_key
   LANGCHAIN_API_KEY=your_langchain_api_key
   ```

4. **Database Configuration:**

   Ensure ClickHouse is running locally and accessible. Update the database configuration if necessary.

## Usage

1. **Load Dataset:**

   Ensure your dataset is available at `MASTER_FILES/Master_Final.csv`.

2. **Run the Script:**

   Execute the main script to start the data analysis process:

   ```bash
   python main.py
   ```

3. **Query Examples:**

   - **What languages is EENADU Newspaper available in?**
   - **What is the Market for the top spent Channel?**

   The script will process these queries, generate SQL code, and provide results based on the dataset.

## Example

Here's an example of how the system processes a query:

1. **User Query:** "What is the Market for the top spent Channel?"
2. **Generated SQL Code:**

   ```sql
   SELECT
     Market,
     Channel,
     SUM(Amount) AS TotalAmount
   FROM campaigns
   GROUP BY
     Market,
     Channel
   ORDER BY
     TotalAmount DESC
   LIMIT 1;
   ```

3. **Query Result:**

   ```json
   [["North", null, 40648499795.36029]]
   ```

4. **Framed Answer:**

   The top-performing combination of market and channel in terms of total amount is the "North" market with no specific channel specified. This combination has generated a total amount of $40,648,499,795.36.

