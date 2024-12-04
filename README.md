# 1.3M_Korea
README: Email Validation and Data Cleaning Script
Overview
This script processes a dataset to:

Validate Email Addresses: Ensure that email addresses in the dataset match a proper format.
Convert created_date_time: Convert the created_date_time column to a proper datetime format.
Handle Duplicates: Identify and separate duplicate rows.
Dataset Separation: Create two output datasets:
Cleaned Dataset: Contains valid rows.
Junk Dataset: Contains rows with invalid emails, invalid datetime values, or duplicates.
The script is designed for use in Google Colab and supports uploading and downloading files within the Colab environment.

Features
Email Validation:

Uses a regular expression to validate email addresses.
Ensures that only rows with properly formatted emails are included in the cleaned dataset.
Datetime Conversion:

Converts the created_date_time column to a proper datetime format.
Rows with invalid or missing datetime values are moved to the junk dataset.
Duplicate Handling:

Identifies duplicate rows in the dataset and includes them in the junk dataset.
File Output:

Saves valid rows to cleaned_dataset.csv.
Saves invalid rows (junk) to junk_dataset.csv.
Integration with Google Colab:

Allows file uploads for processing.
Automatically downloads the cleaned and junk datasets after processing.
Requirements
Environment:

Google Colab or any Python environment with support for the pandas library.
Python Libraries:

pandas: For data manipulation.
google.colab: For file upload and download in Colab.
How to Use the Script
Step 1: Upload Your Dataset
When prompted, upload your dataset (CSV file).
The dataset should contain an email column and optionally a created_date_time column.
Step 2: Script Processing
Email Validation:

The script uses a regular expression to validate email addresses.
Valid emails are included in the cleaned dataset, while invalid ones are moved to the junk dataset.
Datetime Conversion:

If the created_date_time column is present, it is converted to a datetime format.
Rows with invalid datetime values are moved to the junk dataset.
Duplicate Removal:

Duplicate rows are identified using pandas.duplicated() and moved to the junk dataset.
Dataset Separation:

Cleaned Dataset: Contains rows with valid emails, valid created_date_time values, and no duplicates.
Junk Dataset: Contains rows with invalid emails, invalid datetime values, or duplicates.
Step 3: Download the Processed Datasets
The cleaned dataset is saved as cleaned_dataset.csv.
The junk dataset is saved as junk_dataset.csv.
Both files are automatically downloaded to your local machine.
Output
Cleaned Dataset (cleaned_dataset.csv):

Contains rows with:
Valid email addresses.
Valid datetime values (if created_date_time exists).
No duplicate rows.
Junk Dataset (junk_dataset.csv):

Contains rows with:
Invalid email addresses.
Invalid or missing created_date_time values (if the column exists).
Duplicate rows.
Example Input and Output
Example Input Dataset
email	created_date_time	other_column
valid@example.com	2023-01-01 12:00:00	Data1
invalid_email.com	2023-01-02 13:00:00	Data2
valid@example.com	2023-01-01 12:00:00	Data1
another@domain.com	InvalidDate	Data3
Example Output: Cleaned Dataset
email	created_date_time	other_column
valid@example.com	2023-01-01 12:00:00	Data1
Example Output: Junk Dataset
email	created_date_time	other_column
invalid_email.com	2023-01-02 13:00:00	Data2
valid@example.com	2023-01-01 12:00:00	Data1
another@domain.com	InvalidDate	Data3
Script Details
Email Validation
Regex Used: ^[\w\.-]+@[\w\.-]+\.\w+$
Matches valid email formats like user@example.com.
Datetime Conversion
Converts created_date_time to datetime using:
python
Copy code
pd.to_datetime(df['created_date_time'], errors='coerce')
Rows with invalid or missing values are marked as junk.
Duplicate Identification
Uses pandas.duplicated() to flag duplicate rows.
Customization
Adjust Regex:

Modify the email validation pattern to match specific requirements.
Datetime Format:

Customize datetime conversion if specific formats need to be enforced.
Thresholds:

Define additional criteria for separating valid and junk datasets.
Troubleshooting
Missing Columns:

Ensure the dataset includes the email column. The created_date_time column is optional.
Invalid Files:

Verify that the uploaded file is a valid CSV.
Large Datasets:

For large files, ensure sufficient memory is available.
License
This script is free to use and modify. Attribution is appreciated but not required.
