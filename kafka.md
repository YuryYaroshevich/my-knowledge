## Offsets
* `enable.auto.commit` = true(by default)
* with `auto.commit.interval.ms` = 5000(by default) offset is commited every time we call poll() on kafka consumer.
* `auto.offset.reset`=latest(read from end)|earliest(read from start)|none(throw exception of no offset found).
* consumer offsets can be lost if consumer hasn't read new data in 7 days and considered as inactive. This is controlled by `offset.retention.minutes`

## Consumer heartbeat thread
* `heartbeat.interval.ms` - default 3 seconds, how often to send heartbeats.
* `session.timeout.ms` - default 45 seconds, if no heartbeat during this period, consumer considered dead.
Use these configs to speed up consumer rebalances.

## Coonsumer poll thread
* `max.poll.interval.ms` - default 5 minutes, max amount of time between two polls to consider consumer dead.
Increase if your consumer is slow and decrease if the opposite.
* `max.poll.records` - default 500, how many records to fetch with one poll request.
* `fetch.min.bytes` - default 1, how much data to poll at least on each request. Time which is broker waits to fullfil this requirement - `fetch.max.wait.ms` - default 500.
* `max.partition.fetch.bytes` - default 1mb, max amount of data to fetch from 1 partition.
* `fetch.max.bytes` - default 55mb, max data to return in one request.

## Consumer behaviour
Normally consumer reads partition from broker which is a leader for that partition, but from kafka 2.4 reads from replicase are allowed given the proper config in place(rack.id=client.rack, replicas.selector.class = ...RackAwareReplicaSelector)