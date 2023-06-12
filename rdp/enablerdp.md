# RDPを有効にする

## RDP有効

Set-ItemProperty -Path "HKLM:\System\CurrentControlSet\Control\Terminal Server" -Name "fDenyTSconnections" -Value 0


## FW

Enable-NetFirewallRule -DisplayGroup "Remote Desktop"

