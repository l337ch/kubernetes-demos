
# Demo of Postgres Pet Sets

## Create some Postgres servers using k8s Pet Sets
- Create a postgres pet set consisting of 3 postgres  servers or Pods.
```
kubectl create -f pet_sets/postgres/pg_pet_set.yaml
```
- Connect to each of the postgres servers and create a database with a table and populate it with unique data.
```
kubectl run -it --rm --image postgres pg-client --restart=Never /bin/sh
psql -h postgresdb-0.postgres -U postgres
CREATE TABLE demo_table0 (
    did     integer,
    name    varchar(40)
);
INSERT INTO demo_table0 VALUES ('1', 'test 0');
\q
psql -h postgresdb-1.postgres -U postgres
CREATE TABLE demo_table1 (
    did     integer,
    name    varchar(40)
);
INSERT INTO demo_table1 VALUES ('1', 'test 1');
\q
psql -h postgresdb-2.postgres -U postgres
CREATE TABLE demo_table2 (
    did     integer,
    name    varchar(40)
);
INSERT INTO demo_table2 VALUES ('1', 'test 2');
\q
```
## Simulate a cluster failure
- Reduce the cluster size to 1
```
gcloud container clusters resize gke-zonar-demo --size 1
```
- Watch for the postgres server to recover
- Connect to one of the relaunched  postgres server  hostname via the postgres Pod as before and show that the data still exists on the postgres instance
```
kubectl run -it --rm --image postgres pg-client --restart=Never /bin/sh
psql -h postgresdb-0.postgres -U postgres
\d
```
