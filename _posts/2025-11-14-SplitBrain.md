---
layout: post
title:  "The Split Brain Problem"
subtitle: "Understanding and Preventing Data Inconsistencies"
date:   2025-11-14
categories: distributed-systems consistency
---

# What is the Split Brain Problem
Suppose you have a primary server that handles your requests and a failover backup server. The primary server sends regular heartbeats to the backup server over the network to indicate that it is healthy. As long as the backup server receives these heartbeats it will keep forwarding any requests it gets to the primary. When the primary stops sending heartbeats, the backup assumes that the primary is down and takes over as the new primary.

But what happens when the primary is still healthy but the network over which the heartbeats are sent is down. The backup now thinks that the primary is down and assumes the role of primary. This leads to inconsistencies as both servers are now acting and serving requests as the primary. This problem is commonly known as the Split Brain Problem.

<div style="text-align: center;">
  <img src="/assets/images/SplitBrain/Primary_Backup.png" alt="Three scenarios" width="500">
  <p style="font-style: italic; font-size: 0.9em;">Figure 1: Three scenarios — 1. Healthy Primary, 2. Primary down, 3. Network partition</p>
</div>



# Consequences of a Split Brain
Split brain can lead to situations with two versions of the truth. Consider a bank that has two servers storing the balance of an account. Suppose a network partition occurs and the backup assumes primary with the real primary still handling requests. The primary gets a request updating Account A’s balance to 120. The backup gets a request updating the same Account A’s balance to 80. Two different versions of the truth have now emerged. There are several algorithms that aim to resolve such inconsistences (version vectors, LWW, CRDT) but there are some domains where such methods fail. In systems that have a single leader (for example systems that implement the Raft protocol), each partition might end up electing it’s own leader. This again leads to the duplicate writes issue, where two separate servers handle write operations leading to two different versions of the truth.

# Preventing Split Brain
VMWare’s FT solves this problem using a distributed lock. A file server exists common to both the primary and the backup server. When the primary is up, it will test and set the lock. Along with this, it sends continuous heartbeats to the backup server. When the backup server stops receiving heartbeats, it will test the lock. If the lock is set then the primary is still up and there is only a network partition. If the lock returns false the backup will set the lock and assume role as the primary. The use of a common file server leads to a single point of failure. It also fails to handle slow nodes or nodes that have partially crashed. These are also called Byzantine nodes.

Consensus algorithms like Raft and Paxos, prevent the split brain problem by having a majority of the nodes acknowledge every action. In Raft, for example, the leader can only commit an entry to it’s log if a majority of the nodes in the cluster have add the entry. It also requires a majority of votes to be elected as leader. If a partition does not have a majority then it will halt and retry later. This prevents multiple leaders from forming. There are several other methods to prevent split brain, STONITH (shoot the other node in the head) and disabling writes on the minority partition are two other methods commonly used.
