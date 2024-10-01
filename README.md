# Snowflake-Learnings
A repository documenting my Snowflake learning journey, featuring foundational concepts, practical examples, and hands-on SQL queries to enhance cloud data warehousing skills

# Snowflake Overview

## What is Snowflake?
Snowflake is a **cloud-based data warehousing solution**, founded in 2012. It offers services for **data storage** and **analytics**, but it doesn’t rely on its own infrastructure. Instead, it operates on **Amazon S3**, **Microsoft Azure**, and **Google Cloud Platform**, leveraging the power of the cloud.

### Key Features:
- Available as **Software-as-a-Service (SaaS)**.
- Runs entirely on cloud infrastructure.

---

## Why Choose Snowflake?

Snowflake provides several advantages that extend beyond a traditional data warehouse:

- **Pay-as-you-go** pricing model: Only pay for the resources you use.
- **No infrastructure costs**: Fully managed service.
- More than just a **data warehouse**: Supports **data transformations**, building **data pipelines**, and creating **visual dashboards**.
- **High scalability**: Easily scale resources up or down as needed.
- **Data Recovery**: Supports backup, recovery, data sharing, and masking.
- **External File Analysis**: Analyze data from external files.
- **Easy Integration**: Seamlessly integrates with **data visualization** and **reporting tools**.

---

## Snowflake Architecture

### 1. Database Storage Layer:
The **storage layer** manages **table data** and **query results**. Key aspects of this layer include:

- Data is stored in **columnar format** using **micro-partitions**.
- **Snowflake manages** the organization, file size, compression, metadata, and other details.
- Data objects are only accessible via **SQL queries** and are not directly visible.
- **Cluster Keys** can be defined for large tables to optimize performance.

 ![Atchitecture Diagram](Snowflake Image.png)

### 2. Query Processing Layer:
The **processing unit** of Snowflake.

- Queries are executed through **virtual warehouses**, which consist of **compute nodes**.
- Virtual warehouses on AWS are groups of **EC2 instances**, while on Azure they are groups of **Virtual Machines**.
- The **compute cost** is based on the **query execution time** on virtual warehouses.
- Virtual warehouses are highly **scalable** and can be **auto-suspended** or **auto-resumed**.

### 3. Cloud Services Layer:
The **brain** of Snowflake, this layer coordinates services across the platform:

- **Authentication** and **access control**.
- **Infrastructure management**.
- **Metadata management**.
- **Security**.
- Manages serverless tasks like **Snowpipe**, **Tasks**, and **Materialized view maintenance**.

---

## Connecting to Snowflake

Snowflake supports multiple ways to connect:

- **Web-based User Interface**: Full management and usage of Snowflake via a web portal.
- **Command Line Clients (e.g., SnowSQL)**: Manage and use Snowflake through the command line.
- **ODBC and JDBC Drivers**: Connect Snowflake with third-party applications (e.g., Tableau).
- **Native Connectors**: Available in ETL tools like **DataStage** and **Informatica**.

---

## Micro-Partitions and Clustering

### Agenda:
- How data is stored in **micro-partitions**.
- Metadata of micro-partitions.
- Benefits of micro-partitions.
- **Clustering** and **Cluster keys**.
- How to define and choose **Cluster keys**.

### Micro-Partitions:
Snowflake uses a unique partitioning system called **micro-partitioning**. Key features include:

- Automatically applied to all Snowflake tables.
- Data is partitioned based on its order when inserted.
- Micro-partitions are **small in size** (50 to 500 MB) and **compressed**.
- Snowflake automatically selects the most efficient compression algorithm for each column in a micro-partition.

### Metadata of Micro-Partitions:
Snowflake maintains metadata for micro-partitions, including:

- The **number of distinct values** for each field.
- The **range of values** for each field.
- Other performance-enhancing information.

Metadata plays a key role in **query optimization** by enabling **query pruning**. Instead of scanning the entire dataset, Snowflake can scan only relevant micro-partitions, significantly improving query performance.



