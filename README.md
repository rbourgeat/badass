# badass

## Setup Ubuntu

```bash
sudo apt-get update
sudo add-apt-repository -y ppa:gns3/ppa
sudo apt-get install -y ca-certificates curl gnupg lsb-release
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
sudo apt-get install -y docker-ce docker-ce-cli containerd.io docker-compose-plugin gns3-gui gns3-server
sudo usermod -aG kvm,libvirt,docker,ubridge,wireshark $USER
gns3
```

## Part 1

```bash
cd P1
docker build -t host_rbourgea -f _rbourgea-1_host .
docker build -t routeur_rbourgea -f _rbourgea-2 .
```

Go to gns3 `Edit > Preference > Docker > Docker containers`.

Click `New` and create 2 Docker templates with `host_rbourgea:latest` and `routeur_rbourgea:latest` images.

> Info: set more than 1 adapter for the docker templates `routeur_rbourgea`.

Go to gns3 `File > Import portable project` and select `P1.gns3project`.

## Part 2

Go to gns3 `File > Import portable project` and select `P2.gns3project`.

> Info: `brctl showmacs br0` use `/usr/sbin/brctl showmacs br0` instead.

## Part 3

Go to gns3 `File > Import portable project` and select `P3.gns3project`.
