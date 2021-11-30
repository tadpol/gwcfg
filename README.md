# Gateways

I have setup too many beaglebone and raspberries for IoT gateways.  I did have a
nice check list of each step to take, then someone showed me [ansible](https://www.ansible.com).

So working towards all of that automation.

## Running

I don't install ansible on my machine, but instead run it inside a Docker container.
(I used to use a vagrant machine, so I keep the Vagrant file around.)

Things go a lot smoother if you have put public keys in place.

```sh
ssh-copy-id -i ~/.ssh/id_rsa $NODES
```

### Via Docker

1. Build: `docker build -t local/ansible-playbook:latest .`
2. Run with: `ansible_helper`

## Headless Pi

Currently, if you want to setup a Raspberry Pi without keyboard or monitor do the following:

- Copy image to SD Card
- Mount it
- Add empty file to the SD Card named `ssh`
- Add a file named `wpa_supplicant.conf` with the following:

```cfg
country=US
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1

network={
scan_ssid=1
ssid="$your_wifi_ssid"
psk="$your_wifi_password"
}
```

- There appears to be support for a `firstuse.sh` script, but it also appears to be undocumented.
- Eject SD Card from computer
- Insert to Raspberry PI
- Boot device
- Wait a minute or three
- `ssh pi@raspberrypi.local.`; default password
- `sudo raspi-config`
- Change hostname and passwords and resize the filesystem
- Reboot

### Or using Raspberry Pi Imager

1. Press `⌘⇧X` (or `⌃⇧X` if not Mac) to access the advanced options.
2. Check ssh box and WiFi setup and change hostname
3. Write image
