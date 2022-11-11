# Cassandar-DB

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
Restart your nodes.
