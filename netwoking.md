# Networking

### What is netcat (nc)

It can open TCP connections, send UDP packets, listen on arbitrary TCP and  
UDP ports, do port scanning, and deal with both IPv4 and IPv6.


### Simple nc command to make TCP connection to a server

```
nc en.wikipedia.org 80
```

### After creating TCP connection we can send strings to the servers

```
printf 'HEAD / HTTP/1.1\r\nHost: en.wikipedia.org\r\n\r\n' | nc en.wikipedia.org 80
```

It simply connects to wikipedia and sends the string after printf to the  
connected server over TCP.
To the server it looks like a HTTP request so it responds.  
NC doesn't care about the http protocol or the ssh protocols built over the  
TCP protocols, nc's job is to only create/listen connection and send text  

The server responded because to it the string looked like an HTTP request  
so a response was sent.

### Listen on a port which means a plain TCP server is created

```
nc -l 8080
```
A simple TCP server is created over which I can send and receive strings.  
This connection is bi-directional so connect to localhost:8080 using nc and write some text  

```
nc localhost 8080
```
Now on 1 terminal I have the server listening and other terminal connected to  
that server over TCP.  
Now write some text on both ends. It will act like a simple chat app.

### Simple Cool excercise

send http response from the nc server (open localhost:8080 in browser)

```
printf 'HTTP/1.1 302 Moved\r\nLocation: https://www.eff.org/' | nc -l 2345
```
This string is in format of simple http response, browser interprets the response and  
redirects to `https://www.eff.org/`  

## DNS

These servers hold records which map host_name to IP addresses (IPV4 and IPV6)  
there are various other records that they maintain but A type is most important (host name to IPV4)  

### Look IP of any website using linux `host`  

```
host google.com
```

### Look at specific type of record in DNS

```
host -t A google.com
```
-t = type  
A = A type record  
for google.com

### Using `dig` for getting DNS records

```
dig google.com
```
It gives us more technical information as compared to `host` command.  
`host` command is more human readable, whereas dig is used more at places  
where scripts are to be written  

### DNS record types

1. A type - stores domain name vs IP address  
2. C Name - it is an alias record  
3. AAAA - IPV6 record
4. NS - Name server records  

## Network Stack

1. Application Layer  
2. Transport Layer - TCP/UDP  
3. IP Layer  
4. Physical Layer  

### Monitor Network Trafic when some request is made

```
sudo tcpdump -n host 8.8.8.8
```
so if any kind of network flows between my computer and 8.8.8.8 then that  
text would come up here  

For example - make ping request to `8.8.8.8` and you will see the actual TCP traffic  
between my computer and 8.8.8.8 server  

```
sudo tcpdump -n port 53
```
This command will monotor any TCP traffic that happen through port 53 (DNS)  

### Small excercise and great learning

monitor the TCP traffic on a closed port on some host, for example -  
```
sudo tcpdump -n port 12345
```
This is used to monitor traffic on port 12345  

```
nc www.google.com 12345
```
This will be used to send traffic to google on port 12345  

*What do you observe?*  
NC will ask computer to connect to google.com on port 12345  
but since that port is closed, no matter how much the computer tries  
it fails again and again.  
When I observe traffic in `tcpdump` I observe that same packet is sent to  
connect to google again and again but no success.  
Another observation - same packet is sent because computer thinks that previous  
packet was lost or the response could not reach the computer. So same packet is  
resent because no acknowledgement was received. Packet sending pace reduces with  
time and after a considerable amount of effort, the computer stops trying.  

### How Traceroute works ? 

Traceroute makes clever usage of TTL on a packet.  
TTL - Time To Live, when TTL expires then error message sent to source of that packet  
In reality when a packet is sent to a destination server then TTL starts with a high  
value and is reduced by 1 whenever it hops by 1. So that if it ever gets stuck in  
a infinite loop then the source can be notified that packet was undelivered.  

This concept is used by traceroute to find hops.  
`Traceroute` sends packet with TTL 0 then TTL 1 then TTL 2 and so on  
till the error response from the destination is received. This way the  
whole route can be traced from the packet journey,  

### NAT - Network Address Translation  

NAT is maintained by the routers, as these actually solve the  
problem of limited IPV4 addresses.  
My router is assigned an IP address by my ISP and now my  
router gives an new local IP to me. NAT keeps map of  
public IP addresses and ports to local Ip addresses and  
ports. This is how with limited IPV4 addresses we are able  
to connect more people.  

*Disadvantage*  
Lookup for interface in a map is time consuming so IPV6 should be used

