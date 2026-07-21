# High Availability Apache Hadoop Cluster

![Apache Hadoop](https://img.shields.io/badge/Apache-Hadoop-yellow?logo=apache)
![HDFS](https://img.shields.io/badge/HDFS-High%20Availability-blue)
![Ubuntu](https://img.shields.io/badge/Ubuntu-22.04-E95420?logo=ubuntu)
![Linux](https://img.shields.io/badge/Linux-Ubuntu-success?logo=linux)
![Replication](https://img.shields.io/badge/Replication-3-brightgreen)
![Status](https://img.shields.io/badge/Cluster-Healthy-success)

---

## Overview
This project demonstrates the implementation of a production-style High Availability Apache Hadoop Distributed File System (HDFS) Cluster using five Ubuntu virtual machines.

The cluster eliminates the single point of failure by deploying Active/Standby NameNodes coordinated through ZooKeeper and JournalNodes while DataNodes provide distributed block storage with a replication factor of three.

The project validates:

- High Availability (HA)
- Automatic Failover
- Shared Edit Logs
- HDFS Block Replication
- Fault Tolerance
- Cluster Health Verification
---

## Architecture
![Architecture](architecture/cluster-architecture.png)
---

## Infrastructure
| Component | Count |
|-----------|------:|
| Ubuntu Virtual Machines | 5 |
| NameNodes | 2 |
| ZooKeeper Nodes | 3 |
| JournalNodes | 3 |
| DataNodes | 3 |
## Cluster Topology
| Hostname | Role |
|-----------|------------------------------|
| node01 | Active NameNode |
| node02 | Standby NameNode |
| node03 | ZooKeeper + JournalNode + DataNode |
| node04 | ZooKeeper + JournalNode + DataNode |
| node05 | ZooKeeper + JournalNode + DataNode |

## Cluster Architecture
The cluster consists of two NameNodes configured in an Active/Standby architecture.

ZooKeeper continuously monitors both NameNodes and performs automatic failover when the active node becomes unavailable.

JournalNodes maintain shared edit logs ensuring both NameNodes always have synchronized metadata.

DataNodes provide distributed block storage with a replication factor of three to guarantee data durability.
## Technologies Used
- Apache Hadoop
- HDFS
- ZooKeeper
- JournalNodes
- Ubuntu Linux
- Java
- SSH
- Bash

  ## Configuration
  | Property | Value |
|-----------|-------|
| Cluster Name | mycluster |
| Replication Factor | 3 |
| Active NameNode | node01 |
| Standby NameNode | node02 |
| ZooKeeper Quorum | node03 node04 node05 |
| JournalNodes | 3 |
| DataNodes | 3 |

## Validation
```bash
hdfs haadmin -getServiceState nn1

```
Active
Standby
```bash
hdfs dfsadmin -report
```
3 Live DataNodes
Replication = 3
Healthy Cluster

```bash
hdfs fsck /test/test.txt -files -blocks -locations
```
Status : HEALTHY

Live_repl = 3

Replication Factor = 3

## Screenshots

### Cluster Architecture

![Architecture](architecture/cluster-architecture.png)

---

### Upload Workflow

![Upload](architecture/upload-workflow.png)

---

### Automatic Failover

![Failover](architecture/failover-process.png)

---

### Block Replication

![Replication](architecture/block-replication.png)

## Features
- High Availability HDFS
- Active / Standby NameNodes
- ZooKeeper Coordination
- Automatic Failover
- Shared Edit Logs
- JournalNodes
- Block Replication
- Fault Tolerance
- Distributed Storage

## Project Validation
 Active / Standby verified

 Automatic Failover configured

 ZooKeeper Quorum operational

 JournalNodes synchronized

 Three DataNodes online

 Replication Factor = 3

 Healthy File System

 FSCK passed

 ## Future Improvements
 - Apache Spark

- Apache Hive

- Apache HBase

- Kerberos Authentication

- Grafana Monitoring

- Prometheus

- Docker Deployment

- Kubernetes

## License
MIT License
ر
