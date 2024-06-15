# CHAT With DATA

## Overview

This project is a Streamlit web application designed to facilitate the process of querying CSV files using natural language questions. The application leverages the `langchain` and `Groq` libraries to convert user queries into SQL statements, execute them on the uploaded CSV data, and return the results in a user-friendly interface.

## Features

- **Upload CSV Files**: Users can upload CSV files to be queried.
- **SQL Schema Display**: The app displays the SQL schema of the uploaded CSV file.
- **Natural Language to SQL**: Users can input natural language questions about the data, which are then converted into SQL queries.
- **Query Execution**: The generated SQL queries are executed on the uploaded CSV data, and the results are displayed.

## Installation

1. **Clone the repository**:
    ```sh
    git clone <repository-url>
    cd <repository-directory>
    ```

2. **Install dependencies**:
    ```sh
    pip install -r requirements.txt
    ```

3. **Set up environment variables**:
    Create a `.env` file in the project root directory and add your Groq API key:
    ```env
    GSK_API_KEY="your_groq_api_key_here"
    ```

## Usage

1. **Run the application**:
    ```sh
    streamlit run app.py
    ```

2. **Upload a CSV File**:
    - Use the file uploader on the left side of the page to upload your CSV file.
    - The app will display a preview of the uploaded file and its SQL schema.

3. **Ask a Question**:
    - Enter a natural language question about the data in the text input field on the right side of the page.
    - Click the "Get Answer" button to generate and execute the SQL query.
    - The results will be displayed below the input field.

## Code Explanation

### Import Libraries

- **dotenv**: Loads environment variables from a `.env` file.
- **pandas**: For data manipulation and analysis.
- **streamlit**: To create the web application interface.
- **langchain**: For creating the text-to-SQL prompt template.
- **pandasql**: To execute SQL queries on pandas DataFrames.
- **groq**: To interact with the Groq API for generating SQL queries.

### Prompt Template

A template is defined to instruct the Groq model on how to convert a natural language question into an SQL query. 

### Main Function

The `main` function sets up the Streamlit interface:
- **Page Configuration**: Sets the page title, icon, and layout.
- **File Uploader**: Allows users to upload CSV files.
- **Data Preview and SQL Schema**: Displays a preview of the uploaded file and its SQL schema.
- **Question Input**: Provides a text input field for users to enter questions.
- **SQL Query Execution**: Converts the natural language question into an SQL query using the Groq API, executes the query on the uploaded CSV data, and displays the results.

### Error Handling

The application includes error handling to retry query generation and execution up to 5 times if an error occurs.

## Note

- Ensure that your CSV file's column names are alphanumeric and do not contain special characters, as these are replaced during the upload process.
- The API key for Groq is stored securely using environment variables. Make sure to set this up correctly to avoid authentication issues.

## Conclusion

This application simplifies the process of querying CSV files by allowing users to input natural language questions and receive SQL query results, making data analysis more accessible and efficient.
