# Data Catalog

**Dataset Name:** `data_jobs` Dataset.

**Description:** Structured dataset containing scraped job posting data enriched with NLP-based skill extraction and salary normalization.

---

## Table: `data_jobs`

| Column Name            | Data Type                    | Category     | Description |
|------------------------|-----------------------------|-------------|-------------|
| job_title              | STRING                      | Raw         | Full original job title as scraped from the job posting source. |
| job_title_short        | STRING                      | Calculated  | Standardized job title generated using a BERT-based 10-class classification model. |
| job_location           | STRING                      | Raw         | Location string exactly as shown in the job posting. |
| job_country            | STRING                      | Calculated  | Country extracted and standardized from job_location. |
| search_location        | STRING                      | Generated   | Location used by the bot to construct job search queries. |
| job_posted_date        | TIMESTAMP                   | Raw         | Date and time when the job posting was originally published. |
| job_schedule_type      | STRING                      | Raw         | Employment schedule type (Full-time, Part-time, Contractor, etc.). |
| job_work_from_home     | BOOLEAN                     | Parsed      | Indicates whether the job is remote (true / false). |
| job_no_degree_mention  | BOOLEAN                     | Parsed      | Indicates if the posting explicitly mentions that no degree is required. |
| job_health_insurance   | BOOLEAN                     | Parsed      | Indicates whether health insurance benefits are mentioned in the posting. |
| salary_rate            | STRING                      | Raw         | Specifies whether salary is listed as annual or hourly. |
| salary_year_avg        | FLOAT                       | Calculated  | Average yearly salary derived from salary ranges when available. |
| salary_hour_avg        | FLOAT                       | Calculated  | Average hourly salary derived using the same normalization logic. |
| company_name           | STRING                      | Raw         | Company name as listed in the job posting. |
| job_via                | STRING                      | Raw         | Platform where the job was posted (e.g., LinkedIn, Jobijoba). |
| job_skills             | ARRAY<STRING>               | Parsed List | List of relevant skills extracted from the job posting using PySpark NLP pipelines. |
| job_type_skills        | MAP<STRING, ARRAY<STRING>>  | Parsed Dict | Dictionary mapping skill categories (e.g., 'cloud', 'libraries') to corresponding skill sets. |
