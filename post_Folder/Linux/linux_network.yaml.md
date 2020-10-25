# linux_network.yaml

---

sudo vim /etc/netplan/01-network-manager-all.yaml

        network:
        
        ethernets:
        
                ens18:
                
                        dhcp4: no
                        
                        addresses: [172.28.31.201/24]
                        
                        gateway4: 172.28.31.254
                        
                        nameservers:
                        
                                addresses: [114.114.114.114]
        
