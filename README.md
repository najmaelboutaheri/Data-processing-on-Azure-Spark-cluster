# Azure Spark Cluster for Big Data Processing  

This project processes and visualizes visa-related data in Japan using Apache Spark. It leverages distributed computing for data processing and generates insightful visualizations for analysis.


## Project Architecture  

The system processes input data using Apache Spark and outputs results in various formats like visualizations, logs, and files. The Spark cluster is deployed on Azure, leveraging its scalability and reliability.  

### Architecture Overview  

- **Input:**  
  Data sources processed using Spark, Python, and Spark SQL.  
- **Spark Cluster:**  
  A master node orchestrates multiple worker nodes for parallel processing.  
  Hosted on Azure for scalability and high availability.  
- **Output:**  
  Results are exported as visualizations, logs, or files.  

![Flowchart (2)](https://github.com/user-attachments/assets/f1957e49-2f8c-430a-965a-2147874023d1)

## Repository Structure  

### Project Structure  

```plaintext
├── myenv/                    # Python virtual environment
├── src/                      
│   └── input/                # Input data directory
│       └── visa_number_in_japan.csv
├── jobs/                     
│   └── visualisation.py      # Script for generating visualizations
├── output/                   # Output files
│   ├── visa_number_in_japan_cleaned.csv
│   ├── visa_number_in_japan_continent_2006_2017.html
│   ├── visa_number_in_japan_country_2017.html
│   ├── visa_number_in_japan_year_map.html
├── docker-compose.yml        # Docker Compose configuration
├── Dockerfile.spark          # Dockerfile for Spark
├── requirements.txt          # Python dependencies
├── download_files.sh         # Script to download input files
├── upload_files.sh           # Script to upload files to Spark cluster
├── spark-clusters_key.pem    # SSH key for Spark cluster
```

## Features  

- **Data Cleaning:** Processes raw CSV data into a cleaned format (visa_number_in_japan_cleaned.csv).
- **Visualization:** Generates HTML files for continent, country, and year-wise visa data visualizations.
- **Scalable Spark Setup:** Uses Docker for Spark cluster deployment and distributed processing.
- **Automated Workflows:** Includes bash scripts for file management (download_files.sh, upload_files.sh).

## Steps to follow:  

1. **Azure Subscription:** Make sure you have an active subscription ([Sign up](https://azure.microsoft.com/en-us/free/)).
2.  **Cluster Setup:**  
   - A Spark cluster deployed on Azure (using Azure Virtual Machines).
     
     <img width="514" alt="image" src="https://github.com/user-attachments/assets/eaa8bc1b-f096-45b7-8bb4-a063e903101c">

**STEP 1: Tools Installed after connecting to the virtual machine using .PEM key file :**  

   - [Apache Spark](https://spark.apache.org/downloads.html)  
   - [Docker](https://www.docker.com/)
   - [Docker Compose](https://docs.docker.com/engine/install/ubuntu/)
     
**STEP 2: Set Up the Python Environment:** (using Ubuntu terminal)

   ```bash
python3 -m venv myenv
source myenv/bin/activate 
pip install -r requirements.txt
```

**STEP 3: Run Docker Compose:**

 ```docker compose up -d```
 
This the result

<img width="433" alt="azure3" src="https://github.com/user-attachments/assets/ccdd90d6-ca25-45e6-a4a8-89622ebe110a">

list containers within Docker:

<img width="937" alt="azure2" src="https://github.com/user-attachments/assets/36ce41e0-647a-486b-8bb6-ab9d9749238a">

**STEP 4: Upload Input Data to Spark Cluster:**

```/bin/bash upload_files.sh```

**STEP 5: Generate Visualizations:**

```
docker exec -i <worker_name> python jobs/visualisation.py
```

You can try the following command also:

<img width="935" alt="azure7" src="https://github.com/user-attachments/assets/a53a5c99-409e-4d5b-8fdb-f0b48cd11760">

**STEP 5: Connect to Spark web interface by this link: http://your-vm-ip-adress:9090/**

Explore running jobs:

 <img width="938" alt="azure4" src="https://github.com/user-attachments/assets/07bb1e3a-8db1-406c-ac77-286335e614d1">

## Usage

- **Input:** Place input files in the src/input directory.
- **Output:** Check the output folder for cleaned data and generated visualizations.

## Visualizations

- *visa_number_in_japan_continent_2006_2017.html:* Continent-wise visualization of visa data.
  
  <img width="958" alt="image" src="https://github.com/user-attachments/assets/9337de22-bf1d-47fd-a873-3b815b8bfaa6">

- *visa_number_in_japan_country_2017.html:* Top 10 countries with the most issued visa in 2017
  
  <img width="959" alt="image" src="https://github.com/user-attachments/assets/ceec311b-9ad4-4576-8887-a688ab680caa">

- *visa_number_in_japan_year_map.html:* Yearly trends in visa applications.
  
  <img width="956" alt="image" src="https://github.com/user-attachments/assets/3b78adc9-95de-4500-a73f-a493e1e8a58c">


## Future Enhancements

- Automate cluster setup and data processing with CI/CD pipelines.
- Add interactive dashboards using tools like Plotly or Dash.
- Incorporate machine learning models for predictive analysis.
  
## Contributing

Contributions are welcome! Please fork the repository and create a pull request with your changes.
