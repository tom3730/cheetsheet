# Kali LinuxからWindowsへファイルを送る

Kali側でWebサーバーを立て、Windows(PowerShell)からiwr(Windows版のwget的なコマンドで取得する。

@Kali
```
cd <DIRECTORY>
python -m http.server 80
```

@Windows(PowerShell)
```
iwr -Uri http://<KALI_IP>/<FILENAME> -Outfile <FILENAME>
```
