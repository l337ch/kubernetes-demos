
# Demo of Postgres Pet Sets

Create a postgres pet set consisting of 3 postgres database servers.
Connect to each of the postgres servers and create a table and populate it with unique data.
CREATE DATABASE zonar_demo

  CREATE TABLE demo_table (
    did     integer,
    name    varchar(40)
    CONSTRAINT con1 CHECK (did > 100 AND name <> '')
  );
Connect to one of the postgres servers and view the data
Delete one of the nodes from the cluster that belongs to the chosen database servers
Watch for the postgres server to recover
Connect to the same postgres server as before by hostname
Show that the data still exists on the postgres database server
