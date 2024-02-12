
1. Local memory
To measure latency and bandwidth to local memory (DRAM), you can use the mlc (Intel Memory Latency Checker) tool available here.

==>Graph for memory latency and memory bandwidth in the corresponding pdf file



Average bandwidth from excel file:
9565.336MB/sec


**COMMENTS AND OBSERVATIONS**

Latency vs. Inject Delay: There seems to be a fluctuation in latency as the inject delay increases. Initially, latency appears to decrease slightly as inject delay increases from 0 to 200 ns. However, beyond that point, latency remains relatively stable or decreases marginally despite further increases in inject delay.

Bandwidth vs. Inject Delay: Bandwidth also shows some variations with inject delay. Initially, there's a slight decrease in bandwidth as inject delay increases, but then it starts to increase gradually. However, the relationship between inject delay and bandwidth is not as pronounced as with latency.

Latency and Bandwidth Relationship: There seems to be a trade-off between latency and bandwidth. As latency decreases, bandwidth tends to increase, and vice versa. This relationship is not linear and might depend on various factors such as network congestion, system load, and communication protocols.

Saturation Point: Beyond a certain point of inject delay (around 200 ns), the improvements in latency and bandwidth start to diminish, suggesting a saturation point where further increases in inject delay might not yield significant performance improvements.

Network Characteristics: The observed patterns could be indicative of the underlying network characteristics and communication overhead within the cluster. It's essential to consider factors like network topology, routing algorithms, and packet processing delays that could influence the observed latency and bandwidth behaviors.

Optimization Potential: Analyzing these statistics can help identify potential optimization opportunities. For instance, optimizing the network configuration or communication protocols could lead to improvements in both latency and bandwidth, especially in scenarios where the inject delay is critical.

Application Considerations: The observed latency and bandwidth values should be evaluated concerning specific application requirements. Different applications may have different sensitivities to latency and bandwidth, so understanding these metrics is crucial for designing and deploying applications effectively in the cluster.

Overall, these observations highlight the complex interplay between inject delay, latency, and bandwidth in a cluster environment, emphasizing the need for thorough performance analysis and optimization strategies to ensure optimal system performance.



With the command cat/proc/meminfo  I have found out how much physical memory the machine has.Moreover, the total amount of memory will be displayed as MemTotal.


==> MemTotal:       131682620 kB


MemFree:        128124076 kB
MemAvailable:   128937596 kB
Buffers:           72404 kB
Cached:          1709788 kB
SwapCached:            0 kB
Active:           317108 kB
Inactive:        1555076 kB
Active(anon):      94576 kB
Inactive(anon):     1580 kB
Active(file):     222532 kB
Inactive(file):  1553496 kB
Unevictable:        5412 kB
Mlocked:            5412 kB
SwapTotal:       3145724 kB
SwapFree:        3145724 kB
Dirty:                40 kB
Writeback:             0 kB
AnonPages:         95520 kB
Mapped:           119124 kB
Shmem:              2080 kB
Slab:             409932 kB
SReclaimable:     180556 kB
SUnreclaim:       229376 kB
KernelStack:        7680 kB
PageTables:         4956 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:    68987032 kB
Committed_AS:     680328 kB
VmallocTotal:   34359738367 kB
VmallocUsed:           0 kB
VmallocChunk:          0 kB
HardwareCorrupted:     0 kB
AnonHugePages:         0 kB
ShmemHugePages:        0 kB
ShmemPmdMapped:        0 kB
CmaTotal:              0 kB
CmaFree:               0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:      578368 kB
DirectMap2M:     5300224 kB
DirectMap1G:    127926272 kB









2. Local disk

==>Graph for disk latency and in the corresponding pdf file

==> I have used ioping for measuring disk latency.This is the output after the execution of the corresponding
commands for this step.



