# PROJETO DOCKER

## Pré-requisitos
- WSL (Windows)
- Docker
- Docker-compose
- Git
- Redis-cli

## Instalação
Clonar esse projeto pra dentro da raíz do projeto:

``git clone https://github.com/cemim/docker.git``
- Criar um arquivo .env com base no arquivo sample.env, no arquivo .env selecionar a versão do PHP e do banco de dados com base nas versões disponíveis no diretorio bin. 

- Criar um diretorio onde os dados do banco de dados serão persistidos, isso é necessário para que mesmo que o container e o volume sejam destruidos, mesmo assim os dados serao mantidos localmente, caso esteja usando o wsl é recomendado o diretório /home/SEU-USUARIO/mysql-data-wordpress-curso, pois o container não consegue acessar os dados no diretório windows /mnt, no linux esses dados podem ser salvos em qualquer diretorio.

- Antes de subir o container verificar o IP da maquina real se não há conflitos com a mesma rede, por padrão esta configurado para a rede 172.25.0.0/16, sendo que o IP do banco de dados 172.25.0.10 e os demais containers é dinamico, para acessar o banco da sua aplicação pode usar esse IP

- No diretório config altere as configurações do php.ini e do vhost para apontar para o diretorio publico do seu projeto.

Após as devidas configurações:
``docker-compose up -d``

## Acesso dos container:
Acesso a aplicação: [localhost:8000](http://localhost:8000/)

Acesso ao PHPMyadmin: [localhost:8080](http://localhost:8080/)

Acesso ao Redis: ``redis-cli -h *<host> -p 6379``

*Para verificar o IP dos containers: ``docker network inspect wordpress_my_custom_network``

