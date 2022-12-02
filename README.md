# Cassandar-DB

Cassandra logs ,config and data file path resp:

```bash
cd /var/log/cassandra
cd /etc/cassandra
cd /var/lib/cassandra/

```

How to Truncate cassandra DB
```bash
cqlsh
USE thingsboard;
TRUNCATE thingsboard.ts_kv_partitions_cf;
TRUNCATE thingsboard.ts_kv_cf;
```

How to take backup from Truncate snapshot of cassandra DB
```bash
cd /var/lib/docker/volumes/minikube/_data/hostpath-provisioner/thingsboard/cassandra-data-cassandra-0/data/thingsboard/ts_kv_cf-53b137c05f3211ed9d54b565838241ff
```
```bash
cp -RT snapshots/truncated-1668177628209-ts_kv_cf/ .
```
```bash
 nodetool refresh 
```
```bash
kubectl scale statefulset/cassandra --replicas=0
```
```bash
kubectl scale statefulset/cassandra --replicas=1
```
Restart your nodes.

Cassandra Status
```bash
nodetool status
or
nodetool -h ::FFFF:127.0.0.1 status
nodetool -h ::FFFF:127.0.0.1 tablestats
```

Delete data from volume]
```bash
cd /var/lib/docker/volumes/minikube/_data/hostpath-provisioner/thingsboard/cassandra-data-cassandra-1/data/thingsboard/ts_kv_cf-53b137c05f3211ed9d54b565838241ff

```
```bash
truncate -s 0 *

```
Check Size of table 
```bash
nodetool cfstats -- <keyspace>.<table>
```
How-to check database size and desired capacity

To find out free space:
```bash
du -h
```
To find out DB size

1. PostgreSQL
```bash
sudo -u postgres psql -c "SELECT pg_size_pretty( pg_database_size('dbname') );"
```
2. Cassandra
```bash
du -h /var/lib/cassandra/ | tail -1
```

