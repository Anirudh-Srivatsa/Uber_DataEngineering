# Introduction

In this project, my main objective is to work with a dataset similar to Uber's and perform various data engineering tasks. I will build a data model using a fact and dimension format and write transformation code using Python. To deploy my code, I will utilize a compute instance on Google Cloud and leverage an open-source data pipeline tool called Mage.

The data will be loaded into BigQuery, which acts as my data warehouse. Furthermore, I will create a final dashboard using LookerStudio, a powerful business intelligence tool. This dashboard will provide visual representations and insights based on the processed data.

Additionally, I will explore the various Google Cloud Platform (GCP) services that will be utilized throughout the project, such as Google Cloud storage, compute engine, and BigQuery. These GCP services offer a robust infrastructure for managing and analyzing data effectively.

# Technology Used

Programming Language - Python

Google Cloud Platform -

1. Google Storage
2. Compute Instance
3. BigQuery
4. Looker Studio

Modern Data Pipeine Tool - [Mage](https://www.mage.ai/)


# Dataset

TLC Trip Record Data Yellow and green taxi trip records include fields capturing VendorID, tpep_pickup_datetime, tpep_dropoff_datetime, passenger_count, trip_distance, pickup_longitude, pickup_latitude, RatecodeID, dropoff_longitude, dropoff_latitude, payment_type, fare_amount, tip_amount, tolls_amount and total_amount. [Dataset](https://github.com/Anirudh-Srivatsa/Uber_DataEngineering/blob/main/Data/uber_data.txt)


# Data Modeling

As the project execution commences, the initial phase focuses on data modeling and gaining a comprehensive understanding of the dataset and its corresponding data dictionary. This crucial step ensures the design of an effective data model that aligns with the objectives of the project.

To convert the flat hierarchy table into a structured format, an online tool called Lucidchart is employed. Lucidchart enables the transformation of the data frame into fact and dimension tables. Multiple dimension tables are generated based on the information that would have originally been within the fact tables. This approach facilitates a more realistic comprehension and visualisation of the data.

The dimension model can be further enhanced to meet specific project requirements by introducing additional columns, extracting supplementary information, and gaining a deeper insight into the dataset. For instance, incorporating details such as pick-up day, pick-up month, and pick-up weekday can provide valuable context.

In this scenario, the date-time dimension table assumes the role of the primary key, while the passenger account and trip distance represent transactional values that change over time. These values are distributed across distinct dimension tables, enabling exploration of actual joins.

Likewise, dimension tables are created for pick-up location, pick-up location ID, drop location, drop location ID, rate code, and payment type. These tables incorporate primary keys, foreign keys, and relevant columns to accurately depict associated information.

![image](https://github.com/Anirudh-Srivatsa/Uber_DataEngineering/assets/136144340/e2f9dff7-f344-42ea-bc00-cef88255a4f7)

# The Transformation Code(Python)

During the project's transformation code phase in Python, the main objective is to convert the flat file into a dimension model using structured programming code. This process involves dropping duplicates, resetting the index, and assigning unique values to the date-time column.Once the flat file is successfully converted into dimension tables, the subsequent task is to create the fact table by merging the dimension tables. [Here](Data_processing_pyt.ipynb)


Upon completing the transformation code, the data can be uploaded to Google Cloud storage for deployment. Analyzing the data, executing queries, and developing a dashboard follow as subsequent steps in the project.

# Google Cloud Storage & Mage Installation

On Google Cloud console, we create buckets for storing our dataset.

For Mage installation, we start by creating a compute engine instance on Google Cloud. Configure the instance with appropriate CPU and memory specifications. we then connect to the instance and install the necessary packages, such as Python and pandas.

To install Mage, we use either 'Docker' or 'Pip'. In our case, we use 'pip', and the installation commands can be executed in the virtual machine. Once Mage is installed, we start a project by running 'mage start project_name'.

To enable access to the instance, we create a firewall rule to allow requests from port 6789 and specifiying IP address. This will enable accessing the user interface (UI) of the instance.

Within the Mage project, to load data, we provide the API name to extract data from our bucket which contains dataset. Using pandas data frames and transformation blocks, we then transform the data according to the desired data model. The code is later run, and the results, including the created fact table, are verified.

By running the exporter code, we load the data into BigQuery using ymal file and create a table based on the provided name and configuration. We can then preview the data set and tables in BigQuery. This way, the ETL task is completed.

# BigQuery Data Analysis

In BigQuery, analytical queries can be performed using SQL commands on the fact table, such as Analytics Query.sql

In this phase of the project, we select columns from multiple tables to extract data to create visualization.

# Building Dashboards

Once the BigQuery is connected, the data set can be added to the report. The dashboard can be customized by adding text, filters, and different sections for filtering data by VendorID, payment type, rate code and trip distance. Also, the dashboard is created to display metrics such as total revenue, record count, average trip distance, average fare amount and average tip amount, which can be used to make informed decisions. Calculated fields are used to show maps of pickup locations highlighting vendor ID and rate code names. Additionally, charts such as bar charts are used to visualize the average amount by rate code, average amount by payment type, pie charts for rate code and vendor ID . The dashboard provides insights and allows for exploration of data by manipulating columns and visualizations.

To view dashboard [Here](Data_model_flowchart.jpeg)



