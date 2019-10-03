# pgpool2-docker-compose-sample
docker-compose.yml sample for easy change parameter in .env file
docker images using with bitnami/postgresql:11.1.0 and melvinkcx/rds_pgpool:0.2.6
# How to first startup 
  1. docker-compose up -d master and wait to init database finished. Can check with docker logs -f ${MASTER_NAME}
  2. docker-compose up -d slave and wait to database replicated. Can check with docker logs -f ${SLAVE_NAME}
  3. docker-compose up -d pgpool2_master 
  4. application can connect with ${PGPOOL2_MASTER_PORT_CLIENT}
  # Diagram
```
+-------------+
|             |
|  MASTER     +--------------+
|             |              ^
+-------------+       +------+---------+            +-----------------+
                      |                |            |                 |
                      |  PGPOOL2       +-<--------->+  APPLICATION    |
                      |                |            |                 |
                      +------+---------+            +-----------------+
+-------------+              ^
|             |              |
|  SLAVE      +--------------+
|             |
+-------------+
```
