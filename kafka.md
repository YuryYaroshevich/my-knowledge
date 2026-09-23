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
`max.poll.interval.ms` - default 5 minutes, max amount of time between two polls to consider consumer dead.
Increase if your consumer is slow and decrease if the opposite.
