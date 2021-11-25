all:
		docker-compose -f up -d

restart:
		docker-compose up -d --build

first_start:
#installing docker
		sudo apt update
		sudo apt install apt-transport-https ca-certificates curl software-properties-common
		curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
		sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
		sudo apt update
		apt-cache policy docker-ce
		sudo apt install docker-ce
#checking if Docker the installation was successful 
		sudo systemctl status docker

#installing docker-compose
		sudo apt update
		sudo curl -L "https://github.com/docker/compose/releases/download/1.26.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
		sudo chmod +x /usr/local/bin/docker-compose
#checking if Docker-compose the installation was successful 
		docker-compose --version

#installing other packages
		sudo apt update
		sudo apt install vim \
						git \

#changing hosts in Ubuntu
		cat etc/hosts | sed 's/localhost/sgath.42.fr/g' > hosts.tmp
		sudo rm /etc/hosts && mv hosts.tmp /etc/hosts

clean:
		docker-compose down || true

fclean:	clean
		docker rm  inception_nginx inception_wordpress inception_mariadb || true
		docker rmi -f inception_nginx inception_wordpress inception_mariadb || true
		sudo docker volume rm wordpress mariadb || true
		sudo docker system prune -a --force
