# Overview

This project contains my custom ETL pipeline built with Apache Airflow. The goal is to demonstrate how Airflow can be used to manage and automate workflows locally using Docker. This readme explains the project structure and how to run it on your machine.

# Project Contents

The project includes the following files and folders:

* **dags**: Contains all Airflow DAGs. By default, it includes an example ETL DAG:

  * `etl_weather.py`: A simple pipeline that extracts data from an external API, transforms it, and loads it for further use. It uses the TaskFlow API for clean Python-based task definitions and applies dynamic task mapping for flexibility.
* **Dockerfile**: Defines the runtime environment for Airflow with a versioned Docker image. Custom runtime commands and overrides can be added here.
* **include**: For any extra files required by the project.
* **packages.txt**: For installing system-level dependencies.
* **requirements.txt**: For Python dependencies.
* **plugins**: For adding custom or community plugins.
* **airflow\_settings.yaml**: A local-only configuration file for setting Airflow Connections, Variables, and Pools without using the UI.

# Running Airflow Locally

1. Start Airflow:

   ```bash
   astro dev start
   ```

   This will create 4 Docker containers:

   * **Postgres**: Metadata database
   * **Webserver**: Runs the Airflow UI
   * **Scheduler**: Monitors and triggers tasks
   * **Triggerer**: Handles deferred tasks

2. Check that the containers are running:

   ```bash
   docker ps
   ```

3. Access the Airflow UI at [http://localhost:8080](http://localhost:8080) using:

   * Username: `admin`
   * Password: `admin`

   The Postgres database is also available at `localhost:5432/postgres`.

# Next Steps

* Add your own ETL workflows to the `dags` folder.
* Extend `requirements.txt` and `packages.txt` with your dependencies.
* Use `airflow_settings.yaml` to preconfigure Airflow connections and variables.

# Contact

This project was built and is maintained by me as part of my learning and work on Airflow pipelines.

