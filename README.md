# assignment2.2
Ans 1):
-------------------HDFS --------------
HDFS is a distributed file system that provides high-performance access to data across Hadoop clusters.
HDFS is a key tool for managing pools of big data and supporting big data analytics applications.
HDFS typically is deployed on low-cost commodity hardware, server failures are common. 

The file system is designed to be highly fault-tolerant, however, by having transferred of data between compute nodes and enabling Hadoop systems to continue running if a node fails.
When HDFS takes in data, it breaks the information down into separate pieces and distributes them to different nodes in a cluster, allowing for parallel processing. 
The file system also copies each piece of data multiple times and distributes the copies to individual nodes, placing at least one copy on a different server rack than the others. 
hence the data on nodes that crash can be found elsewhere within a cluster, which allows processing to continue while the failure is resolved.
HDFS is built to support applications with large data sets, including individual files that reach into the terabytes.

It uses a master/slave architecture, with each cluster consisting of a single NameNode that manages file system operations and supporting DataNodes that manage data storage.
The architecture of hadoop is attached in a file(assign2.2.1), where we can see master /slave structure , rack arragment and how replication is done to avoid losses after failure.
  HDFS FEATURES:-
  1.Very large files: Files that has size i gigabytes, terabytes, or petabytes.
  2.Streaming data access: HDFS is built around the idea that data is written once but
                           read many times
  3.Commodity hardware: Hadoop does not require expensive, highly reliable hardware.

Ans2) :
-----Hadoop Cluster----- 
     Normally any set of loosely connected or tightly connected computers that work together as a single system is called Cluster. 
     In simple words, a computer cluster used for Hadoop is called Hadoop Cluster. 
Hadoop cluster is a special type of computational cluster designed for storing and analyzing vast amount of unstructured data in a distributed computing environment. 
These clusters run on low cost commodity computers. 
Hadoop clusters are often referred to as "shared nothing" systems because the only thing that is shared between nodes is the network that connects them. 
Large Hadoop Clusters are arranged in several racks. Network traffic between different nodes in the same rack is much more desirable than network traffic across the racks. 
refer attachment(assig2.2.2)
Hadoop cluster has 3 components:
1- Client
2- Master
3- Slave
*Client: It is neither master nor slave, rather play a role of loading the data into cluster, submit MapReduce jobs describing how the data should be processed,
and then retrieve the data to see the response after job completion. 

*Masters:The Masters consists of 3 components NameNode, Secondary Node name and JobTracker. 
1- NameNode(DN) - Contains the Hadoop FileSystem Tree and other metadata information about files and directories.
              Contains in-memory mapping of which blocks are stored in which datanode.
2- JobTracker(TT) -Controls the overall execution of the MapReduce jobs
3.Data node (DD) - Stores actual data blocks of files in HDFS on its own local disk.
4. Secondary Name Node- Performs house-keeping activities for NameNodes, like the periodic merging of namespace and edits. 

Slaves: Slave nodes are the majority of machines in Hadoop Cluster and are responsible to
1.Storage
2.Processing


Que.3)
----HDFS BLOCKS---
When you need to store a file in HDFS, the system breaks it down into a set of individual blocks and stores these blocks in various slave nodes in the Hadoop cluster. 
This is an entirely normal thing to do, as all file systems break files down into blocks before storing them to disk.

HDFS is often blissfully unaware that the final record in one block may be only a partial record, with the rest of its content shunted off to the following block.
HDFS only wants to make sure that files are split into evenly sized blocks that match the predefined block size for the Hadoop instance . 
In the preceding figure, that block size is 128MB.

The concept of storing a file as a collection of blocks is entirely consistent with how file systems normally work. But what’s different about HDFS is the scale.
A typical block size that you’d see in a file system under Linux is 4KB, whereas a typical block size in Hadoop is 128MB. 
This value is configurable, and it can be customized, as both a new system default and a custom value for individual files.
First of all, every data block stored in HDFS has its own metadata and needs to be tracked by a central server so that applications needing to access a specific file can be directed to wherever all the file’s blocks are stored. 
If the block size were in the kilobyte range, even modest volumes of data in the terabyte scale would overwhelm the metadata server with too many blocks to track.
Second, HDFS is designed to enable high throughput so that the parallel processing of these large data sets happens as quickly as possible. The key to Hadoop’s scalability on the data processing side is, 
and always will be, parallelism — the ability to process the individual blocks of these large files in parallel.

The continuos allocation hepls to achieve less seek time. 
The attached file (assign2.2.3) help us understand how allocation is done. 
the sector will store and collection of sector is sector clusture , the tracks on hard disk will point the position.





