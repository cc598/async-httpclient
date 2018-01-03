#异步Http客户端原理实验

把同一个http客户端写成同步和异步形式，再用curl测试其吞吐率。

##异步
>Server Software:        
Server Hostname:        localhost
Server Port:            9090

>Document Path:          /home
Document Length:        243 bytes

>Concurrency Level:      100
Time taken for tests:   3.343 seconds
Complete requests:      1000
Failed requests:        0
Total transferred:      360000 bytes
HTML transferred:       243000 bytes
Requests per second:    299.13 [#/sec] (mean)
Time per request:       334.303 [ms] (mean)
Time per request:       3.343 [ms] (mean, across all concurrent requests)
Transfer rate:          105.16 [Kbytes/sec] received

>Connection Times (ms)
              min  mean[+/-sd] median   max
Connect:        0   11  22.4      0     111
Processing:    19  312 176.4    246    1058
Waiting:        2  228 194.0    163    1057
Total:         19  323 180.4    267    1059

>Percentage of the requests served within a certain time (ms)
  50%    267
  66%    333
  75%    425
  80%    448
  90%    586
  95%    687
  98%    841
  99%   1012
 100%   1059 (longest request)


总请求时间：3.343s 总请求数：1000reqs 并发请求数：100reqs
吞吐率=总请求数/总请求时间=299.133(reqs/s) 用户平均请求等待时间=总请求时间/（总请求数/并发用户数）=0.3343(s/reqs) 服务器平均请求等待时间=总请求时间/总请求数=0.003343(s/reqs)



##同步

>Server Software:        
Server Hostname:        localhost
Server Port:            9090

>Document Path:          /home
Document Length:        243 bytes

>Concurrency Level:      100
Time taken for tests:   3.633 seconds
Complete requests:      1000
Failed requests:        0
Total transferred:      360000 bytes
HTML transferred:       243000 bytes
Requests per second:    275.25 [#/sec] (mean)
Time per request:       363.303 [ms] (mean)
Time per request:       3.633 [ms] (mean, across all concurrent requests)
Transfer rate:          96.77 [Kbytes/sec] received

>Connection Times (ms)
              min  mean[+/-sd] median   max
Connect:        0   11  18.1      1      77
Processing:    11  342 120.7    331     671
Waiting:        0  197 100.3    181     583
Total:         42  353 123.0    361     699

>Percentage of the requests served within a certain time (ms)
  50%    361
  66%    396
  75%    415
  80%    427
  90%    514
  95%    640
  98%    652
  99%    666
 100%    699 (longest request)



总请求时间：3.633s 总请求数：1000reqs 并发请求数：100reqs
吞吐率=总请求数/总请求时间=275(reqs/s) 用户平均请求等待时间=总请求时间/（总请求数/并发用户数）=0.3633(s/reqs) 服务器平均请求等待时间=总请求时间/总请求数=0.003633(s/reqs)



##结论

可以发现无论是吞吐率还是用户等待时间，都是异步请求效率更高。
