sudo apt update
sudo apt install tor -y
sudo apt install -y obfs4proxy

sudo nano /etc/tor/torrc
вставляем в самый конец
```
SocksPort 9050
SocksListenAddress 0.0.0.0
```

sudo nano /etc/tor/torrc
в конец файла вставляем содержимое файла bridges.txt

sudo systemctl enable tor
sudo systemctl restart tor

проверка работы
curl --socks5 127.0.0.1:9050 https://ifconfig.me
curl --max-time 20 --socks5-hostname 127.0.0.1:9050 https://ifconfig.me

systemctl status tor
systemctl status tor@default
ss -ltnp | grep 9050
