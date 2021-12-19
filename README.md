# wifishowpassword_powershell
Скрипт который показывает все пароли практически на любой версии Windows начиная(7-11)

#### Просто вставьте это в powershell:
```powershell
chcp 65001;cls;(netsh wlan show profiles) | Select-String "\:(.+)$" | %{$name=$_.Matches.Groups[1].Value.Trim(); $_} | %{(netsh wlan show profile name="$name" key=clear)} | Select-String "Key Content\W+\:(.+)$" | %{$pass=$_.Matches.Groups[1].Value.Trim(); $_} | %{[PSCustomObject]@{ PROFILE_NAME=$name;PASSWORD=$pass }} | Format-Table -Wrap
```
