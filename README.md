# My Synopsis


## Client
* Has Local Storage: which caches information locally
* Has Session Storage: which caches information for a specific session
* Local Storage doesn’t cache data in incognito mode
* Encoding Schemes
  * br
  * gzip : gives 9x compression
  * deflate
  * compress
  * identity"
* Base 64 encoding for uploading small images and binary data
* size of input packet is max 1500 bytes
* timeout is usually 10ms

## Between Client and Load Balancer

* CDN
* DNS
* latency expected is 10ms
* Latency is dependent on provider and the location user is in, speed in a village is different from office

## Load Balancer
* Network LB
  * Network load balancer is designed to handler million requests/ second.
* Software LB
* Virtual Ips
  * Keep Alived
* Master and Slave
* Redirection the basis of API
* Various balancing strategy
  * Least response time
  * least load
  * Sticky session
  * Round Robin
  * IP Hash based"
* TCP Load Balancer -> once connection established it is served
* HTTP Load Balancer ->connection can be terminated

## API Server
* Number of connections
* Blocking vs Non Blocking
* Rate Limiter
* Caching for quick response
* multiple services communicate in Message Formats:
  * Textual: XML, CSV, JSON
  * Binary: Thrift, Protocol Buffers, Avro"


## Process Queue/Broker
* If response time required is quick we use buffering queue else payloads can be batched for workers
* Kafka is an example
* Multiple queues dealing with multiple partitions
* Hot Partitions can occur

## Worker
* can either take input directly from API Server or can poll broker queue
* Here meat logic stays, multiple workers for different usage

## Cache
* Think of distributed cache such as redis
* zookeeper for concurrency issues
* Latency Numbers

| L1 Cache | L2 Cache    | RAM                    | 1GB/s Network           | SSD         | SATA Disk               |
|----------|-------------|------------------------|-------------------------|-------------|-------------------------|
| 0.5ns    | 7ns or 14xL1|100ns or 20xL2 or 200xL1|10 ms or 40xRAM or 10xSSD| 1ms or 4xRAM|30ms or 120xRAM or 30xSSD|

## Hot Data
* DB wil most accessed data
* data needs to be sharded
* Proxy redirection
* consistent hashing
* Data needs to purged from time to tim
* synchronous or async update of data between master and slave
* Types of DB
  * Column
    * cassandra (is Fault tolerant, wide column, master less, supports cross data center replication)
    * Hbase (has master slave replication)
  * Key Value
    * Couch DB
    * Rocks DB
  * Document
    * MongoDB (uses leader based replication)
  * Graph
    * Neo4j"


## Cold Data
* Long term cheap storage for analytical usage
* Object Store
* Glacier


## Monitoring/observability
* With each component there is a element to send metrics to a observability service/alerts
