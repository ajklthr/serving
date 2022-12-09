Test -Reactive

Scale when run = 1

Config:
autoscaling.knative.dev/metric: rps
autoscaling.knative.dev/target: "4.2"
autoscaling.knative.dev/target-utilization-percentage: "70"
autoscaling.knative.dev/target-burst-capacity: "0"


          <PreciseThroughputTimer guiclass="TestBeanGUI" testclass="PreciseThroughputTimer" testname="Precise Throughput Timer" enabled="true">
            <doubleProp>
              <name>allowedThroughputSurplus</name>
              <value>1.0</value>
              <savedValue>0.0</savedValue>
            </doubleProp>
            <intProp name="batchSize">1</intProp>
            <intProp name="batchThreadDelay">0</intProp>
            <longProp name="duration">120</longProp>
            <intProp name="exactLimit">10000</intProp>
            <longProp name="randomSeed">0</longProp>
            <doubleProp>
              <name>throughput</name>
              <value>150</value>
              <savedValue>0.0</savedValue>
            </doubleProp>
            <intProp name="throughputPeriod">60</intProp>
          </PreciseThroughputTimer>


Starting the test @ Fri Dec 09 18:18:40 UTC 2022 (1670609920610)
Remote engines have been started
Waiting for possible Shutdown/StopTestNow/Heapdump message on port 4445
summary =    154 in 00:00:59 =    2.6/s Avg:    66 Min:    12 Max:   457 Err:     0 (0.00%)
Tidying up remote @ Fri Dec 09 18:19:42 UTC 2022 (1670609982143)
... end of run



Test - Proactive


Config:   
autoscaling.knative.dev/metric: rps
autoscaling.knative.dev/target: "4.2"
autoscaling.knative.dev/target-utilization-percentage: "70"
autoscaling.knative.dev/target-burst-capacity: "0"


          <PreciseThroughputTimer guiclass="TestBeanGUI" testclass="PreciseThroughputTimer" testname="Precise Throughput Timer" enabled="true">
            <doubleProp>
              <name>allowedThroughputSurplus</name>
              <value>1.0</value>
              <savedValue>0.0</savedValue>
            </doubleProp>
            <intProp name="batchSize">1</intProp>
            <intProp name="batchThreadDelay">0</intProp>
            <longProp name="duration">120</longProp>
            <intProp name="exactLimit">10000</intProp>
            <longProp name="randomSeed">0</longProp>
            <doubleProp>
              <name>throughput</name>
              <value>150</value>
              <savedValue>0.0</savedValue>
            </doubleProp>
            <intProp name="throughputPeriod">60</intProp>
          </PreciseThroughputTimer>


Starting the test @ Fri Dec 09 18:11:52 UTC 2022 (1670609512989)
Remote engines have been started
Waiting for possible Shutdown/StopTestNow/Heapdump message on port 4445
summary =    140 in 00:01:00 =    2.3/s Avg:    22 Min:    12 Max:    49 Err:     0 (0.00%)
Tidying up remote @ Fri Dec 09 18:12:55 UTC 2022 (1670609575199)
... end of run


Results:

Test2 Reactive Latency - https://snapshots.raintank.io/dashboard/snapshot/W9M1ZBIgLUJF55yr9fYUeF7vf70XD7pi?orgId=2
Test2 Reactive-Pod-Count - https://snapshots.raintank.io/dashboard/snapshot/3EjAUwO3PpfU7xLQxNQBBny57PzgMbFu
Test2- Reactive -CPU -https://snapshots.raintank.io/dashboard/snapshot/RU31ZQQ2XZyOOE6cDsbvIARDMGrP05PD (edited)
Test 2- Reactive- Memory https://snapshots.raintank.io/dashboard/snapshot/XpS40r81ccDm0fI9svtoZezglGlkjBnj

Test2 PPA- Latency https://snapshots.raintank.io/dashboard/snapshot/UqeFOQvyrSVvaZvsz6HmT7pmZ9lEKLxX
Test2 -PPA - Pod https://snapshots.raintank.io/dashboard/snapshot/MpuOuODXp40SQLCTvJSU4dc2sNJ51rUn
Test2 PPA-CPUhttps://snapshots.raintank.io/dashboard/snapshot/7TXnMD5vEOoiKIFG4Rxsfm0D5V1jlV2M
Test2 PPA-MEM  https://snapshots.raintank.io/dashboard/snapshot/dXiUDN7OpYfaZNXhN1y1uV6wkoHwXFy8
