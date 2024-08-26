[edit](https://github.com/2cld/ai/edit/main/docs/README.md)

# ai/docs
- [nginx-truenas.md](./nginx-truenas)
- [nodejs-test.md](./nodejs-test)
- [open-webui-install.md](./open-webui-install)

## wip
- https://github.com/run-llama/llama_parse
- 

## working external through cloudflare [https://netstack.org/docs/wan/cloudflare/](https://netstack.org/docs/wan/cloudflare/)
- [https://chat.bradnordyke.com](https://chat.bradnordyke.com) - ollama open-webui
- [https://home.bradnordyke.com](https://home.bradnordyke.com) - homer
- [https://casa.bradnordyke.com](https://casa.bradnordyke.com) - casaos
  
## working need wsl route to local wsl / docker
- [local web only http://192.168.6.30:8080/](http://192.168.6.30:8080/)
- [local web only http://192.168.6.30:11434/](http://192.168.6.30:11434/)
- powershell PS C:\WINDOWS\system32> netsh interface portproxy show all
```
Listen on ipv4:             Connect to ipv4:

Address         Port        Address         Port
--------------- ----------  --------------- ----------
192.168.6.30    8080        172.25.17.150   8080
192.168.6.30    20200       172.25.17.150   80
192.168.6.30    8090        172.25.17.150   8090
192.168.6.30    11434       127.0.0.1       11434
```

## local wsl / docker
- [local web only http://172.25.17.150:8080/](http://172.25.17.150:8080/)
- [local web only http://172.25.17.150:11434/](http://172.25.17.150:11434/)

### works on local
- [local web only http://localhost:11434/](http://localhost:11434/) - olama must be running under wsl
```
ghadmin@Cybertruck:/mnt/c/WINDOWS/system32$ pgrep ollama
232
ghadmin@Cybertruck:/mnt/c/WINDOWS/system32$
```
- [local web only http://localhost:8080/](http://localhost:8080/) - docker open-webui must be running under wsl
```
ghadmin@Cybertruck:/mnt/c/WINDOWS/system32$ sudo docker ps
[sudo] password for ghadmin:
CONTAINER ID   IMAGE                                COMMAND           CREATED      STATUS                   PORTS     NAMES
0a3f081ea4f6   ghcr.io/open-webui/open-webui:main   "bash start.sh"   2 days ago   Up 2 minutes (healthy)             open-webui
```
- monitor nvidia GPU
```
ghadmin@Cybertruck:/mnt/c/WINDOWS/system32$ watch -n 0.5 nvidia-smi
```
## Restart Refernce
- nvidia monitor
```
ghadmin@Cybertruck:/mnt/c/WINDOWS/system32$ watch -n 0.5 nvidia-smi
```
- restart existing image
```
ghadmin@Cybertruck:/mnt/c/Users/ghadmin$ sudo docker run -d --network=host  -v open-webui:/app/backend/data -e OLLAMA_BASE_URL=http://127.0.0.1:11434 40
86dd959bc608fe5a17aa2b6cfeb52232e9c4cfdab1cffff12ff75a664a89fb0f
ghadmin@Cybertruck:/mnt/c/Users/ghadmin$ sudo docker image list
REPOSITORY                      TAG       IMAGE ID       CREATED      SIZE
ghcr.io/open-webui/open-webui   main      40b61f294e78   8 days ago   3.89GB
ghadmin@Cybertruck:/mnt/c/Users/ghadmin$
```

### update ref
- How to tell if model is in gpu [faq link](https://github.com/ollama/ollama/blob/main/docs/faq.md#how-can-i-tell-if-my-model-was-loaded-onto-the-gpu)
- where ollama keeps data [youtube](https://youtu.be/6bF1uCHTFyk) and [issue](https://github.com/ollama/ollama/issues/1836)
  - windows C:\Users*****\AppData\Local\Packages\CanonicalGroupLimited.Ubuntu_79*****gsc\LocalState\ext4.vhdx
  - linux \wsl.localhost\Ubuntu\usr\share\ollama.ollama\models
- You might want to [from this issue](https://github.com/ollama/ollama/issues/6301)
```
sudo docker rm -f ollama-webui
```
- repull
```
sudo docker pull ghcr.io/ollama-webui/ollama-webui:main
```
- Then run
```
sudo docker run -d -p 8080:8080 --add-host=host.docker.internal:host-gateway -v ollama-webui:/app/backend/data --name ollama-webui --restart always ghcr.io/ollama-webui/ollama-webui:main
```
- network issues in wsl 
  - https://stackoverflow.com/questions/61002681/connecting-to-wsl2-server-via-local-network
  - https://docs.docker.com/guides/workshop/02_our_app/#:~:text=Start%20an%20app%20container%201%20Run%20your%20container,mark%20items%20as%20complete%20and%20remove%20them.%20
  - https://docs.openwebui.com/getting-started/
  - https://docs.docker.com/language/golang/run-containers/
  - https://github.com/open-webui/open-webui/discussions/743
  - https://github.com/open-webui/open-webui/discussions/770
## Install Reference
- [Networkchuck - host ALL your AI locally](https://academy.networkchuck.com/products/youtube-videos/categories/2155282450/posts/2177513911)
- ollama FAQ [https://github.com/ollama/ollama/blob/main/docs/faq.md](https://github.com/ollama/ollama/blob/main/docs/faq.md)
- install wsl Ubuntu-22.04 [wsl install help](https://learn.microsoft.com/en-us/windows/wsl/install)
```
 wsl --install
 wsl --list --online <to see a list of available distros and run>
 wsl --install -d <DistroName> To change the distribution installed, enter: wsl --install -d <Distribution Name>.
 wsl --install -d Ubuntu-22.04
 wsl -d <DistributionName> To run a specific wsl distribution from within PowerShell or Windows Command Prompt without changing your default distribution, use the command: wsl -d <DistributionName>
 wsl -s <DistributionName> or wsl --set-default <DistributionName> To set the default Linux distribution used with the wsl command, enter: wsl -s <DistributionName> or wsl --set-default <DistributionName>
```
- ollama [Linux install script](https://ollama.com/download/linux)
- verify Ubuntu-22.04
```
ghadmin@Cybertruck:~$ cat /etc/*release
```
- install ollama
```
ghadmin@Cybertruck:~$ sudo apt update
ghadmin@Cybertruck:~$ sudo apt upgrade -y
ghadmin@Cybertruck:~$ curl -fsSL https://ollama.com/install.sh | sh
```
- pull llama2
```
ghadmin@Cybertruck:~$ ollama pull llama2
```
- monitor nvidia gpu
```
ghadmin@Cybertruck:~$ watch -n 0.5 nvidia-smi
```
## open-webui
- https://docs.openwebui.com/tutorial-development/
- intall docker open-webui
- keyring for packages
```
ghadmin@Cybertruck:~$ sudo apt-get update
ghadmin@Cybertruck:~$ sudo apt-get install ca-certificates curl
ghadmin@Cybertruck:~$ sudo install -m 0755 -d /etc/apt/keyrings
ghadmin@Cybertruck:~$ sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
ghadmin@Cybertruck:~$ sudo chmod a+r /etc/apt/keyrings/docker.asc
ghadmin@Cybertruck:~$ echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
$(. /etc/os-release && echo "$VERSION_CODENAME") stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
- docker install
```
ghadmin@Cybertruck:~$ sudo apt-get update
ghadmin@Cybertruck:~$ sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```
- open-webui docker
```
ghadmin@Cybertruck:~$ sudo docker run -d --network=host -v open-webui:/app/backend/data -e OLLAMA_BASE_URL=http://127.0.0.1:11434 --name open-webui --restart always ghcr.io/open-webui/open-webui:main
```
- docker status
```
ghadmin@Cybertruck:~$ sudo docker ps
```

### External Access
- https://stackoverflow.com/questions/64513964/wsl-2-which-ports-are-automatically-forwarded
- portforward 8080 to 8080 wsl docker
```
PS C:\WINDOWS\system32> netsh interface portproxy show all
PS C:\WINDOWS\system32> netsh interface portproxy show v4tov4
PS C:\WINDOWS\system32> netsh interface portproxy show all
PS C:\WINDOWS\system32> netsh interface portproxy add v4tov4 listenport=11434 listenaddress=192.168.6.30 connectport=11434 connectaddress=127.0.0.1

Listen on ipv4:             Connect to ipv4:

Address         Port        Address         Port
--------------- ----------  --------------- ----------
193.168.6.30    11434       127.0.0.1       11434


PS C:\WINDOWS\system32> netsh interface portproxy add v4tov4 listenport=11434 listenaddress=192.168.6.30 connectport=8080 connectaddress=127.0.0.1

PS C:\WINDOWS\system32> netsh interface portproxy show all

Listen on ipv4:             Connect to ipv4:

Address         Port        Address         Port
--------------- ----------  --------------- ----------
192.168.6.30    11434       127.0.0.1       8080

PS C:\WINDOWS\system32> netsh interface portproxy add v4tov4 listenport=8080 listenaddress=192.168.6.30 connectport=8080 connectaddress=127.0.0.1

PS C:\WINDOWS\system32> netsh interface portproxy show all

Listen on ipv4:             Connect to ipv4:

Address         Port        Address         Port
--------------- ----------  --------------- ----------
192.168.6.30    11434       127.0.0.1       8080
192.168.6.30    8080        127.0.0.1       8080

PS C:\WINDOWS\system32> netsh interface portproxy add v4tov4 listenport=11434 listenaddress=192.168.6.30 connectport=11434 connectaddress=127.0.0.1

PS C:\WINDOWS\system32> netsh interface portproxy show all

Listen on ipv4:             Connect to ipv4:

Address         Port        Address         Port
--------------- ----------  --------------- ----------
192.168.6.30    11434       127.0.0.1       11434
192.168.6.30    8080        127.0.0.1       8080

PS C:\WINDOWS\system32>
```
- tbd

### casaos on wsl install
- ghadmin@Cybertruck:/mnt/c/Users/ghadmin/casaos$ curl -fsSL get.casaos.io/install.sh | sudo bash
- ghadmin@Cybertruck:/mnt/c/Users/ghadmin/casaos$ sudo ufw allow 8080
- PS C:\WINDOWS\system32> netsh interface portproxy add v4tov4 listenport=20200 listenaddress=192.168.6.30 connectport=80 connectaddress=172.25.17.150
- PS C:\WINDOWS\system32> netsh interface portproxy show all
