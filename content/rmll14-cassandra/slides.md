# Legacy application
## from
# JDBC
## to
# Cassandra

%%%

# Me

## Matthieu Baechler
## [@m_baechler](http://twitter.com/m_baechler)
## [github/mbaechler](https://github.com/mbaechler)


## Long time developper/architect
## (Paid) Free software for nearly 4 years at Linagora

%%%

# Linagora

<img class="stretch" src="./img/13talks.png"/>


## Develop OBM, a free software 
## alternative to MS Exchange et al.


## Very eager to adopt new technologies

%%%

# NoSQL in 5 minutes


## NoSQL features


## small fraction of what SQL do


## ~~Transaction~~


## ~~consistency~~


## ~~complex queries~~


## ~~JOIN~~


## ~~standard~~


# Going NoSQL costs
# **a lot**


## change of datamodel


## more responsibility on application side


## duplication management


## customer education


# The single feature
## that makes 
# **NoSQL**
## relevant :
# scalability

%%%

# Still interested ?


# Discover **Cassandra**


## On-demand consistency level


## Every-nodes are (almost) equals


## Very fast for write loads

%%%

# Live coding ?


## Some context first


# Opush
## My legacy application


## libre MS-EAS  implementation
## started in early 2009
## 5 years old


## part of OBM
## 14 years old


# Technologies :
- SQL
- OBM XML over HTTP services
- Cyrus Imap
- Servlets
- ...


# Scalability needs

## from
# 100 users 
## to 
# 500K users


# **x 5000**

%%%

# Let's code


## JDBC code 
## with a tiny test-suite running on H2


## discover CQLSH
## (using docker)


## replace JDBC code with some Cassandra


# So easy


But you are not looking for a single-node server, do you ?

%%%

# Eventual consistency is hard


## Where are my data


## Which node ?


# Eventually working application ?


# consistency level
## comes to the rescue


# ONE
- partition tolerant
- better latency
- weak consistency


# QUORUM
- weaker partition tolerancy
- longer latency
- strong consistency


# ALL
- not partition tolerant
- bad performances
- it makes conservatives people happy


## QUORUM is a very good start


## **ONE** can be used with some specitific data


## immutable data helps a lot


## TDD probably won't help

%%%

# Production


I expected to encouter issues by the time I come to RMLL


But in fact I didn't got much


# Authentication


Authentication tables must be replicated


Created by Cassandra


With replication factor = 1


Not replicated


A single login/password lives on a single node


Authentication fails if this node is down


# Replication factor is important


RP = 2 is not very useful if you use QUORUM


# Monitoring
- read latency
- write latency
- read count
- write count


## Main problem in real life ?


## Getting the right hardware


- local disks
- two disks per node (commitlog + data)	
- SSDs
- lot of RAM
- 2 Gb Ethernet interfaces / 2 networks

%%%

# Thank you !

- [@m_baechler](http://twitter.com/m_baechler)
- [http://github.com/mbaechler/rmll14-cassandra](http://github.com/mbaechler/rmll14-cassandra)
- [Slides](http://mbaechler.github.io/slides/content/rmll14-cassandra/)
- [Linagora](http://linagora.com)
