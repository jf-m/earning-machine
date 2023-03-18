# earning-machine

Docker stack that runs the most profitable passive-income apps in one single docker-compose file.

With this project, you can start earning money doing nothing through a curated list of passive income applications.
You can use this project on any device that supports docker. This includes : Raspberry Pi, Synology NAS, a VPS, Windows, MacOS, Linux... 

# Table of content

- [Requirements](#1-requirements)
  + [Docker](#docker)
  + [Docker-Compose](#docker-compose)
- [Installation](#2-installation)
- [Configuration](#3-configuration)
	+ [Peer2Profit](#-peer2profit)
	+ [PacketStream](#-packetstream)
	+ [HoneyGain](#-honeygain)
	+ [EarnApp](#-earnapp)
	+ [Repocket](#-repocket)
	+ [TraffMonetizer](#-traffmonetizer)
	+ [Pawns](#-pawns)
	+ [Bitping](#-bitping)
- [Running the stack](#4-running-the-stack)
- [Support](#5-support)

-------------
# 1. Requirements

This project uses Docker and Docker-Compose **only** (no third party app installed on the host).


## Docker

Follow the steps to install Docker if you don't have it already.

The steps can be found here: https://docs.docker.com/get-docker/

For your convenience, here are the steps to install Docker on a Debian/Raspbian OS :

```
sudo apt-get update && sudo apt-get upgrade
curl -fsSL test.docker.com -o get-docker.sh && sh get-docker.sh
sudo usermod -aG docker docker_user
sudo usermod -aG docker ${USER}
groups ${USER}
sudo systemctl enable docker
sudo reboot
```

## Docker-Compose

Follow the steps to install Docker-Compose if you don't have it already.

The steps can be found here: https://docs.docker.com/compose/install/
For your convenience, here are the steps to install Docker-Compose on a Debian/Raspbian OS :

```
sudo apt-get install libffi-dev libssl-dev
sudo apt install python3-dev
sudo apt-get install -y python3 python3-pip
sudo pip3 install docker-compose
```

-------------
# 2. Installation

First, clone this repository.

Here are two different techniques

- Method 1: Download as Zip

On this webpage, click on the green button "<> Code" and then "Download ZIP".
Unzip the zip, and verify that you have a folder named `earning-machine` containing this repo.

- Method 2: Using git clone

The following command will create a folder `earning-machine` and clone the repository inside it.

```
git clone https://github.com/jf-m/earning-machine.git earning-machine
cd earning-machine
```

Once done, I recommend that you move the directory called `earning-machine` to somewhere safe on your device. Don't leave it in the `Downloads` folder, because you might delete it in the future.


-------------
# 3. Configuration

The following steps will guide you through the account creation and the configuration of the [`docker-compose.yml`](docker-compose.yml) file for each passive income application.

During these steps, you'll be required to open your copy of the [`docker-compose.yml`](docker-compose.yml) located in your `earning-machine` directory with a text editor such as `vim`, `sublime text`, `NotePad`, `TextEdit`. Then, follow the next steps and find/replace each "Variable" by your own value (email address, password, identification, ... it depends on the application).

## Extra explanations

These apps won't use much RAM/CPU, but should you need to narrow down these apps to the best ones only, each app is ranked using the following emojis:

- 🟩 High yield earnings
- 🟧 Medium yield earnings
- 🟫 Low yield earnings
- 🟥 Very low yield earnings

Feel free to remove the apps you do not want by simply commenting the relevant configuration part in the [`docker-compose.yml`](docker-compose.yml).

Please note that this rank is based on my experience using those apps in the UK (the earnings depends mostly on your location but also internet speed and other factors).
If you do not live in the UK, I recommend that you try them out first and review the earnings after a few weeks.

## 🟩 Peer2Profit

### Account creation

Create your account on the following website

[https://p2pr.me](https://p2pr.me/1669297549637f758d3c27b "https://p2pr.me")

### Update the docker-compose

In the [`docker-compose.yml`](docker-compose.yml), edit :

| Variable  | Description |
| --------- | -----|
| `YOUR_PEER2PROFIT_EMAIL_ADDRESS`  | Peer2Profit account address |


## 🟩 PacketStream

### Account creation

Create your account on the following website

[https://packetstream.io](https://packetstream.io/?psr=4XCY "https://packetstream.io")

### Update the docker-compose

In the [`docker-compose.yml`](docker-compose.yml), edit :

| Variable  | Description |
| --------- | -----|
| `YOUR_PACKETSTREAM_CID`  | PacketStream referral ID (4 characters), which can be found in your referral link, the last 4 characters https://packetstream.io/dashboard/referrals |

Note that if you changed the name of the folder in which the [`docker-compose.yml`](docker-compose.yml) is located (by default `earning-machine`, see section [1. Installation](#installation)), then edit the following:

| Variable  | Description |
| --------- | -----|
| `earning-machine_psclient_1` | Change this variable to `NAME_OF_FOLDER` followed by `_psclient_1` (remove any spaces that might be in the name of your folder) |


## 🟩 HoneyGain

### Account creation

Create your account on the following website

[https://r.honeygain.me](https://r.honeygain.me/JFMEI0ED48 "https://r.honeygain.me")

### Update the docker-compose

In the [`docker-compose.yml`](docker-compose.yml), edit :

| Variable  | Description |
| --------- | -----|
| `YOUR_HONEYGAIN_EMAIL_ADDRESS`  | HoneyGain account address |
| `YOUR_USER_HONEYGAIN_PASSWORD`  |   HoneyGain account password |


## 🟧 EarnApp

### Account creation

Create your account on the following website

[https://earnapp.com](https://earnapp.com/i/xt5f3gs "https://earnapp.com")

### Generate your Node id

Execute the following command :

```
docker run --privileged --rm -v /sys/fs/cgroup:/sys/fs/cgroup:ro --name earnapp fazalfarhan01/earnapp:lite /bin/bash -c "apt-get update && apt install -y systemctl && /download/earnapp install && cat /etc/earnapp/uuid"
```

This command will generate and output a node id with the following pattern : 
`sdk-node-xxxxxxxxxxxxxxxxxxxx`.

### Link your node id

Link your newly created node id to your account by following the steps here:

(Replace `YOUR_NODE_ID` with your node id)

https://earnapp.com/r/YOUR_NODE_ID

### Update the docker-compose

In the [`docker-compose.yml`](docker-compose.yml), edit :

| Variable  | Description |
| --------- | -----|
| `YOUR_EARNAPP_NODE_ID`  | EarnApp Node Id |


## 🟫 Repocket

### Account creation

Create your account on the following website

[https://link.repocket.co](https://link.repocket.co/JmtW "https://link.repocket.co")

### Update the docker-compose

In the [`docker-compose.yml`](docker-compose.yml), edit :

| Variable  | Description |
| --------- | -----|
| `YOUR_REPOCKET_EMAIL_ADDRESS`  | Repocket account address |
| `YOUR_REPOCKET_USER_PASSWORD`  | Repocket account password |


## 🟫 TraffMonetizer

### Account creation

Create your account on the following website

[https://traffmonetizer.com](https://traffmonetizer.com/?aff=809605 "https://traffmonetizer.com")

### Update the docker-compose

In the [`docker-compose.yml`](docker-compose.yml), edit :

| Variable  | Description |
| --------- | -----|
| `YOUR_TRAFFMONETIZER_TOKEN`  | TraffMonetizer token that can be found in the dashboard (https://app.traffmonetizer.com/dashboard) on the top left corner "Your application token" |


## 🟫 Pawns

### Account creation

Create your account on the following website

[https://pawns.app](https://pawns.app?r=1055724 "https://pawns.app")

### Update the docker-compose

In the [`docker-compose.yml`](docker-compose.yml), edit :

| Variable  | Description |
| --------- | -----|
| `YOUR_PAWNS_EMAIL_ADDRESS`  | Pawns account address |
| `YOUR_PAWNS_USER_PASSWORD`  | Pawns account password |


## 🟥 Bitping

### Account creation

Create your account on the following website

[https://app.bitping.com](https://app.bitping.com?r=t0MNBbDe "https://app.bitping.com")

### Generate configuration file

Execute the following command and follow the BitPing steps (enter your BitPing credentials) to generate a configuration file

`sudo docker run -it -v $(pwd)/data/bitping/:/root/.bitping bitping/bitping-node:latest`

When `Successfully logged in to Bitping` is displayed, you can safely kill the container with `CTRL+C` or `CMD+C`.

-------------
# 4. Running the stack

To run the stack and start earning money, execute the following command in this project directory (the folder `earning-machine`):

`docker-compose up -d`

-------------
# 5. Support

If you have any questions, feel free to open an issue here, I'll answer.

If you like this project, use the referral links provided on this README.md file to support it.

Alternatively, consider donating.

BTC: `bc1qpc022g22v36axp320nzdm962prnhue7jve05l8`
