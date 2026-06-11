# MovieLens 100K Data Pipeline using Apache Spark & Cassandra

<p align="center">
  <img width="1584" height="396" alt="Image" src="https://github.com/user-attachments/assets/072c5aa5-d032-4175-b942-96737dd97993" />
</p>

<p align="center">
  <a href="#overview">Overview</a> •
  <a href="#dataset">Dataset</a> •
  <a href="#workflow">Workflow</a> •
  <a href="#environment">Environment</a> •
  <a href="#implementation">Implementation</a> •
  <a href="#results">Results</a> •
  <a href="#validation">Validation</a> •
  <a href="#reproducibility">Reproducibility</a> •
  <a href="#author">Author</a>
</p>

> A distributed data processing project using Apache Spark and Apache Cassandra to analyse the MovieLens 100K dataset. This project demonstrates a complete data engineering workflow from data ingestion into HDFS, analytical querying with Spark SQL and storage in Cassandra.

---

# Overview

The objective is to build a Python-based data pipeline using Apache Spark and Cassandra to perform analytical queries on the MovieLens 100K dataset.

The project demonstrates:

```mermaid
flowchart LR

A[MovieLens Dataset]
--> B[Upload to HDFS]

B --> C[Create RDDs]

C --> D[Convert to DataFrames]

D --> E[Data Cleaning]

E --> F[Spark SQL Analytics]

F --> G[Write Results to Cassandra]

G --> H[Read Back from Cassandra]

```
### Notebook Structure

```yaml
movielens_analysis_spark_cassandra.json
│
├── 1. Environment Configuration
├── 2. Download MovieLens dataset 
├── 3. Load Data into HDFS
├── 4. Parse Raw Data into RDDs
├── 5. Transform RDDs into Spark DataFrames
├── 6. Data cleaning & preprocessing
│
├── 7. Analytical queries using Spark SQL
│   ├── Task 1
│   ├── Task 2
│   ├── Task 3
│   ├── Task 4
│   └── Task 5
│
└── 8. Write results to Cassandra
└── 9. Read back from Cassandra for validation
└── 10. Session Completion
```
---

# Dataset

### Source: [MovieLens 100K Dataset](https://grouplens.org/datasets/movielens/)↗️

### Files Used

| File | Description |
|--------|--------|
| u.data | User ratings data |
| u.user | User demographic information |
| u.item | Movie information and genres |

### Dataset Summary

| Dataset | Records |
|----------|----------|
| Ratings | 100003 |
| Users | 943 |
| Movies | 1682 |

---

# Implementation

## Step 1: Load Dataset into HDFS

The MovieLens dataset files were uploaded into HDFS before processing.

### Screenshot

Insert screenshot of:

```bash
hdfs dfs -ls /movielens
```

File:

```text
screenshots/hdfs_files.png
```

---

## Step 2: Create RDD Objects

The raw text files were loaded into Spark and converted into RDDs.

RDDs created:

- ratings_rdd
- users_rdd
- movies_rdd

Example:

```python
ratings_rdd = sc.textFile("/movielens/u.data")
users_rdd = sc.textFile("/movielens/u.user")
movies_rdd = sc.textFile("/movielens/u.item")
```

---

## Step 3: Transform RDDs into DataFrames

RDDs were converted into Spark DataFrames using predefined schemas to enable SQL-based processing.

### Screenshot

Insert screenshot showing:

```python
ratings_df.printSchema()
users_df.printSchema()
movies_df.printSchema()
```

File:

```text
screenshots/schema.png
```

---

## Step 4: Data Cleaning and Preprocessing

The following preprocessing steps were performed:

- Schema validation
- Data type conversion
- Null value checking
- Duplicate record checking
- Column selection and formatting

These steps ensured the dataset was ready for analytical processing.

---

## Step 5: Analytical Queries Using Spark SQL

The following analytical tasks were completed:

1. Calculate average rating for each movie
2. Identify top 10 highest rated movies
3. Determine favourite genre of users who rated at least 50 movies
4. Find users under 20 years old
5. Find scientists aged between 30 and 40 years old

---

## Step 6: Cassandra Integration

A Cassandra keyspace named `movielens` was created.

Results were stored in the following tables:

| Table |
|---------|
| avg_movie_ratings |
| top10_movies |
| user_fav_genre |
| users_under20 |
| scientists_30_40 |

### Screenshot

Insert screenshot showing:

```sql
DESCRIBE KEYSPACE movielens;
```

File:

```text
screenshots/cassandra_schema.png
```

---

# Results

## Task 1: Average Rating for Each Movie

The average rating and total number of ratings were calculated for every movie in the dataset.

### Screenshot

Insert screenshot:

```text
screenshots/task1_avg_rating.png
```

### Discussion

