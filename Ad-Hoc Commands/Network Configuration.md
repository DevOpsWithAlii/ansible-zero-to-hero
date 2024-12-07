# 💻 Network Configuration

### 1. Assign an IP address to a network interface

```
  ansible webservers -m command -a "ip addr add 192.168.1.10/24 dev eth0"
```

### 2. Bring an interface up or down

```
  # Bring Up
  ansible dbservers -m command -a "ip link set eth0 up"

  # Bring Down
  ansible dbservers -m command -a "ip link set eth0 down"
```

### 3. Show all network interfaces on a host

```
  ansible webservers -m command -a "ip addr show"
```

### 4. Set the default gateway

```
  ansible all -m command -a "ip route add default via 192.168.1.1"
```

### 5. Delete the default gateway

```
  ansible all -m command -a "ip route del default via 192.168.1.1"
```

### 6. Add a DNS server to /etc/resolv.conf

```
  ansible all -m lineinfile -a "path=/etc/resolv.conf line='nameserver 8.8.8.8' state=present"
```

### 7. Remove a DNS server entry

```
  ansible all -m lineinfile -a "path=/etc/resolv.conf line='nameserver 8.8.8.8' state=absent"
```

### 8. Allow HTTP traffic (port 80)

```
  ansible all -m command -a "ufw allow 80"
```

### 9. Deny a port (e.g., port 22 for SSH)

```
  ansible all -m command -a "ufw deny 22"
```

### 10. Check firewall status
```
  ansible all -m command -a "ufw status"
```

### 11. Add a static route

```
  ansible all -m command -a "ip route add 192.168.20.0/24 via 192.168.10.1 dev eth0"
```

### 12. Remove a static route

```
  ansible all -m command -a "ip route del 192.168.20.0/24"
```

### 13. Install iperf3 on all hosts

```
  ansible all -m apt -a "name=iperf3 state=present"
```

### 14. Run a bandwidth test as a client

```
  ansible client -m command -a "iperf3 -c 192.168.1.100"
```

### 15. Restart the network service

```
  ansible all -m service -a "name=networking state=restarted"
```

### 16. Check the status of the networking service

```
  ansible all -m service -a "name=networking state=started"
```

---
