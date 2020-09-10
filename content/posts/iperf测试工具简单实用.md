---
title: iperf 测试工具简单使用
date: 2019-08-02 16:48:02
tags: 
  - test
  - tool
categories:
  - Test

---

### 网络性能测试工具 iperf 简单使用



#### TCP协议测试

服务端

`iperf -s -p 12345 -i 10`

- -s 以server模式启动
- -p 指定服务器端使用的端口
- -i 以秒为单位，指定显示报告的时间间隔

客户端

`iperf -c 8.168.1.2 -p 12345 -i 10 -P 1000 -t 300`

- -c 8.168.1.2  以 client 模式启动，8.168.1.2是 server 端地址
- -p 指定客户端连接的端口（即服务端使用的端口）
- -i 以秒为单位，指定显示报告的时间间隔
- -P 指定客户端的并发数
- -t 测试时间，默认10秒



#### UDP协议测试

服务端

`iperf -u -s -C -p 12345 -i 10`

- -u 使用udp协议
- -s 以server模式启动
- -C 兼容旧版本（当server端和client端版本不一样时使用）
- -p 指定服务端使用的端口
- -i 显示报告的时间间隔

客户端

`iperf -u -c 8.168.1.2 -p 12345 -i 10  -P 1 -b 4M -t 300`

- -u 使用udp协议
- -c 以client模式启动
- -p 指定客户端连接的端口（即服务端使用的端口）
- -i 显示报告的时间间隔
- -P 客户端并发数
- -b 指定发送数据时的带宽或每秒发送的包数量
- -t 测试时间，默认10秒



**完整参数列表**

```
Client/Server:
-b, --bandwidth #[KMG | pps]  bandwidth to send at in bits/sec or packets per second
-e, --enhancedreports    use enhanced reporting giving more tcp/udp and traffic information
-f, --format    [kmKM]   format to report: Kbits, Mbits, KBytes, MBytes
-i, --interval  #        seconds between periodic bandwidth reports
-l, --len       #[KM]    length of buffer to read or write (default 8 KB)
-m, --print_mss          print TCP maximum segment size (MTU - TCP/IP header)
-o, --output    \<filename\> output the report or error message to this specified file
-p, --port      #        server port to listen on/connect to
-u, --udp                use UDP rather than TCP
-w, --window    #[KM]    TCP window size (socket buffer size)
-z, --realtime           request realtime scheduler
-B, --bind      \<host\>   bind to \<host\>, an interface or multicast address
-C, --compatibility      for use with older versions does not sent extra msgs
-M, --mss       #        set TCP maximum segment size (MTU - 40 bytes)
-N, --nodelay            set TCP no delay, disabling Nagle's Algorithm
-V, --ipv6_domain        Set the domain to IPv6

Server specific:
-s, --server             run in server mode
-U, --single_udp         run in single threaded UDP mode
-D, --daemon             run the server as a daemon

Client specific:
-c, --client    \<host\>   run in client mode, connecting to <host>
-d, --dualtest           Do a bidirectional test simultaneously
-n, --num       #[KM]    number of bytes to transmit (instead of -t)
-r, --tradeoff           Do a bidirectional test individually
-t, --time      #        time in seconds to transmit for (default 10 secs)
-B, --bind [\<ip\> | \<ip:port>] bind src addr(s) from which to originate traffic
-F, --fileinput \<name\>   input the data to be transmitted from a file
-I, --stdin              input the data to be transmitted from stdin
-L, --listenport #       port to receive bidirectional tests back on
-P, --parallel  #        number of parallel client threads to run
-T, --ttl       #        time-to-live, for multicast (default 1)
-Z, --linux-congestion \<algo\>  set TCP congestion control algorithm (Linux only)

Miscellaneous:
-x, --reportexclude [CDMSV]   exclude C(connection) D(data) M(multicast) S(settings) V(server) reports
-y, --reportstyle C      report as a Comma-Separated Values
-h, --help               print this message and quit
-v, --version            print version information and quit
```











