# Gateways

I have setup too many beaglebone and raspberries for IoT gateways.  I did have a
nice check list of each step to take, then someone showed me [ansible](https://www.ansible.com).

So working towards all of that automation.

## Running

I don't install ansible on my machine, but instead run it inside a Docker container. 
(I used to use a vagrant machine, so I keep the Vagrant file around.)

### Via Docker

1. Build: `docker build -t local/ansible-playbook:latest .`
2. Run with: `ansible_helper`
