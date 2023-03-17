# Synapse

check comments in docker-compose.yml for how to deploy.

## Prepare the homeserver.yaml file

```bash
docker run --rm -it -v /synapse/data:/data -e SYNAPSE_SERVER_NAME=matrix.example.com -e SYNAPSE_REPORT_STATS=no docker.io/matrixdotorg/synapse:latest generate
```

## Prepare the database
modify the database config in the homserver.yaml file as below
```yaml
database:
  name: psycopg2
  args:
    user: synapse
    password: synapse_pg_password
    database: synapse
    host: postgres
    cp_min: 5
    cp_max: 10
```
## Create user

```bash    
docker exec -it synapse_synapse_1[synapse container name] /bin/bash
register_new_matrix_user -c /data/homeserver.yaml http://localhost:8008
```