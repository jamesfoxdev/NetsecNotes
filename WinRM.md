---
tags: [Exploitation, Powershell]
title: Exploitation/WinRM
created: '2020-01-04T22:20:05.889Z'
modified: '2020-01-04T23:02:59.096Z'
---

# Exploitation/WinRM
WinRM is a service (usually on port `5986`) which allows remote powershell code execution

## Start a WinRM Instance
Starting WinRM
```
Enable-PSRemoting –force
```
Set WinRM to start automatically on boot
```
Set-Service WinRM -StartMode Automatic
```
Verify start mode and state of service
```
Get-WmiObject -Class win32_service | Where-Object {$_.name -like "WinRM"}
```
Set all remote hosts to trusted
```
Set-Item WSMan:localhost\client\trustedhosts -value *
```

## Executing Remote Commands
Without Auth
```
Invoke-Command –ComputerName <target> -ScriptBlock {<PSCode>}
```
With Auth
```
Invoke-Command –ComputerName -Credential <domain>\<username> <target> -ScriptBlock {<PSCode>}
```

## Starting an Interactive Console Through PS
Without auth
```
Enter-PsSession –ComputerName <target>
```
With auth
```
Enter-PsSession –ComputerName <target> –Credentials <domain>\<username>
```

## Using Ruby WinRM (good on Linux)
### Using Plaintext Creds
For example `examplewinrm.rb`
```
gem install winrm
```
```
require 'winrm'

conn = WinRM::Connection.new( 
  endpoint: 'https://IP:5986/wsman',
  transport: :ssl,
  user: 'username',
  password: 'password',
  :no_ssl_peer_verification => true
)

command=""

conn.shell(:powershell) do |shell|
    until command == "exit\n" do
        output = shell.run("-join($id,'PS ',$(whoami),'@',$env:computername,' ',$((gi $pwd).Name),'> ')")
        print(output.output.chomp)
        command = gets        
        output = shell.run(command) do |stdout, stderr|
            STDOUT.print stdout
            STDERR.print stderr
        end
    end    
    puts "Exiting with code #{output.exitcode}"
end
```
```
ruby examplewinrm.rb
```
### Using Signed SSL Cert
```
require 'winrm'

conn = WinRM::Connection.new( 
  endpoint: 'https://IP:5986/wsman',
  transport: :ssl,
  :client_cert: 'CERTFILE.cer',
  :client_key: 'CLIENTKEY.key',
  :no_ssl_peer_verification => true
)

command=""

conn.shell(:powershell) do |shell|
    until command == "exit\n" do
        output = shell.run("-join($id,'PS ',$(whoami),'@',$env:computername,' ',$((gi $pwd).Name),'> ')")
        print(output.output.chomp)
        command = gets        
        output = shell.run(command) do |stdout, stderr|
            STDOUT.print stdout
            STDERR.print stderr
        end
    end    
    puts "Exiting with code #{output.exitcode}"
end
```
```
ruby examplewinrm.rb
```

