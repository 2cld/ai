[edit]()

# ai/docs

### works on local
- [local web only http://localhost:8080/](http://localhost:8080/)
- [local web only http://localhost:11434/](http://localhost:11434/)

## not working need wsl route to local wsl / docker
- [local web only http://192.168.6.30:8080/](http://192.168.6.30:8080/)
- [local web only http://192.168.6.30:11434/](http://192.168.6.30:11434/)

## Install Reference
- [Networkchuck - host ALL your AI locally](https://academy.networkchuck.com/products/youtube-videos/categories/2155282450/posts/2177513911)
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
PS C:\WINDOWS\system32> netsh interface portproxy set v4tov4 listenport=8080 listenaddress=0.0.0.0 connectport=8080 connectaddress=$(wsl hostname -I)
PS C:\WINDOWS\system32> netsh interface portproxy show v4tov4
Listen on ipv4:             Connect to ipv4:

Address         Port        Address         Port
--------------- ----------  --------------- ----------
0.0.0.0         8080        172.25.17.150 172.17.0.1  8080
```
- tbd