4 KiB <<< /tmp/ (ext3 /dev/nvme0n1p1): request=1 time=146.8 us (warmup)
4 KiB <<< /tmp/ (ext3 /dev/nvme0n1p1): request=2 time=148.4 us
4 KiB <<< /tmp/ (ext3 /dev/nvme0n1p1): request=3 time=144.9 us
4 KiB <<< /tmp/ (ext3 /dev/nvme0n1p1): request=4 time=157.3 us
4 KiB <<< /tmp/ (ext3 /dev/nvme0n1p1): request=5 time=146.1 us
4 KiB <<< /tmp/ (ext3 /dev/nvme0n1p1): request=6 time=111.9 us
4 KiB <<< /tmp/ (ext3 /dev/nvme0n1p1): request=7 time=155.3 us
4 KiB <<< /tmp/ (ext3 /dev/nvme0n1p1): request=8 time=150.7 us
4 KiB <<< /tmp/ (ext3 /dev/nvme0n1p1): request=9 time=152.8 us
4 KiB <<< /tmp/ (ext3 /dev/nvme0n1p1): request=10 time=158.2 us (slow)
4 KiB <<< /tmp/ (ext3 /dev/nvme0n1p1): request=11 time=146.9 us
4 KiB <<< /tmp/ (ext3 /dev/nvme0n1p1): request=12 time=155.7 us
4 KiB <<< /tmp/ (ext3 /dev/nvme0n1p1): request=13 time=148.7 us
4 KiB <<< /tmp/ (ext3 /dev/nvme0n1p1): request=14 time=152.3 us
4 KiB <<< /tmp/ (ext3 /dev/nvme0n1p1): request=15 time=150.6 us
4 KiB <<< /tmp/ (ext3 /dev/nvme0n1p1): request=16 time=149.3 us
4 KiB <<< /tmp/ (ext3 /dev/nvme0n1p1): request=17 time=150.6 us
4 KiB <<< /tmp/ (ext3 /dev/nvme0n1p1): request=18 time=154.8 us
4 KiB <<< /tmp/ (ext3 /dev/nvme0n1p1): request=19 time=116.5 us
4 KiB <<< /tmp/ (ext3 /dev/nvme0n1p1): request=20 time=151.1 us

--- /tmp/ (ext3 /dev/nvme0n1p1) ioping statistics ---
19 requests completed in 2.80 ms, 76 KiB read, 6.78 k iops, 26.5 MiB/s
generated 20 requests in 19.0 s, 80 KiB, 1 iops, 4.21 KiB/s
min/avg/max/mdev = 111.9 us / 147.5 us / 158.2 us / 12.0 us

**COMMENTS AND OBSERVATIONS**
Consistency: The latency values for most requests are fairly consistent, with fluctuations within a relatively narrow range. This suggests that the disk is responding consistently to read requests, which is a positive sign for predictable performance.

Average Latency: The average latency (avg) of approximately 147.5 microseconds is relatively low, indicating that, on average, read requests to the /tmp directory are processed quickly. This suggests good performance for typical read operations.

Minimum and Maximum Latency: The minimum latency (min) of 111.9 microseconds and the maximum latency (max) of 158.2 microseconds show the range of response times observed. While the majority of requests fall within this range, there are occasional outliers where the disk response time is either exceptionally fast or slow.

Request Variation: Some requests exhibit slower response times compared to others, as indicated by the occasional "slow" remark in the output. For example, the 10th request has a time of 158.2 microseconds, which is noticeably higher than the average. Investigating the cause of these slower responses could help identify potential performance bottlenecks or issues.

IOPS and Throughput: The output also provides information about the Input/Output Operations Per Second (IOPS) and throughput. In this case, the disk is handling approximately 6.78 thousand IOPS with a throughput of 26.5 MiB/s. These metrics provide additional context for understanding the disk's performance characteristics.

Warmup Period: The initial request is labeled as "warmup", which may indicate that the first request experienced slightly different latency compared to subsequent requests. This could be due to factors such as disk caching or other system optimizations.

Overall, the results indicate relatively good disk performance with consistent response times and acceptable latency for read operations. However, further analysis and monitoring may be warranted to identify and address any occasional spikes in latency or potential performance issues.



==> I have used fio for measuring disk bandwidth.This is the output after the execution of the corresponding
commands for this step.

