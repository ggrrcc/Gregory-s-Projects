## Step 1: Turn off Swap

```bash
sudo swapoff -a
```

## Step 2: Resize the Swap File

Remove the existing swap file:

```bash
sudo rm /swapfile
```

Create a new swap file with the desired size (e.g., 48GB):

```bash
sudo fallocate -l 48G /swapfile
```

If fallocate doesn’t work, use:

```bash
sudo dd if=/dev/zero of=/swapfile bs=1M count=4096
```

Set the correct permissions:

```bash
sudo chmod 600 /swapfile
```

Format it as swap:

```bash
sudo mkswap /swapfile
```

Enable the swap:

```bash
sudo swapon /swapfile
```

Make it permanent by adding this line to /etc/fstab:

```bash
echo '/swapfile none swap sw 0 0' | sudo tee -a /etc/fstab
```

Verify swap is active:

```bash
free -h
```