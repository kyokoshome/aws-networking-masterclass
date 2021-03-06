
# SSH Guide

## Login to EC2 instance 
Depending on your computer’s OS there are various methods to login to your ec2 instance 

###   Linux Based Systems and Mac OS
Download private key from Chime room

Change permissions of your private key so that only you can use it. 
```
chmod 400 /path/L2H.pem SSH into you instance 
ssh -i /path/ L2H.pem ec2-user@[See your IP at Chime Room] 
```

You should see a response like the following 
```
The authenticity of host 'ec2-198-51-100-1.compute-1.amazonaws.com (10.254.142.33)'
can't be established.
RSA key fingerprint is 1f:51:ae:28:bf:89:e9:d8:1f:25:5d:37:2d:7d:b8:ca:9f:f5:f1:6f. 
Are you sure you want to continue connecting (yes/no)? 
```
Click Yes 

### *Windows* 

Convert the .pem file to .ppk file for use with putty 

![](https://github.com/kyokoshome/aws-networking-masterclass/blob/master/img/win1.png)

Open Putty terminal and enter ec2-user@[IP at you name card] in the hostname 

![](https://github.com/kyokoshome/aws-networking-masterclass/blob/master/img/win2.png)

Load the ppk file 

![](https://github.com/kyokoshome/aws-networking-masterclass/blob/master/img/win3.png)

Click open to start a putty session 


### Step-3: Test EC2 instance connectivity
Run the following command  

```
curl -v ipinfo.io
```

You should see a response like the following
```
* $ curl -v ipinfo.io
* Rebuilt URL to: ipinfo.io/
*   Trying 216.239.36.21...
* TCP_NODELAY set
* Connected to ipinfo.io (216.239.36.21) port 80 (#0)
> GET / HTTP/1.1
> Host: ipinfo.io
> User-Agent: curl/7.52.1
> Accept: */*
>
< HTTP/1.1 200 OK
< Date: Tue, 28 Apr 2020 06:09:44 GMT
< Content-Type: application/json; charset=utf-8
< Content-Length: 321
< Vary: Accept-Encoding
< Access-Control-Allow-Origin: *
< X-Frame-Options: DENY
< X-XSS-Protection: 1; mode=block
< X-Content-Type-Options: nosniff
< Referrer-Policy: strict-origin-when-cross-origin
< Via: 1.1 google
<
{
  "ip": "3.112.234.196",
  "hostname": "ec2-3-112-234-196.ap-northeast-1.compute.amazonaws.com",
  "city": "Tokyo",
  "region": "Tokyo",
  "country": "JP",
  "loc": "35.6895,139.6917",
  "org": "AS16509 Amazon.com, Inc.",
  "postal": "151-0052",
  "timezone": "Asia/Tokyo",
  "readme": "https://ipinfo.io/missingauth"
* Curl_http_done: called premature == 0
* Connection #0 to host ipinfo.io left intact
```


## TCP:

### Recommend Resource:
* TCP State Machine 
http://tcpipguide.com/free/t_TCPOperationalOverviewandtheTCPFiniteStateMachineF-2.htm
* TCP 3 way-handshake
http://www.tcpipguide.com/free/t_TCPConnectionEstablishmentProcessTheThreeWayHandsh-3.htm
* TCP 4 way-Closure
http://www.tcpipguide.com/free/t_TCPConnectionTermination-2.htm
* TCP segment
http://www.tcpipguide.com/free/t_TCPMessageSegmentFormat-3.htm
* Wireshake packet parse:
https://www.cnblogs.com/TankXiao/archive/2012/10/10/2711777.html
* MSS/MTU
https://www.incapsula.com/blog/mtu-mss-explained.html
* Window Scale
RFC:
https://tools.ietf.org/html/rfc1323#page-8
https://www.cnblogs.com/djiankuo/p/7019768.html
* TCP keepalive/HTTP keepalive
https://blog.csdn.net/oceanperfect/article/details/51064574
*  High Performance Browser Networking - TCP:
https://hpbn.co/building-blocks-of-tcp/


