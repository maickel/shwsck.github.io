## Shadowsocks Setup

### Install
```markdown
# Admin
sudo su

# shadowsocks
apt-get update
apt-get install python-pip
pip install shadowsocks

# m2crypto
apt-get install python-m2crypto
apt-get install build-essential
wget https://github.com/jedisct1/libsodium/releases/download/1.0.10/libsodium-1.0.10.tar.gz
tar xf libsodium-1.0.10.tar.gz && cd libsodium-1.0.10
./configure && make && make install
ldconfig

# shadowsocks-libev
apt-get install software-properties-common -y
add-apt-repository ppa:max-c-lv/shadowsocks-libev -y
apt-get update
apt install shadowsocks-libev
```

### Configuration
```markdown
# Edit the configuration file
sudo vim /etc/shadowsocks-libev/config.json

{
    "server":"private_ip",
    "server_port":443,
    "local_port":1080,
    "password":"password",
    "timeout":600,
    "method":"chacha20-ietf-poly1305"
}
```

### Manage
```markdown
# Edit the default configuration for debian
sudo vim /etc/default/shadowsocks-libev

# Start the service
sudo /etc/init.d/shadowsocks-libev start    # for sysvinit, or
sudo systemctl start shadowsocks-libev      # for systemd
```
