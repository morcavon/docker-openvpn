# OpenVPN for Docker with Raspberry Pi
This project is forked from kylemanna/docker-openvpn.
You can find detailed README from the original project.

## Really Quick Start
        OVPN_DATA="ovpn-data"
        docker run --name $OVPN_DATA -v /etc/openvpn morcavon/rpi-busybox-docker
        docker run --volumes-from $OVPN_DATA --rm morcavon/openvpn ovpn_genconfig -u udp://VPN.SERVERNAME.COM
        docker run --volumes-from $OVPN_DATA --rm -it morcavon/openvpn ovpn_initpki
        docker run --volumes-from $OVPN_DATA -d -p 1194:1194/udp --cap-add=NET_ADMIN morcavon/openvpn
        docker run --volumes-from $OVPN_DATA --rm -it morcavon/openvpn easyrsa build-client-full CLINETNAME nopass
        docker run --volumes-from $OVPN_DATA --rm morcavon/openvpn ovpn_getclient CLIENTNAME > CLIENTNAME.ovpn

* Now, we can use CLIENTNAME.ovpn with OpenVPN client.
* Thanks to Ryan Grenz for inform of me the rpi-busybox-docker.