~$ fio --randrepeat=1 --ioengine=libaio --direct=1 --gtod_reduce=1 --name=fiotest --filename=testfio --bs=4k --iodepth=64 --size=1G --readwrite=read
fiotest: (g=0): rw=read, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=64
fio-3.16
Starting 1 process
fiotest: Laying out IO file (1 file / 1024MiB)
Jobs: 1 (f=1)
fiotest: (groupid=0, jobs=1): err= 0: pid=8385: Thu Feb  8 13:10:28 2024
  read: IOPS=156k, BW=609MiB/s (639MB/s)(1024MiB/1681msec)
   bw (  KiB/s): min=396768, max=779720, per=96.13%, avg=599653.33, stdev=192493.06, samples=3
   iops        : min=99192, max=194930, avg=149912.67, stdev=48123.15, samples=3
  cpu          : usr=35.42%, sys=56.85%, ctx=3760, majf=0, minf=73
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=0.1%, >=64=100.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.1%, >=64=0.0%
     issued rwts: total=262144,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=64

Run status group 0 (all jobs):
   READ: bw=609MiB/s (639MB/s), 609MiB/s-609MiB/s (639MB/s-639MB/s), io=1024MiB (1074MB), run=1681-1681msec

Disk stats (read/write):
  nvme0n1: ios=260646/0, merge=0/0, ticks=20477/0, in_queue=512, util=94.53%





Example usage: To retrieve information for the disk device /dev/sda

==>This is the output after the execution of the corresponding
commands for disk capacity.


~$ sudo hdparm -I /dev/sda

/dev/sda:

ATA device, with non-removable media
        Model Number:       INTEL SSDSC2BB480G7K
        Serial Number:      BTDV72420A3D480BGN
        Firmware Revision:  N201CS04
        Media Serial Num:
        Media Manufacturer:
        Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6, SATA Rev 3.0
Standards:
        Used: unknown (minor revision code 0x006d)
        Supported: 10 9 8 7 6 5
        Likely used: 10
Configuration:
        Logical         max     current
        cylinders       16383   0
        heads           16      0
        sectors/track   63      0
        --
        LBA    user addressable sectors:   268435455
        LBA48  user addressable sectors:   937703088
        Logical  Sector size:                   512 bytes
        Physical Sector size:                  4096 bytes
        Logical Sector-0 offset:                  0 bytes
        device size with M = 1024*1024:      457862 MBytes
        device size with M = 1000*1000:      480103 MBytes (480 GB)
        cache/buffer size  = unknown
        Form Factor: 2.5 inch
        Nominal Media Rotation Rate: Solid State Device
Capabilities:
        LBA, IORDY(can be disabled)
        Queue depth: 32
        Standby timer values: spec'd by Standard, no device specific minimum
        R/W multiple sector transfer: Max = 1   Current = 1
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4
             Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    SMART feature set
                Security Mode feature set
           *    Power Management feature set
           *    Write cache
           *    Look-ahead
           *    WRITE_BUFFER command
           *    READ_BUFFER command
           *    NOP cmd
           *    DOWNLOAD_MICROCODE
           *    48-bit Address feature set
           *    Mandatory FLUSH_CACHE
           *    FLUSH_CACHE_EXT
           *    SMART error logging
           *    SMART self-test
           *    General Purpose Logging feature set
           *    WRITE_{DMA|MULTIPLE}_FUA_EXT
           *    64-bit World wide name
           *    IDLE_IMMEDIATE with UNLOAD
           *    WRITE_UNCORRECTABLE_EXT command
           *    {READ,WRITE}_DMA_EXT_GPL commands
           *    Segmented DOWNLOAD_MICROCODE
           *    unknown 119[6]
           *    unknown 119[8]
           *    Gen1 signaling speed (1.5Gb/s)
           *    Gen2 signaling speed (3.0Gb/s)
           *    Gen3 signaling speed (6.0Gb/s)
           *    Native Command Queueing (NCQ)
           *    Phy event counters
           *    READ_LOG_DMA_EXT equivalent to READ_LOG_EXT
           *    Software settings preservation
           *    SMART Command Transport (SCT) feature set
           *    SCT Write Same (AC2)
           *    SCT Error Recovery Control (AC3)
           *    SCT Features Control (AC4)
           *    SCT Data Tables (AC5)
           *    SANITIZE_ANTIFREEZE_LOCK_EXT command
           *    SANITIZE feature set
           *    CRYPTO_SCRAMBLE_EXT command
           *    OVERWRITE_EXT command
           *    BLOCK_ERASE_EXT command
           *    reserved 69[2]
           *    reserved 69[3]
           *    reserved 69[4]
           *    Data Set Management TRIM supported (limit 4 blocks)
           *    Deterministic read ZEROs after TRIM
