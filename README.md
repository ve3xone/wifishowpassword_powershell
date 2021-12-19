# wifishowpassword_powershell
Скрипт который показывает все пароли от wifi практически на любой версии Windows(7-11), работает через powershell

#### Просто вставьте это в powershell:
```powershell
chcp 65001;cls;(netsh wlan show profiles) | Select-String "\:(.+)$" | %{$name=$_.Matches.Groups[1].Value.Trim(); $_} | %{(netsh wlan show profile name="$name" key=clear)} | Select-String "Key Content\W+\:(.+)$" | %{$pass=$_.Matches.Groups[1].Value.Trim(); $_} | %{[PSCustomObject]@{ PROFILE_NAME=$name;PASSWORD=$pass }} | Format-Table -Wrap
```
#### [Огромное спасибо ребятам из winitpro](https://winitpro.ru/index.php/2020/11/09/pokazat-sohranenie-paroli-wi-fi-setej-v-windows/)
