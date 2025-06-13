I Got some error, idk why netplan cant change the Network Settings, so you need to change it manually by GUI or : 

1. Cek if your wifi is ON
nmcli connection show
**contoh :
NAME    UUID                                  TYPE      DEVICE
HERO    xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx  wifi      wlp2s0

2. Change IP Static via NetworkManager
nmcli connection modify HERO ipv4.addresses 192.168.2.25/24 <!-- Your IP -->
nmcli connection modify HERO ipv4.gateway 192.168.2.1 <!-- Your gateaway -->
nmcli connection modify HERO ipv4.dns "8.8.8.8 1.1.1.1" 
nmcli connection modify HERO ipv4.method manual <!-- change to manual (static)-->

3. Restart network
nmcli connection down HERO && nmcli connection up HERO

4. Cek your ip
ip a
