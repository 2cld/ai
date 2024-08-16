
- This is commandlines in history of open-webui-install on Cybertruck under wsl
- just after wsl2 setup in ps check version
```
ghadmin@Cybertruck:/mnt/c/Users/ghadmin$ cat /etc/*version
ghadmin@Cybertruck:/mnt/c/Users/ghadmin$ cat /etc/*release
```
- tbd
```
```
- tbd
```
```
- tbd
```
```
- tbd
```
```
- tbd
```
```
- tbd
```
```
- history
```
ghadmin@Cybertruck:/mnt/c/Users/ghadmin$ history
    1  exit
    2  cd ~
    3  cat /etc/*versions
    4  cat /etc/*version
    5  cat /etc/*release
    6  sudo apt update
    7  sudo apt upgrade -y
    8  curl -fsSL https://ollama.com/install.sh | sh
    9  ollama pull llama2
   10  ollama run llama2
   11  # Add Docker's official GPG key:
   12  sudo apt-get update
   13  echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
   14  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
   15  sudo apt-get update
   16  sudo apt-get install ca-certificates curl
   17  sudo install -m 0755 -d /etc/apt/keyrings
   18  sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
   19  sudo chmod a+r /etc/apt/keyrings/docker.asc
   20  echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
   21  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
   22  sudo apt-get update
   23  sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
   24  docker run -d --network=host -v open-webui:/app/backend/data -e OLLAMA_BASE_URL=http://127.0.0.1:11434 --name open-webui --restart always ghcr.io/open-webui/open-webui:main
   25  docker --status
   26  docker ps
   27  sudo docker ps
   28  sudo docker run -d --network=host -v open-webui:/app/backend/data -e OLLAMA_BASE_URL=http://127.0.0.1:11434 --name open-webui --restart always ghcr.io/open-webui/open-webui:main
   29  ip a
   30  docker container ls
   31  suso docker container ls
   32  sudo docker container ls
   33  docker stop open-webui
   34  sudo docker stop open-webui
   35  sudo docker container ls
   36  exit
   37  cd ~
   38  sudo docker run -d --network=host -v open-webui:/app/backend/data -e OLLAMA_BASE_URL=http://127.0.0.1:11434 --name open-webui --restart always ghcr.io/open-webui/open-webui:main
   39  sudo docker ps
   40  sudo docker ls
   41  sudo docker --help
   42  docker images
   43  sudo docker images
   44  sudo docker run 40
   45  ollama
   46  ollama serve
   47  ollama show
   48  ollama ps
   49  ollama list
   50  ollama run llama2
   51  exit
   52  docker ps
   53  sudo docker run 40
   54  ollama list
   55  sudo docker images
   56  sudo docker run 40
   57  echo $OLLAMA_API_BASE_URL
   58  echo OLLAMA_API_BASE_URL
   59  echo "$OLLAMA_API_BASE_URL"
   60  var
   61  env
   62  ollama
   63  ollama ps
   64  ollama list
   65  ollama serve
   66  ollama run llama2
   67  watch -n 0.5 nvidia-smi
   68  ollama
   69  ollama list
   70  ollama ps
   71  pgrep ollama
   72  kill 229
   73  sudo kill 229
   74  pgrep ollama
   75  ollama ps
   76  sudo kill 851
   77  ollama ps
   78  pgrep ollama
   79  docker ps
   80  sudo docker ps
   81  docker
   82  docker ps
   83  sudo docker ps
   84  cd ~
   85  exit
   86  docker ps
   87  sudo docker ps
   88  pgrep ollama
   89  netsh interface portproxy add v4tov4 listenport=11434 listenaddress=0.0.0.0 connectport=11434 connectaddress=IP_ADDRESS_HERE
   90  netsh interface portproxy add v4tov4 listenport=11434 listenaddress=0.0.0.0 connectport=11434 connectaddress=172.25.17.150
   91  ufw allow 8080
   92  sudo ufw allow 8080
   93  sudo ufw allow 11434
   94  npm -v
   95  exit
   96  watch -n 0.5 nvidia-smi
   97  exit
   98  pwd
   99  ls
  100  mkdir casaos
  101  cd casaos/
  102  curl -fsSL get.casaos.io/install.sh | sudo bash
  103  sudo docker ps
  104  ip a
  105  exit
  106  pgrep ollama
  107  watch -n 0.5 nvidia-smi
  108  ollama list
  109  ollama --help
  110  ollama pull ollama3_5
  111  ollama pull ollama3.5
  112  ollama pull ollama3
  113  ollama pull llama3_5
  114  ollama pull llama3.5
  115  ollama pull --help
  116  ollama run llama3.1:8b
  117  watch -n 0.5 nvidia-smi
  118  ollama run codellama
  119  ip a
  120  cat /etc/wsl.conf
  121  npm -v
  122  ping 172.25.17.150
  123  netsh interface portproxy show all
  124  netstat -help
  125  docker ps
  126  sudo docker ps
  127  sudo apt install net-tools
  128  netstat -npl|grep 11434
  129  systemctl edit ollama.service
  130  sudo systemctl edit ollama.service
  131  sudo docker ps
  132  sudo systemctl edit ollama.service
  133  exit
  134  sudo docker ps
  135  sudo ufw allow 11434
  136  ip a
  137  sudo docker exec -it open-webui /bin/bash
  138  sudo docker ps
  139  sudo docker stop open-webui
  140  sudo docker ps
  141  sudo docker list
  142  sudo docker ==help
  143  sudo docker --help
  144  sudo docker images
  145  ip addr
  146  sudo docker run -d --network=host -v open-webui:/app/backend/data -e OLLAMA_BASE_URL=http://127.0.0.1:11434 --name open-webui --restart always ghcr.io/open-webui/open-webui:main
  147  docker image
  148  docker image ls
  149  sudo docker image ls
  150  sudo docker run -dp 127.0.0.1:8080:8080 open-webui
  151  sudo docker run -dp 127.0.0.1:8080:8080 40
  152  sudo docker ps
  153  ip addr
  154  sudo docker stop 86
  155  sudo docker ps
  156  sudo docker run -dp 172.25.17.150:8080:8080 40
  157  sudo docker ps
  158  sudo docker stop 43
  159  sudo docker ps
  160  sudo docker run  40
  161  sudo docker run  -dp localhost:8080 40
  162  sudo docker run  -dp 8080:8080 40
  163  sudo docker ps
  164  ls
  165  ls /usr/share/ollama/.ollama/models/
  166  ls /usr/share/ollama/.ollama/models/blobs/
  167  ls /usr/share/ollama/.ollama/models/manifests/
  168  ls /usr/share/ollama/.ollama/models/blobs/ -alu
  169  ollama -v
  170  ollama list
  171  ollama run llama3.1
  172  sudo docker -version
  173  sudo docker -v
  174  history
```
