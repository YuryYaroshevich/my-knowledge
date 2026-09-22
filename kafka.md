## Offsets
* `enable.auto.commit` = true(by default)
* with `auto.commit.interval.ms` = 5000(by default) offset is commited every time we call poll() on kafka consumer.
* `auto.offset.reset`=latest(read from end)|earliest(read from start)|none(throw exception of no offset found).
* consumer offsets can be lost if consumer hasn't read new data in 7 days. This is controlled by `offset.retention.minutes`