Security:
        Master password revision code = 65534
                supported
        not     enabled
        not     locked
        not     frozen
        not     expired: security count
                supported: enhanced erase
        4min for SECURITY ERASE UNIT. 4min for ENHANCED SECURITY ERASE UNIT.
Logical Unit WWN Device Identifier: 55cd2e414dd321f1
        NAA             : 5
        IEEE OUI        : 5cd2e4
        Unique ID       : 14dd321f1
Checksum: correct




3. Remote memory and disk
To measure network latency and bandwidth between two machines in the cluster


==> ping for measuring network latency

~$ ping node1
PING node1-link-1 (10.10.1.2) 56(84) bytes of data.
64 bytes from node1-link-1 (10.10.1.2): icmp_seq=1 ttl=64 time=0.382 ms
64 bytes from node1-link-1 (10.10.1.2): icmp_seq=2 ttl=64 time=0.184 ms
64 bytes from node1-link-1 (10.10.1.2): icmp_seq=3 ttl=64 time=0.183 ms
64 bytes from node1-link-1 (10.10.1.2): icmp_seq=4 ttl=64 time=0.184 ms
64 bytes from node1-link-1 (10.10.1.2): icmp_seq=5 ttl=64 time=0.181 ms
64 bytes from node1-link-1 (10.10.1.2): icmp_seq=6 ttl=64 time=0.183 ms
64 bytes from node1-link-1 (10.10.1.2): icmp_seq=7 ttl=64 time=0.183 ms
64 bytes from node1-link-1 (10.10.1.2): icmp_seq=8 ttl=64 time=0.180 ms
64 bytes from node1-link-1 (10.10.1.2): icmp_seq=9 ttl=64 time=0.182 ms
64 bytes from node1-link-1 (10.10.1.2): icmp_seq=10 ttl=64 time=0.181 ms
64 bytes from node1-link-1 (10.10.1.2): icmp_seq=11 ttl=64 time=0.184 ms
64 bytes from node1-link-1 (10.10.1.2): icmp_seq=12 ttl=64 time=0.179 ms
64 bytes from node1-link-1 (10.10.1.2): icmp_seq=13 ttl=64 time=0.180 ms
64 bytes from node1-link-1 (10.10.1.2): icmp_seq=14 ttl=64 time=0.182 ms
64 bytes from node1-link-1 (10.10.1.2): icmp_seq=15 ttl=64 time=0.182 ms
64 bytes from node1-link-1 (10.10.1.2): icmp_seq=16 ttl=64 time=0.182 ms
64 bytes from node1-link-1 (10.10.1.2): icmp_seq=17 ttl=64 time=0.180 ms
64 bytes from node1-link-1 (10.10.1.2): icmp_seq=18 ttl=64 time=0.181 ms
64 bytes from node1-link-1 (10.10.1.2): icmp_seq=19 ttl=64 time=0.186 ms
64 bytes from node1-link-1 (10.10.1.2): icmp_seq=20 ttl=64 time=0.184 ms
^C
--- node1-link-1 ping statistics ---
20 packets transmitted, 20 received, 0% packet loss, time 19444ms
rtt min/avg/max/mdev = 0.179/0.192/0.382/0.043 ms




==>iperf for measuring network bandwidth.



==>This the output for node0:

