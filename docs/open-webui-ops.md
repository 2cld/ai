[edit]()

## debug
Had open webui working through docker-wsl-cybertruck-cloudflare.  Was attempting to run a vm with VirtualBox when I began to have issues with external access.

debug open webui

- [https://ai.2cld.net/docs/](https://ai.2cld.net/docs/)

- [https://github.com/open-webui/open-webui#troubleshooting](https://github.com/open-webui/open-webui#troubleshooting)
- [https://docs.openwebui.com/troubleshooting/](https://docs.openwebui.com/troubleshooting/)
- Configure Ollama Host: Set the OLLAMA_HOST environment variable to 0.0.0.0. This tells Ollama to listen on all available network interfaces, enabling connections from external sources, including the Open WebUI.
- sudo ufw allow port/protocol sudo ufw deny port/protocol Replace port with the port number and protocol with TCP or UDP.
- 
## portainer
- https://localhost:9443/#!/auth
- tbd
## website
---
- Open webui
- [http://localhost:8080/](http://localhost:8080/) works on Cybertruck
- [http://172.25.17.150:8080/](http://172.25.17.150:8080/) works on Cybertruck
- [http://192.168.6.30:8080/](http://192.168.6.30:8080/) 500: Internal Error on Cybertruck
- [https://chat.bradnordyke.com/](https://chat.bradnordyke.com/) fails on Cybertruck
- []() works on Cybertruck
---
- ollama
- [http://localhost:11434/](http://localhost::11434/) works on Cybertruck
- [http://127.0.0.1:11434/](http://127.0.0.1:11434/) works on Cybertruck
- [http://172.25.17.150::11434/](http://172.25.17.150::11434/) Does NOT work on Cybertruck
- [http://192.168.6.30:11434/](http://192.168.6.30:11434/) works on Cybertruck


## logs
- [cfCyberTruck_PS_ConsoleHost_history.txt](./cfCyberTruck_PS_ConsoleHost_history.txt)
- [cfCyberTruck_wsl_ConsoleHost_history.txt](./cfCyberTruck_wsl_ConsoleHost_history.txt)
- [PowerShell History commands](https://stackoverflow.com/questions/44104043/how-can-i-see-the-command-history-across-all-powershell-sessions-in-windows-serv)
- [forwarding ports in WSL2 NAT](https://aalonso.dev/blog/2021/accessing-network-apps-running-inside-wsl2-from-other-devices-in-your-lan-1e1p)
- powershell
  ```powershell
  netsh interface portproxy add v4tov4 listenport=3000 listenaddress=0.0.0.0 connectport=3000 connectaddress=<the_wsl_ip>
  ```
- [Microsoft tcpview](https://learn.microsoft.com/en-us/sysinternals/downloads/tcpview)
- [Microsoft Find process listening on port in windows](https://woshub.com/which-program-listening-port-windows/#:~:text=You%20can%20use%20a%20PowerShell%20one-line%20command%20to,2%20UDP%20port%3A%20Get-Process%20-Id%20%28Get-NetUDPEndpoint%20-LocalPort%2053%29.OwningProcess)
- You can use a PowerShell one-line command to instantly get the name of the process listening on a specific port:
```
TCP port: Get-Process -Id (Get-NetTCPConnection -LocalPort 80).OwningProcess
UDP port: Get-Process -Id (Get-NetUDPEndpoint -LocalPort 53).OwningProcess
```
- [netsh-port-forwarding-from-local-port-to-local-port-not-working](https://stackoverflow.com/questions/24646165/netsh-port-forwarding-from-local-port-to-local-port-not-working)

---
## weblogs
A container's logs can be found in : /var/lib/docker/containers/<container id>/<container id>-json.log (if you use the default log format which is json)
```
ghadmin@Cybertruck:/mnt/c/Users/ghadmin$ sudo tail /var/lib/docker/containers/0a3f081ea4f65bf0504f2b0be862811bf74ab3a5fbcb42ea6456afccf90c793c/0a3f081ea4f65bf0504f2b0be862811bf74ab3a5fbcb42ea6456afccf90c793c-json.log
{"log":"INFO:     172.25.16.1:57588 - \"GET /api/v1/functions/ HTTP/1.1\" 200 OK\n","stream":"stdout","time":"2024-08-27T02:00:14.019170638Z"}
{"log":"INFO:     172.25.16.1:57587 - \"GET /api/v1/tools/ HTTP/1.1\" 200 OK\n","stream":"stdout","time":"2024-08-27T02:00:14.019291504Z"}
{"log":"INFO:     172.25.16.1:57582 - \"GET /api/models HTTP/1.1\" 200 OK\n","stream":"stdout","time":"2024-08-27T02:00:14.022128485Z"}
{"log":"INFO:     172.25.16.1:57586 - \"GET /api/v1/prompts/ HTTP/1.1\" 200 OK\n","stream":"stdout","time":"2024-08-27T02:00:14.023702181Z"}
{"log":"INFO:     172.25.16.1:57588 - \"GET /api/v1/chats/tags/all HTTP/1.1\" 200 OK\n","stream":"stdout","time":"2024-08-27T02:00:14.038650157Z"}
{"log":"INFO:     172.25.16.1:57586 - \"GET /ollama/api/version HTTP/1.1\" 200 OK\n","stream":"stdout","time":"2024-08-27T02:00:14.074402072Z"}
{"log":"INFO:     172.25.16.1:57588 - \"POST /api/v1/chats/tags HTTP/1.1\" 200 OK\n","stream":"stdout","time":"2024-08-27T02:00:14.091514192Z"}
{"log":"INFO:     172.25.16.1:57586 - \"GET /static/favicon.png HTTP/1.1\" 304 Not Modified\n","stream":"stdout","time":"2024-08-27T02:00:14.098856148Z"}
{"log":"INFO:     172.25.16.1:57582 - \"GET /api/v1/users/user/settings HTTP/1.1\" 200 OK\n","stream":"stdout","time":"2024-08-27T02:00:14.105445297Z"}
{"log":"INFO:     172.25.16.1:57586 - \"GET /api/v1/chats/?page=1 HTTP/1.1\" 200 OK\n","stream":"stdout","time":"2024-08-27T02:00:14.114447368Z"}
```
---
```
ghadmin@Cybertruck:/mnt/c/Users/ghadmin$ sudo grep " 500 " /var/lib/docker/containers/0a3f081ea4f65bf0504f2b0be862811bf74ab3a5fbcb42ea6456afccf90c793c/0a3f081ea4f65bf0504f2b0be862811bf74ab3a5fbcb42ea6456afccf90c793c-json.log
{"log":"INFO:     127.0.0.1:47662 - \"GET /openai/models/0 HTTP/1.1\" 500 Internal Server Error\n","stream":"stdout","time":"2024-08-10T18:39:41.584508432Z"}
{"log":"INFO:     127.0.0.1:39514 - \"GET /openai/models/0 HTTP/1.1\" 500 Internal Server Error\n","stream":"stdout","time":"2024-08-10T19:15:15.070286437Z"}
{"log":"INFO:     24.149.3.190:0 - \"GET /openai/models/0 HTTP/1.1\" 500 Internal Server Error\n","stream":"stdout","time":"2024-08-14T15:40:54.450554Z"}
{"log":"INFO:     172.25.16.1:52353 - \"GET /openai/models/0 HTTP/1.1\" 500 Internal Server Error\n","stream":"stdout","time":"2024-08-26T14:31:16.760185044Z"}
{"log":"INFO:     172.25.16.1:52358 - \"GET /openai/models/0 HTTP/1.1\" 500 Internal Server Error\n","stream":"stdout","time":"2024-08-26T14:31:52.595721362Z"}
{"log":"INFO:     127.0.0.1:54592 - \"GET /openai/models/0 HTTP/1.1\" 500 Internal Server Error\n","stream":"stdout","time":"2024-08-26T15:11:09.154371757Z"}
{"log":"INFO:     172.25.16.1:52774 - \"GET /openai/models/0 HTTP/1.1\" 500 Internal Server Error\n","stream":"stdout","time":"2024-08-26T15:19:21.322374321Z"}
g
```
