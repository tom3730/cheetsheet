# AD環境の列挙

## ユーザーの列挙

Get-NetUser

Get-NetUser -SPN

## グループの列挙

Get-NetGroup


## コンピューターの列挙

Get-NetComputer

Get-NetComputer | select cn,dnshostname,operatingsystem

## ドメイン共有

Find-DomainShare
