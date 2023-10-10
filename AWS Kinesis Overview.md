- for application logs, metrics, IoT, clickstreams
- real-time big data
- streaming processing frameworks (Spark, NiFI, etc..)
- automated replicated into 3 AZs

##### Kinesis Streams:
low latency streaming ingest at scale

##### Kinesis Analytics:
perform real-time analytics on streams using SQL

##### Kinesis Firehose:
load streams into S3, Redshift, ElasticSearch & Splunk

##### Kinesis Video Streams:
streaming video in real-time

### Kinesis
Onboard a lot of data
Do analytics
Firehose to insert into Database or RedShift

#### Kinesis Streams Overview
- ordered Shards / Partition, producer, and consumer
- retention is for 24 hours by default but can go up to 1 years
- Ability to reprocess / replay data
- Multiple applications can consume the same stream (pub-sub architecture)
- Immutable
- upto 1MB size

#### Kinesis Data Streams - Capacity Modes:
- Provisioned mode:
	- You choose the number of shards provisioned, scale manually or using API.
	- Each shard gets 1MB/s in (or 1000 records per second)
	- Each shard gets 2MB/s out (classic or enhanced fan-out consumer)
	- You pay per shard provisioned per hour
- On-demand mode:
	- No need to provision or manage the capacity
	- Default capacity provisioned (4MB/s in or 4000 records per second)
	- Scales automatically based on observed throughput peak during the last 30 days
	- Pay per stream per hour & data in/out per GB

#### Kinesis Data Streams Limits to Know
- Producer:
	- 1MB/s or 1000 messages/s at write PER SHARD
	- "ProvisionedThroughputException" otherwise
- Consumer Classic:
	- 2MB/s at read PER SHARD across all consumers
	- 5 API calls per second PER SHARD across all consumers
- Data Retention:
	- 24 hours data retention by default
	- Can be extended to 365 days

#### Kinesis Data Firehose:
- Fully managed service, no administration
- Near RealTime (60 seconds latency minimum for non full batches)
- Data Ingestion into Redshift / Amazon S3 / ElasticSearch / Splunk
- Automatic scaling
- Supports many data format