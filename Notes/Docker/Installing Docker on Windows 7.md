# Docker on Windows 7

I found an article which said Docker Toolbox was the best way to do this, however github says Docker toolbox is now deprecated and to user (Docker Desktop)[https://www.docker.com/products/docker-desktop] instead.

Docker Desktop errors when trying to install it on Windows 7 Home Premium 

Install Docker with Chocolatey 

`choco install -y docker`
`choco install -y docker-machine`
Docker machine is a tool that  lets you install Docker Engine on virtual hosts.
`choco install -y docker-machine-vmwareworkstation`
Vmworkstation is a Hypervisor. Hypervisors create and run virtual machines.

Create a VMware Docker Machine called default
`docker-machine --native-ssh create -d vmwareworkstation default
`

to delete the Docker Machine
`docker-machine rm -f default`

This errored for me 

(default) Waiting for VM to come online...
Error creating machine: Error in driver during machine creation: Machine didn't return an IP after 120 seconds, aborting
You can further specify your shell with either 'cmd' or 'powershell' with the --shell flag.

I think this error is because vmware isn't installed on this pc. 

`vmware --version` says command not found.

