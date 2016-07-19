- https://www.digitalocean.com/community/tutorials/how-to-create-a-high-availability-setup-with-corosync-pacemaker-and-floating-ips-on-ubuntu-14-04

- Network configuration: https://wiki.debian.org/NetworkConfiguration#Multiple_IP_addresses_on_One_Interface

## Setup

### Create Cluster Authorization Keys

On the primary server, generates key

```
$ sudo corosync-keygen
```

Then copy the authkey to the secondary server

```
$ sudo scp /etc/corosync/authkey vagrant@192.168.5.101:/tmp
```

On secondary server, move the authkey to the proper location

```
$ sudo mv /tmp/authkey /etc/corosync
$ sudo chown root: /etc/corosync/authkey
$ sudo chmod 400 /etc/corosync/authkey
```


## Useful commands

- Check cluster status

```
$ sudo crm status
```

- Periodically check cluster
```
$ sudo crm_mon
```
