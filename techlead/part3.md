## Scalability vs Performance

«If you can scale vertically, do it!»: если можно масштабироваться вертикально, лучше так и сделать. При небольшой нагрузке масштабированная система будет работать медленнее немасштабированной засчёт load balancer, communication between nodes, etc.

## Availability

### Последовательный vs параллельный поток обработки

Доступность при последовательном потоке обработки: A = A1 * A2 -> 99% * 99% = 98%
Доступность при параллельном потоке обработки: A = 1 - (1-A1) * (1-A2) -> 1 - (1 - 99%) * (1 - 99%) = 99.99%

Балансировка бывает:
* серверной(load balancer)
* клиентской(client decides to which instance request should be sent)
* DNS балансировка