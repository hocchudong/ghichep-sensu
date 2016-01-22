### Các bước cài đặt sensu
- Chạy lệnh dưới để update Ubuntu 
```sh
apt-get update -y && apt-get upgrade -y && apt-get dist-upgrade -y && init 6
```

####  Install Erlang
```sh
sudo wget http://packages.erlang-solutions.com/erlang-solutions_1.0_all.deb
sudo dpkg -i erlang-solutions_1.0_all.deb
sudo apt-get - y update
sudo apt-get -y install erlang-nox=1:18.2
```


#### Cài đặt RABBITMQ

- Cài đặt RABBITMQ
```sh
sudo wget http://www.rabbitmq.com/releases/rabbitmq-server/v3.6.0/rabbitmq-server_3.6.0-1_all.deb
sudo dpkg -i rabbitmq-server_3.6.0-1_all.deb
```

- Khởi động RABBITMQ
```sh
sudo update-rc.d rabbitmq-server defaults
sudo /etc/init.d/rabbitmq-server start
```

- Cấu hình cho RABBITMQ
```sh
sudo rabbitmqctl add_vhost /sensu
sudo rabbitmqctl add_user sensu secret
sudo rabbitmqctl set_permissions -p /sensu sensu ".*" ".*" ".*"


### Cài đặt REDDIS
- Cài đặt REDDIS
```sh
sudo apt-get -y update
sudo apt-get -y install redis-server
```

- Khởi động REDDIS cùng OS
```sh
sudo update-rc.d redis-server defaults
sudo /etc/init.d/redis-server start
```

#### Cài đặt SENSU

- Khai báo repos cho SENSU
```sh
wget -q http://repositories.sensuapp.org/apt/pubkey.gpg -O- | sudo apt-key add -
echo "deb     http://repositories.sensuapp.org/apt sensu main" | sudo tee /etc/apt/sources.list.d/sensu.list
```

- Thực hiện cài SENSU sau khi khai báo repos
```sh
sudo apt-get -y update
sudo apt-get -y install sensu
```



















