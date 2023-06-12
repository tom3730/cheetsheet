# 現在のDNS設定を確認する
Get-DnsClientServerAddress -AddressFamily IPv4

# AD参加しているサーバのDNSをかえる
Set-DnsClientServerAddress -InterfaceIndex 1 -ServerAddresses("<DC_IP>")
Set-DnsClientServerAddress -InterfaceIndex 2 -ServerAddresses("<DC_IP>")
