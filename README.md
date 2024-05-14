# Pollux Chain SR Node Setup
Welcome to the setup guide for the Super Representative (SR) node on the Pollux Chain, This document provides detailed instructions on how to configure and run an SR node, essential for participating in the consensus and governance of the Pollux Chain.

## Whats Pollux?
- Pollux is a project dedicated to building the infrastructure for a truly decentralized Internet.

- Pollux Protocol, one of the largest blockchain-based operating systems in the world, offers scalable, high-availability, and high-throughput support that underlies all the decentralized applications in the Pollux ecosystem.

- Pollux Virtual Machine (PVM) allows anyone to develop decentralized applications (DAPPs) for themselves or their communities with smart contracts, thereby making decentralized crowdfunding and token issuance easier than ever.

- Pollux enables large-scale development and engagement. With over 10000 transactions per second (TPS), high concurrency, low latency, and massive data transmission, it is ideal for building decentralized entertainment applications. Free features and incentive systems allow developers to create premium app experiences for users.

# Prerequisites

Before you begin, ensure you have the following:
Minimum:
- CPU with 8 cores
- 16GB RAM
- 500GB free storage 


Recommended:

- CPU with 16+ cores(32+ cores for a super representative)
- 32GB+ RAM(64GB+ for a super representative)
- High Performance SSD with at least 2.5TB free space
- 100+ MB/s download Internet service

## Running a super representative node for mainnet

Adding the `--witness` parameter to the startup command, full node will run as a super representative node. The super representative node supports all the functions of the full node and also supports block production. Before running, make sure you have a super representative account and get votes from others. Once the number of obtained votes ranks in the top 27, your super representative node will participate in block production.

Fill in the private key of a super representative address into the `localwitness` list in the `supernode.conf`. Here is an example:
Fill the external IP that is your public IP of the Machine
```
 localwitness = [
    <your_private_key>
 ]
```

```
  external.ip = <place your external ip>

```

then run the following command to start the node:

```bash
$ nohup java -Xms9G -Xmx9G -XX:ReservedCodeCacheSize=256m \
             -XX:MetaspaceSize=256m -XX:MaxMetaspaceSize=512m \
             -XX:MaxDirectMemorySize=1G -XX:+PrintGCDetails \
             -XX:+PrintGCDateStamps  -Xloggc:gc.log \
             -XX:+UseConcMarkSweepGC -XX:NewRatio=2 \
             -XX:+CMSScavengeBeforeRemark -XX:+ParallelRefProcEnabled \
             -XX:+HeapDumpOnOutOfMemoryError \
             -XX:+UseCMSInitiatingOccupancyOnly  -XX:CMSInitiatingOccupancyFraction=70 \
             -jar FullNode.jar --witness -c supernode.conf >> start.log 2>&1 &
```


# License

java-pollux is released under the [LGPLv3 license].
