### Swaping memory

- Check System Monitor: see the Memory (with 3.9GB) and Swap (normally with 2GB)
- Check the link to see how is the maximum memory can swap: https://help.ubuntu.com/community/SwapFaq
- Can swap maximum 8GB

- Create the Swap File:
We will create a 8GB file (/mnt/8GiB.swap) to use as swap:
```
sudo fallocate -l 8g /mnt/8GB.swap
```
fallocate size suffixes: g = Giga, m = Mega, etc. (See man fallocate).

We need to set the swap file permissions to 600 to prevent other users from being able to read potentially sensitive information from the swap file.

sudo chmod 600 /mnt/8GB.swap
Format the file as swap:
```
sudo mkswap /mnt/8GB.swap
```
Enable use of Swap File
```
sudo swapon /mnt/8GB.swap
```
Enable Swap File at Bootup
Add the swap file details to /etc/fstab so it will be available at bootup:
```
echo '/mnt/1GiB.swap swap swap defaults 0 0' | sudo tee -a /etc/fstab
```

- You can use the following website to get the swap manually back into RAM: https://help.ubuntu.com/community/SwapFaq

