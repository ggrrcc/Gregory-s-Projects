sudo apt install openssh-server

sudo systemctl status ssh

optional if not active: sudo systemctl start ssh

sudo systemctl enable ssh



## firewall

sudo ufw allow ssh

if doesn't work:

sudo apt install ufw
sudo ufw enable
sudo ufw allow ssh
sudo ufw allow 2222/tcp
sudo ufw enable

## configure

optional: sudo nano /etc/ssh/sshd_config
uncomment the port and add 2222

sudo systemctl restart ssh

## Do ip setup

Run ip a (and get local ip)

Run curl ifconfig.me (and get external ip)

## Connect from other comp
On other computer run ssh-keygen

From WSL or bash copy public key
ssh-copy-id -p 2222 user@IP

Then ssh -p 2222 user@IP





# SSH Setup on Debian

This guide walks you through the process of setting up an SSH server on a Debian machine so that you can securely connect to it remotely.

## 1. Install OpenSSH Server

First, install the OpenSSH server package:

```bash
sudo apt install openssh-server
```

After installation, check if the SSH service is running:

```bash
sudo systemctl status ssh
```

If the service is not active, start it:

```bash
sudo systemctl start ssh
```

Enable SSH to start on boot:

```bash
sudo systemctl enable ssh
```

## 2. Firewall Configuration

If you have a firewall enabled, allow SSH traffic. If ufw (Uncomplicated Firewall) is not installed, you can install it:

```bash
sudo apt install ufw
```

Then, allow SSH through the firewall:

```bash
sudo ufw allow ssh
```

If you're using a custom port (e.g., 2222), also allow that port:

```bash
sudo ufw allow 2222/tcp
```

Finally, enable the firewall:

```bash
sudo ufw enable
```

You can check the status of the firewall with:

```bash
sudo ufw status
```

## 3. Configure SSH (Optional)

You can optionally configure SSH settings, such as changing the default port or other security-related settings.

To edit the SSH configuration file, open it with a text editor:

```bash
sudo nano /etc/ssh/sshd_config
```

Uncomment the Port line and change it to 2222 (or any other port you prefer):

```bash
Port 2222
```

Save the file and restart the SSH service to apply the changes:

```bash
sudo systemctl restart ssh
```

## 4. Find Your IP Address

To connect from another computer, you'll need to know your Debian machine's IP address.
Local IP:

Run the following command to find your local IP address (on the same network):

```bash
ip a
```

Look for the inet address under your network interface (usually eth0 or wlan0).
External IP (for remote connections):

If you want to connect over the internet, you will need your public IP. Run the following command to find your external IP:

```bash
curl ifconfig.me
```

## 5. Connect from Another Computer

On the other computer, generate an SSH key pair:

```bash
ssh-keygen
```

If you're using WSL or Git Bash, copy the generated public key to your Debian server:

```bash
ssh-copy-id -p 2222 user@IP
```

Replace user with your Debian username and IP with the local or external IP of your Debian machine.

Now you can SSH into your Debian machine using the following command:

```bash
ssh -p 2222 user@IP
```

You should now be able to connect to your Debian machine securely using SSH.

Note: If you are connecting over the internet (external IP), you may need to set up port forwarding on your router to forward port 2222 (or whichever port you chose) to your Debian machine.

## 6. Other stuff

### Turn on if pc gets power

This is in UEFI

### Turn off suspend if connected by ssh