Average ratings were successfully calculated for all movies in the dataset.

Movies with a larger number of ratings provide a more reliable measure of audience preference. In contrast, movies with only a small number of ratings may exhibit extreme average scores that are less representative of overall user opinion.

---

## Task 2: Top 10 Movies with Highest Average Ratings

The ten highest-rated movies were identified based on average rating.

### Screenshot

Insert screenshot:

```text
screenshots/task2_top10_movies.png
```

### Discussion

Several movies achieved a perfect average rating of 5.0.

However, inspection of the results shows that most of these movies received only one to three ratings. This suggests that ranking movies solely by average rating can be misleading because a small sample size may inflate the average score.

A more robust ranking approach would consider both average rating and number of ratings received.

---

## Task 3: Favourite Genre of Users Who Rated at Least 50 Movies

Users with at least 50 ratings were identified and their favourite genre was determined based on the genre they rated most frequently.

### Screenshot

Insert screenshot:

```text
screenshots/task3_fav_genre.png
```

### Discussion

The analysis revealed the most frequently rated genres among highly active users.

Genres such as Drama, Comedy, and Action appeared prominently, indicating stronger user engagement with mainstream movie categories.

This task demonstrates how user activity data can be combined with movie metadata to derive behavioural insights.

---

## Task 4: Users Under 20 Years Old

Users younger than 20 years old were extracted from the dataset.

### Screenshot

Insert screenshot:

```text
screenshots/task4_users_under20.png
```

### Discussion

A significant proportion of users under 20 were identified.

Many belonged to the student occupation category, suggesting that younger users formed an important segment of the MovieLens user base.

This query demonstrates demographic filtering capabilities using Spark SQL.

---

## Task 5: Scientists Aged Between 30 and 40 Years Old

Users whose occupation was scientist and whose age was between 30 and 40 years old were identified.

### Screenshot

Insert screenshot:

```text
screenshots/task5_scientists.png
```

### Discussion

Only a small subset of users satisfied both occupation and age requirements.

The result illustrates how Spark SQL can efficiently perform multi-condition filtering on large datasets.

Such demographic segmentation is commonly used in recommendation systems and user profiling applications.

---

# Validation

After writing the processed DataFrames into Cassandra, all tables were read back into Spark DataFrames.

This step ensured that:

- Data was successfully stored in Cassandra
- No records were lost during transfer
- Retrieved results matched the original outputs

### Screenshot

Insert screenshot showing:

```python
spark.read \
.format("org.apache.spark.sql.cassandra") \
.options(table="top10_movies", keyspace="movielens") \
.load() \
.show()
```

File:

```text
screenshots/cassandra_validation.png
```

---

# Key Findings

1. Apache Spark successfully processed the MovieLens 100K dataset using distributed computing techniques.

2. Average ratings were calculated for all movies and stored in Cassandra.

3. Several movies achieved perfect ratings, but most had very few ratings, highlighting the importance of considering rating counts when ranking movies.

4. User behaviour analysis revealed popular movie genres among active users.

5. Demographic filtering successfully identified young users and scientists within a specified age range.

6. Cassandra effectively served as a storage layer for processed analytical results.

7. Validation confirmed successful integration between Spark and Cassandra.

---

# Reproducibility

## Development Environment

This project was developed and tested using the following environment:

| Component | Version |
|------------|------------|
| Apache Zeppelin | 0.7.3 |
| Apache Spark | 2.3.1 |
| PySpark | 2.3.1 |
| Apache Cassandra | 3.11.17 |
| CQLSH | 5.0.1 |
| Hadoop (HDFS) | HDP Sandbox |
| Python | 2.7.5 |

---

## Running the Project

1. Ensure HDP Sandbox is running.
2. Open Apache Zeppelin:
   http://localhost:9995
3. Apache Cassandra is running:
  ```bash
  pgrep -a java | grep cassandra
```
4. Spark interpreter in Zeppelin configured with:
```bash
spark.jars.packages = com.datastax.spark:spark-cassandra-connector_2.11:2.3.0
spark.cassandra.connection.host = 127.0.0.1
spark.cassandra.connection.port	= 9042
```
5. Import the notebook file:

```text
movielens_analysis_spark_cassandra.json
```

6. Execute the notebook paragraphs sequentially from top to bottom.

---

> [!NOTE]
> 1. All outputs presented in this repository were generated directly from the provided Zeppelin notebook.
> 2. Zeppelin was selected as the development environment because it provides native integration with Apache Spark which allow Spark jobs to be executed directly within interactive notebook paragraphs.
> 3. This notebook also supports built-in visualisation of query results which improves interpretability and reduces the need for external plotting tools.

---

<br>

## Author
* **Name:** Wan Ainin Sofiya binti Wan Mustafa
* **Matric No:** P160638


