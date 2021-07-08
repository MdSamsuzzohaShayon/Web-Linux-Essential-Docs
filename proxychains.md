## [Prodychains](https://github.com/rofl0r/proxychains-ng)
 - Proxy: In computer networking, a proxy server is a server application or appliance that acts as an intermediary for requests from clients seeking resources from servers that provide those resources. 
 - Proxy vs VPN: VPNs provide greater protection because they encrypt traffic. For organizations that deal with sensitive data and need to keep their browsing activity hidden, a VPN is the ideal solution. Organizations that are simply looking for users to browse the internet anonymously can benefit from a proxy server. This also enables them to see which websites their employees are visiting and ensure employees can access sites that would otherwise be blocked in their country. A proxy acts as a gateway – it’s ideal for basic functions like anonymous web browsing and managing (or circumventing) content restrictions.A VPN client on your computer establishes a secure tunnel with the VPN server, replacing your local ISP routing. VPN connections encrypt and secure all of your network traffic, not just the HTTP or SOCKS calls from your browser like a proxy server.
 - [ProxyChains:](https://github.com/haad/proxychains) ProxyChains is a UNIX program, that hooks network-related libc functions in dynamically linked programs via a preloaded DLL and redirects the connections through SOCKS4a/5 or HTTP proxies.
```
sudo apt install proxychains
```
- [PROXYCHAINS FEATURES](https://linuxhint.com/proxychains-tutorial/)
Support SOCKS5, SOCKS4, and HTTP CONNECT proxy servers.
Proxychains can be mixed up with a different proxy types in a list
Proxychains also supports any kinds of chaining option methods, like: random, which takes a random proxy in the list stored in a configuration file, or chaining proxies in the exact order list, different proxies are separated by a new line in a file. There is also a dynamic option, that lets Proxychains go through the live only proxies, it will exclude the dead or unreachable proxies, the dynamic option often called smart option.
Proxychains can be used with servers, like squid, sendmail, etc.
Proxychains is capable to do DNS resolving through proxy.
Proxychains can handle any TCP client application, ie., nmap, telnet.
 - [Types of Proxy Servers (Protocols)](https://www.educba.com/types-of-proxy-servers/)
Below are the different types of proxy servers protocols:
Socks Proxy Server: This type of proxy server provides a connection to a particular server. Depending on Socks protocols, this type of server allows the multilayering of various data types such as TCS or UDP.
FTP Proxy Server: This type of proxy server caches FTP requests’ traffic and uses the concept of relaying.
HTTP Proxy Server: This proxy was developed to process a one-way request to the web pages using HTTP protocols.
SSL Proxy Server: This type of server was developed using the concept of TCP relaying being used in the SOCKS 
proxy protocol to allow Web Pages’ requests.
 - [Socks vs HTTP Proxy](https://oxylabs.io/blog/socks-vs-http-proxy)
There is no question of rivalry since selecting between SOCKS vs HTTP proxies depends on your use case and needs. SOCKS may be a reliable choice for projects that involve downloading and transferring large amounts of data. On the other hand, HTTP proxies may be ideal for filtering data for security or performance reasons. If in doubt, if your target is HTTP(S), HTTP proxies should work just fine for you. Oxylabs’ HTTP proxies are considered as one of the most stable proxy types on the market. 
Unlike HTTP proxies, which can only interpret and work with HTTP and HTTPS webpages, SOCKS5 proxies can work with any traffic.
 - [Proxy annonimity levels](https://proxyscrape.com/blog/proxy-anonymity-levels/)
Transparent proxies do not hide your IP Address and they don’t alter any user information.
An anonymous proxy does not reveal your IP address but does reveal that you are using a proxy server.
Elite proxy servers hide both your IP address and the fact that you are using a proxy server at all.
 - [Types of chains](https://linuxhint.com/proxychains-tutorial/)
Random chaining will allow proxychains to randomly choose IP addresses from our list and each time we use proxychains, the chain of proxy will look different to the target, making it harder to track our traffic from its source.
 Dynamic chaining will enable us to run our traffic through every proxy on our list, and if one of the proxies is down or not responding, the dead proxies are skipped, it will automatically go to the next proxy in the list without throwing an error. Each connection will be done via chained proxies. All proxies will be chained in the order as they appear in the list.

Get free proxy
__https://spys.one/en/__
__https://free-proxy-list.net/__
__https://www.proxynova.com__


### tor
 - [tor](https://2019.www.torproject.org/docs/documentation.html.en) 
Tor is free software and an open network that helps you defend against traffic analysis, a form of network surveillance that threatens personal freedom and privacy, confidential business activities and relationships, and state security.
```
sudo apt install tor
```

- [configuring proxychains](https://linuxhint.com/proxychains-tutorial/)
```
sudo nano /etc/proxychains.conf
```















