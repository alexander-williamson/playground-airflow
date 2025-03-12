# playground-airflow
This quickstart will spin up airflow and bring in the example Dag.
This docker compose creates:
- A `postgres` database with a volume (which will stick around after stopping)
- A `airflow-webserver` website that is connected to the database
- A `airflow-scheduler` scheduler that is connected to the database

1. Start it for the first time, you'll get failures but that's OK
```
docker-compose up -d
```

2. Initialise the database
```
docker-compose run airflow-webserver airflow db init
```

3. Create the admin user
```
docker-compose run airflow-webserver airflow users create --role Admin --username admin --email admin@example.com --firstname Admin --lastname User --password admin
```

4. Restart the stopped services (it's easier to restart it the first time otherwise you can use `docker-compose service <name> up`)
```
docker-compose down
docker-compose up
```

There is now a username `admin` with password `admin` for you to use.