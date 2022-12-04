# Compare the Avg and P99 Latency for PPA and Reactive scalar

# For PPA

1. Set PPA Lambda to average rps (this will be later calculated by periodic cluster probing) in autoscaler.go
2. Use JMeter -Precise throughput timer to construct a poisson distribution load based on the average rps
3. Get Avg and P99 latency


# For Reactive

1. Use JMeter -Precise throughput timer to construct a poisson distribution load based on the same average rps
2. Set scale from zero
3. Get Avg and P99 latency


# For Reactive

1. Use JMeter -Precise throughput timer to construct a poisson distribution load based on the same average rps
2. Set scale from 1
3. Get Avg and P99 latency