[  3] local 10.10.1.1 port 5001 connected with 10.10.1.2 port 54009
[ ID] Interval       Transfer     Bandwidth        Jitter   Lost/Total Datagrams
[  3]  0.0- 1.0 sec  1.19 MBytes  10.0 Mbits/sec   0.011 ms    0/  851 (0%)
[  3]  1.0- 2.0 sec  1.19 MBytes  10.0 Mbits/sec   0.013 ms    0/  851 (0%)
[  3]  2.0- 3.0 sec  1.19 MBytes  10.0 Mbits/sec   0.016 ms    0/  850 (0%)
[  3]  3.0- 4.0 sec  1.19 MBytes  10.0 Mbits/sec   0.010 ms    0/  850 (0%)
[  3]  4.0- 5.0 sec  1.19 MBytes  10.0 Mbits/sec   0.016 ms    0/  851 (0%)
[  3]  5.0- 6.0 sec  1.19 MBytes  10.0 Mbits/sec   0.010 ms    0/  850 (0%)
[  3]  6.0- 7.0 sec  1.19 MBytes  10.0 Mbits/sec   0.015 ms    0/  850 (0%)
[  3]  7.0- 8.0 sec  1.19 MBytes  10.0 Mbits/sec   0.016 ms    0/  851 (0%)
[  3]  8.0- 9.0 sec  1.19 MBytes  10.0 Mbits/sec   0.012 ms    0/  850 (0%)
[  3]  0.0-10.0 sec  11.9 MBytes  10.0 Mbits/sec   0.010 ms    0/ 8504 (0%)



==>This is the output for node1:

------------------------------------------------------------
[  3] local 10.10.1.2 port 54009 connected with 10.10.1.1 port 5001
[ ID] Interval            Transfer     Bandwidth      Write/Err  PPS
[  3] 0.0000-1.0000 sec  1.19 MBytes  10.0 Mbits/sec  852/0      851 pps
[  3] 1.0000-2.0000 sec  1.19 MBytes  10.0 Mbits/sec  850/0      850 pps
[  3] 2.0000-3.0000 sec  1.19 MBytes  10.0 Mbits/sec  850/0      850 pps
[  3] 3.0000-4.0000 sec  1.19 MBytes  10.0 Mbits/sec  851/0      850 pps
[  3] 4.0000-5.0000 sec  1.19 MBytes  10.0 Mbits/sec  850/0      850 pps
[  3] 5.0000-6.0000 sec  1.19 MBytes  10.0 Mbits/sec  850/0      850 pps
[  3] 6.0000-7.0000 sec  1.19 MBytes  10.0 Mbits/sec  851/0      850 pps
[  3] 7.0000-8.0000 sec  1.19 MBytes  10.0 Mbits/sec  850/0      850 pps
[  3] 8.0000-9.0000 sec  1.19 MBytes  10.0 Mbits/sec  850/0      850 pps
[  3] 0.0000-10.0008 sec  11.9 MBytes  10.0 Mbits/sec  8504/0      850 pps
[  3] Sent 8504 datagrams
[  3] Server Report:
[  3]  0.0-10.0 sec  11.9 MBytes  10.0 Mbits/sec   0.010 ms    0/ 8504 (0%)

**COMMENTS AND OBSERVATIONS**

Bandwidth:

Both node0 and node1 report a consistent bandwidth of 10.0 Mbits/sec throughout the test duration. This indicates that the network link between these two nodes is capable of sustaining a constant data transfer rate of 10.0 megabits per second.
Transfer Size:

Each interval reports a transfer size of 1.19 MBytes, contributing to a total transfer size of 11.9 MBytes over the entire test duration. This suggests that the size of each data transfer segment remains constant throughout the test.
Jitter:

The jitter, which measures the variation in packet arrival times, is consistently low across intervals, ranging from 0.010 ms to 0.016 ms. This indicates stable network performance without significant fluctuations in latency.
Lost Datagrams:

Both node0 and node1 report no lost datagrams throughout the test, indicated by the "0/8504 (0%)" notation. This implies a reliable network connection without packet loss.
Packet Rate (PPS):

Node1 reports the number of packets sent per second (PPS), which remains constant at 850 packets per second throughout the test. This suggests a consistent packet transmission rate.
Server Report:

Node1 provides a summary report, indicating a total transfer size of 11.9 MBytes over the entire 10-second duration, consistent with the client-side report from node0.



==>I have made a final graph for bandwidth,latency and capacity of local memory,local disk and network memory and disk.
Specifically, I have computed the avergaes of every measurement.