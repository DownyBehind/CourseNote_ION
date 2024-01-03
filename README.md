# CourseNote_ION
How to Run ION node in Ubuntu

Linux : Ubutu 18.04LTS

Docker engine
```bash
sudo apt-get update

sudo apt-get install -y apt-transport-https ca-certificates curl software-properties-common

curl -fsSL --max-time 10 --retry 3 --retry-delay 3 --retry-max-time 60 https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

sudo apt-get install -y docker-ce
sudo systemctl enable docker
```

Docker compose
```bash
sudo curl -L --max-time 60 --retry 3 --retry-delay 3 --retry-max-time 100 "https://github.com/docker/compose/releases/download/v2.6.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

sudo chmod +x /usr/local/bin/docker-compose
```

Run

```bash
git clone https://github.com/decentralized-identity/ion.git
```

To run a testnet ION node

```bash
cd ./ion/docker
docker-compose -f docker-compose.yml -f docker-compose.testnet-override.yml up -d

```






## Error Handling

Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running?

1. kill docker service
```bash
sudo systemctl stop docker
sudo systemctl stop docker.socket
sudo systemctl stop containerd
```
  
2. docker restart
```bash
sudo systemctl start docker

```
