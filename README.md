rcheck
======

CLI access to remote ping/http/dig/traceroute checks via the wheresitup.com endpoints.

Requires
--------
rcheck requires the *curb*, *json*, and *yaml* gems.

Usage
-----
    rcheck target test city
e.g.

    rcheck www.google.com trace seattle
    ---
    seattle:
      trace:
      - - 10.28.117.243 (10.28.117.243)
        - 0.031 ms
        - 0.023 ms
        - 0.024 ms
        - 0
      - - ae12.dar01.sr01.sea01.networklayer.com (67.228.118.224)
        - 0.176 ms
        - 0.199 ms
        - 0.186 ms
        - 1
      - - ae8.bbr01.wb01.sea02.networklayer.com (173.192.18.198)
        - 0.419 ms
        - 0.402 ms
        - 0.429 ms
        - 0
      - - 72.14.216.150 (72.14.216.150)
        - 0.454 ms
        - 0.487 ms
        - 0.471 ms
        - 1
      - - 66.249.94.212 (66.249.94.212)
        - 0.462 ms
        - 0.484 ms
        - ! '&mdash;'
        - 0
      - - 66.249.94.214 (66.249.94.214)
        - ! '&mdash;'
        - ! '&mdash;'
        - 0.525 ms
        - 0
      - - 66.249.94.199 (66.249.94.199)
        - 0.715 ms
        - ! '&mdash;'
        - ! '&mdash;'
        - 1
      - - 66.249.94.197 (66.249.94.197)
        - ! '&mdash;'
        - 0.820 ms
        - 0.725 ms
        - 1
      - - 216.239.46.156 (216.239.46.156)
        - 37.748 ms
        - 44.022 ms
        - ! '&mdash;'
        - 0
      - - 216.239.46.158 (216.239.46.158)
        - ! '&mdash;'
        - ! '&mdash;'
        - 36.941 ms
        - 0
      - - 72.14.239.48 (72.14.239.48)
        - 53.630 ms
        - ! '&mdash;'
        - ! '&mdash;'
        - 1
      - - 72.14.239.50 (72.14.239.50)
        - ! '&mdash;'
        - 53.672 ms
        - ! '&mdash;'
        - 1
      - - 216.239.46.53 (216.239.46.53)
        - ! '&mdash;'
        - ! '&mdash;'
        - 54.343 ms
        - 1
      - - 209.85.241.23 (209.85.241.23)
        - 68.677 ms
        - ! '&mdash;'
        - ! '&mdash;'
        - 0
      - - 72.14.232.140 (72.14.232.140)
        - ! '&mdash;'
        - 78.525 ms
        - ! '&mdash;'
        - 0
      - - 209.85.241.23 (209.85.241.23)
        - ! '&mdash;'
        - ! '&mdash;'
        - 68.710 ms
        - 0
      - - 72.14.237.111 (72.14.237.111)
        - 70.283 ms
        - ! '&mdash;'
        - ! '&mdash;'
        - 1
      - - 72.14.237.132 (72.14.237.132)
        - ! '&mdash;'
        - 68.851 ms
        - ! '&mdash;'
        - 1
      - - 72.14.237.131 (72.14.237.131)
        - ! '&mdash;'
        - ! '&mdash;'
        - 70.148 ms
        - 1
      - - 209.85.248.222 (209.85.248.222)
        - 85.238 ms
        - 69.155 ms
        - 70.219 ms
        - 0
      - - 72.14.236.148 (72.14.236.148)
        - 70.243 ms
        - 68.874 ms
        - 68.875 ms
        - 1
      - - 72.14.235.90 (72.14.235.90)
        - 144.205 ms
        - 144.134 ms
        - 143.160 ms
        - 0
      - - 72.14.232.134 (72.14.232.134)
        - 148.252 ms
        - 148.313 ms
        - 148.137 ms
        - 1
      - - 216.239.49.45 (216.239.49.45)
        - 148.778 ms
        - ! '&mdash;'
        - ! '&mdash;'
        - 0
      - - 209.85.252.83 (209.85.252.83)
        - ! '&mdash;'
        - 148.557 ms
        - 148.478 ms
        - 0
      - - wb-in-f99.1e100.net (74.125.132.99)
        - 148.903 ms
        - 147.972 ms
        - 149.974 ms
        - 1

    rcheck www.google.com ping seattle 
    ---
    seattle:
      ping:
        pings: []
        summary:
          transmitted: '10'
          received: '10'
          packetloss: 0%
          time: 4501ms
          min: '147.449'
          avg: '148.097'
          max: '148.662'
          mdev: 0.532 ms
    
    rcheck www.google.com http seattle
    ---
    seattle:
      http:
      - responseCode: 200
        responseStatus: OK
        serverIP: 74.125.132.99
        timingConnected: '0.148743'
        timingResponse: '0.306805'
        timingRequest: '0.306947'
    
    rcheck www.google.com dig seattle 
    ==============================================
    ---
    seattle:
      dig:
        question:
        - domain: www.google.com.
          type: A
        answer:
        - domain: www.google.com.
          type: A
          ttl: '99'
          ip: 74.125.132.99
        - domain: www.google.com.
          type: A
          ttl: '99'
          ip: 74.125.132.105
        - domain: www.google.com.
          type: A
          ttl: '99'
          ip: 74.125.132.106
        - domain: www.google.com.
          type: A
          ttl: '99'
          ip: 74.125.132.103
        - domain: www.google.com.
          type: A
          ttl: '99'
          ip: 74.125.132.147
        - domain: www.google.com.
          type: A
          ttl: '99'
          ip: 74.125.132.104
