# frps
## Install FRP on your EC2 instance
~~~bash
wget https://github.com/fatedier/frp/releases/download/v0.49.0/frp_0.49.0_linux_amd64.tar.gz
~~~

<img width="982" alt="Screenshot 2025-03-24 at 12 47 01 AM" src="https://github.com/user-attachments/assets/8e9b9715-2ca0-4cec-873e-29bf75105c7b" />

## Extract the downloaded FRP archive:
~~~bash
tar -xvzf frp_0.49.0_linux_amd64.tar.gz
cd frp_0.49.0_linux_amd64
~~~

Move the binaries to a system path
~~~bash
sudo mv frps /usr/local/bin/
sudo mv frpc /usr/local/bin/
~~~
## Configure FRP

### Server Configuration
~~~bash
sudo mkdir -p /etc/frp
~~~
##Create the FRP server configuration file
~~~bash
sudo nano /etc/frp/frps.ini
~~~
### Example configuration for the server:
~~~bash
[common]
bind_port = 7000
vhost_http_port = 8080
vhost_https_port = 443
~~~
# Client Configuration (frpc)

## 1. Create the client configuration file:
~~~bash
nano frpc.ini
~~~
## 2. In frpc.ini file put this Example :
~~~bash
[common]
server_addr = your-ec2-public-ip
server_port = 7000

[web]
type = tcp
local_ip = 127.0.0.1
local_port = 80
remote_port = 8080
~~~

<img width="299" alt="Screenshot 2025-03-24 at 12 54 32 AM" src="https://github.com/user-attachments/assets/ce7d7027-3e37-42b8-825d-4f984a807171" />

# Start the FRP Server (frps)
## 1. Start the server in the background:
~~~bash
sudo frps -c /etc/frp/frps.ini &
~~~
<img width="656" alt="Screenshot 2025-03-24 at 12 48 27 AM" src="https://github.com/user-attachments/assets/39fed422-9567-4ca5-bca9-7a212ebf9ac9" />

## 2. To make FRP run as a service on startup, you can create a systemd service file:
~~~bash
sudo nano /etc/systemd/system/frps.service
~~~

