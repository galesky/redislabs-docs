---
Title: Shard Placement Policy
description:
weight: $weight
alwaysopen: false
categories: ["RS"]
aliases: /rs/concepts/rebalancing-shard-placement/
---
{{< embed-md "shard-placement-intro.md"  >}}

## Shard Placement Policies

### Dense Shard Placement Policy

In the dense policy, the cluster places the database shards on as few nodes as possible.
When the node is not able to host all of the shards, some shards are moved to another node to maintain optimal node health.

For example, for a database with two master and two slave shards on a cluster with three nodes and a dense shard placement policy,
the two master shards are hosted on one node and the two slave shards are hosted on another node.

The dense policy helps to use less system resources and proxies for access to the database.

![dense_placement_1-1](/images/rs/dense_placement_1-1.png)

*Figure: Three nodes with two master shards (red) and two slave shards (grey) with a dense placement policy*

### Sparse Shard Placement Policy

In the sparse policy, the cluster places shards on as many nodes as possible to distribute the shards of a database across all available nodes.
When all nodes have database shards, the shards are distributed evenly across the nodes to maintain optimal node health.

For example, for a database with two master and two slave shards on a cluster with three nodes and a sparse shard placement policy:

- Node 1 hosts one of the master shards
- Node 2 hosts the slave for the first master shard
- Node 3 hosts the second master shard
- Node 1 hosts for the slave shard for master shard 2

The dense policy helps to use fewer system resources.

![sparse_placement_1-1](/images/rs/sparse_placement_1-1.png)

*Figure: Three nodes with two master shards (red) and two slave shards (grey) with a sparse placement policy*