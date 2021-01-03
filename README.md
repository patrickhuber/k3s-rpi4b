# k3s-rpi4b

## OS

Install ubuntu 20.04 by following instructions here: https://linuxhint.com/install_ubuntu_ssh_headless_raspberry_pi_4/

## k3s

1. setup ssh keys on each machine
2. add `cgroup_enable=cpuset cgroup_enable=memory cgroup_memory=1` to /boot/firmware/cmdline.txt
3. reboot
4. install k3sup
5. use `sudo hostnamectl set-hostname $HOSTNAME` to set a unique hostname for each node, reboot
6. for the first node run `k3sup install --cluster --ip $IP --user ubuntu --merge --local-path ~/.kube/config --context rpi4` where $IP is set to the ip of the node
7. for each additional master run `k3sup join --server --ip "$NODE1" --user ubuntu --server-user ubuntu --server-ip "$NODEN"` where $NODE1 is the first node and $NODEN is the Nth node
