# Setup ARM32 Runner on ARM64 (v8)

## AWS VM

- Instance type: c7g.xlarge
- Graviton3

## Setup Docker and Start Docker

```bash
sudo apt update
sudo apt dist-upgrade
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh ./get-docker.sh
sudo usermod -aG docker $USER
sudo reboot
docker run -it --platform linux/arm/v7 arm32v7/debian:bullseye bash
```

## Check Environment

```bash
dpkg --print-architecture
ldd --version
uname -m
```

## Prepare GitHub Runner

```bash
apt-get -qq update
apt-get install libatomic1 curl sudo openjdk-11-jdk-headless
```

```bash
mkdir actions-runner && cd actions-runner
[ownload and extract]
RUNNER_ALLOW_RUNASROOT=1 ./config.sh --url https://github.com/bruestel/conscrypt --token xyz
RUNNER_ALLOW_RUNASROOT=1 ./run.sh
```

