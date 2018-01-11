# Networking for web dev

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

