JMH benchmark for String replace
================================================
ref: 
* http://openjdk.java.net/projects/code-tools/jmh
* http://java-performance.info/jmh/
* http://java-performance.info/introduction-jmh-profilers/
* http://hg.openjdk.java.net/code-tools/jmh/file/tip/jmh-samples/src/main/java/org/openjdk/jmh/samples/

#build jar
```
mvn clean package
```

#get help from cmd `java -jar target/benchmarks.jar  -h`
* List matching benchmarks -- `java -jar target/benchmarks.jar -l `
* List profilers -- `java -jar target/benchmarks.jar  -lprof `

#run
```
java -jar target/benchmarks.jar  StringReplaceBenchmark -wi 3 -i 6 -f 1 -tu ms
```
```
Benchmark                                                Mode  Cnt       Score      Error   Units
StringReplaceBenchmark.testFast                         thrpt    6    9452.604 ±  206.597  ops/ms
StringReplaceBenchmark.testFastLong                     thrpt    6     141.205 ±    5.052  ops/ms
StringReplaceBenchmark.testFastLongNoMatch              thrpt    6     338.768 ±    6.288  ops/ms
StringReplaceBenchmark.testFastNoMatch                  thrpt    6   95299.407 ±  914.842  ops/ms
StringReplaceBenchmark.testLang3StringUtils             thrpt    6    7180.628 ±  110.975  ops/ms
StringReplaceBenchmark.testLang3StringUtilsLong         thrpt    6     149.292 ±    3.630  ops/ms
StringReplaceBenchmark.testLang3StringUtilsLongNoMatch  thrpt    6     347.124 ±    3.906  ops/ms
StringReplaceBenchmark.testLang3StringUtilsNoMatch      thrpt    6   86763.723 ± 1068.531  ops/ms
StringReplaceBenchmark.testOsgl                         thrpt    6    8678.101 ± 1286.512  ops/ms
StringReplaceBenchmark.testOsglLong                     thrpt    6     217.889 ±    6.731  ops/ms
StringReplaceBenchmark.testOsglLongNoMatch              thrpt    6     407.895 ±    4.442  ops/ms
StringReplaceBenchmark.testOsglNoMatch                  thrpt    6   29719.813 ±  531.590  ops/ms
StringReplaceBenchmark.testString                       thrpt    6    2616.016 ±  220.651  ops/ms
StringReplaceBenchmark.testStringLong                   thrpt    6      72.485 ±    2.366  ops/ms
StringReplaceBenchmark.testStringLongNoMatch            thrpt    6     253.809 ±    9.510  ops/ms
StringReplaceBenchmark.testStringNoMatch                thrpt    6    7099.968 ±  164.769  ops/ms
StringReplaceBenchmark.testStringUtils                  thrpt    6    8178.607 ±  115.928  ops/ms
StringReplaceBenchmark.testStringUtilsLong              thrpt    6     153.263 ±    5.699  ops/ms
StringReplaceBenchmark.testStringUtilsLongNoMatch       thrpt    6     330.020 ±    7.464  ops/ms
StringReplaceBenchmark.testStringUtilsNoMatch           thrpt    6  101255.351 ±  980.553  ops/ms
```


```
java -jar target/benchmarks.jar  StringReplaceBenchmark -wi 3 -i 6 -f 1  -bm thrpt,avgt -tu us
```
```
Benchmark                                      Mode  Cnt  Score   Error   Units
StringReplaceBenchmark.test4Osgl              thrpt    6  4.696 ± 0.070  ops/us
StringReplaceBenchmark.test4String            thrpt    6  1.332 ± 0.160  ops/us
StringReplaceBenchmark.test4StringUtils       thrpt    6  4.212 ± 0.091  ops/us
StringReplaceBenchmark.test4fast              thrpt    6  4.895 ± 0.353  ops/us
StringReplaceBenchmark.test4lang3StringUtils  thrpt    6  3.364 ± 0.027  ops/us
StringReplaceBenchmark.test4Osgl               avgt    6  0.216 ± 0.009   us/op
StringReplaceBenchmark.test4String             avgt    6  0.773 ± 0.294   us/op
StringReplaceBenchmark.test4StringUtils        avgt    6  0.245 ± 0.022   us/op
StringReplaceBenchmark.test4fast               avgt    6  0.188 ± 0.009   us/op
StringReplaceBenchmark.test4lang3StringUtils   avgt    6  0.315 ± 0.007   us/op
```

```
java -jar target/benchmarks.jar  StringReplaceBenchmark -wi 3 -i 6 -f 1 -prof gc
```

