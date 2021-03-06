# Apache Airflow 2.0 Guide
### Python Virtual Environment Setup and Initialization
**Install python3 on OSX**
```shell
brew install python3
```

**Create and activate Python virtual environment**
```shell
python3 -m venv airflowsandbox
source airflowsandbox/bin/activate
```

```bash
# Assumes Python 3.8.5 installed
# Assumes python3-pip 20.2.4
pip install wheel
pip install apache-airflow==2.0.0 --constraint https://gist.githubusercontent.com/cjtravis/8c9c136e3cd20e513c9c253a7275f8fc/raw/5da51f9fe99266562723fdfb3e11d3b6ac727711/constraint.txt
```

**Initialize database**

Default metadata database is local SQLite database. Postgres or MySQL can be configured by modifying `airflow.cfg` file.
```shell
export AIRFLOW_HOME=~/git/cjtravis/airflow/airflow
airflow db init
```

This will populate `~/git/cjtravis/airflow/airflow` with airflow configuration files.

**Create Airflow Admin User**
```shell
airflow users create \
    --username admin \
    --firstname CJ \
    --lastname Travis \
    --role Admin \
    --email cj@cjtravis.com \
    --password airflow
```

### Starting Airflow Services
**Webserver**
```shell
airflow webserver 

```
The webserver should be accessible at [http://localhost:8080](http://localhost:8080).

**Scheduler**
```shell
airflow scheduler
```

### DAGs
**Create `dags` directory**
```shell
mkdir AIRFLOW_HOME/dags
```