```
Benchmark                                                                       Mode  Cnt        Score        Error   Units
StringReplaceBenchmark.test4Osgl                                               thrpt    6  4737653.657 ±  98116.460   ops/s
StringReplaceBenchmark.test4Osgl:·gc.alloc.rate                                thrpt    6     1228.683 ±     25.418  MB/sec
StringReplaceBenchmark.test4Osgl:·gc.alloc.rate.norm                           thrpt    6      408.000 ±      0.001    B/op
StringReplaceBenchmark.test4Osgl:·gc.churn.PS_Eden_Space                       thrpt    6     1312.367 ±    704.467  MB/sec
StringReplaceBenchmark.test4Osgl:·gc.churn.PS_Eden_Space.norm                  thrpt    6      435.757 ±    231.955    B/op
StringReplaceBenchmark.test4Osgl:·gc.churn.PS_Survivor_Space                   thrpt    6        0.069 ±      0.080  MB/sec
StringReplaceBenchmark.test4Osgl:·gc.churn.PS_Survivor_Space.norm              thrpt    6        0.023 ±      0.026    B/op
StringReplaceBenchmark.test4Osgl:·gc.count                                     thrpt    6       19.000               counts
StringReplaceBenchmark.test4Osgl:·gc.time                                      thrpt    6       20.000                   ms
StringReplaceBenchmark.test4String                                             thrpt    6  1324709.557 ±  22571.671   ops/s
StringReplaceBenchmark.test4String:·gc.alloc.rate                              thrpt    6     1212.556 ±     20.726  MB/sec
StringReplaceBenchmark.test4String:·gc.alloc.rate.norm                         thrpt    6     1440.000 ±      0.001    B/op
StringReplaceBenchmark.test4String:·gc.churn.PS_Eden_Space                     thrpt    6     1221.226 ±    500.956  MB/sec
StringReplaceBenchmark.test4String:·gc.churn.PS_Eden_Space.norm                thrpt    6     1450.689 ±    603.800    B/op
StringReplaceBenchmark.test4String:·gc.churn.PS_Survivor_Space                 thrpt    6        0.062 ±      0.074  MB/sec
StringReplaceBenchmark.test4String:·gc.churn.PS_Survivor_Space.norm            thrpt    6        0.074 ±      0.089    B/op
StringReplaceBenchmark.test4String:·gc.count                                   thrpt    6       26.000               counts
StringReplaceBenchmark.test4String:·gc.time                                    thrpt    6       24.000                   ms
StringReplaceBenchmark.test4StringUtils                                        thrpt    6  3781943.748 ±  75046.418   ops/s
StringReplaceBenchmark.test4StringUtils:·gc.alloc.rate                         thrpt    6     1192.358 ±     23.568  MB/sec
StringReplaceBenchmark.test4StringUtils:·gc.alloc.rate.norm                    thrpt    6      496.000 ±      0.001    B/op
StringReplaceBenchmark.test4StringUtils:·gc.churn.PS_Eden_Space                thrpt    6     1248.335 ±    337.017  MB/sec
StringReplaceBenchmark.test4StringUtils:·gc.churn.PS_Eden_Space.norm           thrpt    6      519.457 ±    145.629    B/op
StringReplaceBenchmark.test4StringUtils:·gc.churn.PS_Survivor_Space            thrpt    6        0.073 ±      0.121  MB/sec
StringReplaceBenchmark.test4StringUtils:·gc.churn.PS_Survivor_Space.norm       thrpt    6        0.030 ±      0.050    B/op
StringReplaceBenchmark.test4StringUtils:·gc.count                              thrpt    6       25.000               counts
StringReplaceBenchmark.test4StringUtils:·gc.time                               thrpt    6       22.000                   ms
StringReplaceBenchmark.test4fast                                               thrpt    6  4375516.774 ±  58662.515   ops/s
StringReplaceBenchmark.test4fast:·gc.alloc.rate                                thrpt    6      600.764 ±      8.056  MB/sec
StringReplaceBenchmark.test4fast:·gc.alloc.rate.norm                           thrpt    6      216.000 ±      0.001    B/op
StringReplaceBenchmark.test4fast:·gc.churn.PS_Eden_Space                       thrpt    6      609.346 ±    142.370  MB/sec
StringReplaceBenchmark.test4fast:·gc.churn.PS_Eden_Space.norm                  thrpt    6      219.158 ±     53.998    B/op
StringReplaceBenchmark.test4fast:·gc.churn.PS_Survivor_Space                   thrpt    6        0.101 ±      0.101  MB/sec
StringReplaceBenchmark.test4fast:·gc.churn.PS_Survivor_Space.norm              thrpt    6        0.036 ±      0.036    B/op
StringReplaceBenchmark.test4fast:·gc.count                                     thrpt    6       52.000               counts
StringReplaceBenchmark.test4fast:·gc.time                                      thrpt    6       46.000                   ms
StringReplaceBenchmark.test4lang3StringUtils                                   thrpt    6  3077705.258 ± 246133.484   ops/s
StringReplaceBenchmark.test4lang3StringUtils:·gc.alloc.rate                    thrpt    6      970.373 ±     77.640  MB/sec
StringReplaceBenchmark.test4lang3StringUtils:·gc.alloc.rate.norm               thrpt    6      496.000 ±      0.001    B/op
StringReplaceBenchmark.test4lang3StringUtils:·gc.churn.PS_Eden_Space           thrpt    6      893.991 ±    751.504  MB/sec
StringReplaceBenchmark.test4lang3StringUtils:·gc.churn.PS_Eden_Space.norm      thrpt    6      458.328 ±    398.802    B/op
StringReplaceBenchmark.test4lang3StringUtils:·gc.churn.PS_Survivor_Space       thrpt    6        0.017 ±      0.078  MB/sec
StringReplaceBenchmark.test4lang3StringUtils:·gc.churn.PS_Survivor_Space.norm  thrpt    6        0.009 ±      0.040    B/op
StringReplaceBenchmark.test4lang3StringUtils:·gc.count                         thrpt    6        7.000               counts
StringReplaceBenchmark.test4lang3StringUtils:·gc.time                          thrpt    6        5.000                   ms
```