# Instalação do NGINX

### Instalando via package manager:
- Instalação rápida e simples
- Opções limitadas de instalação
- Não tem suporte para módulos adicionais
- Adequado para web servers básicos ou ambiente de teste e desenvolvimento

*Apt-get update* e 
*Apt-get install nginx*

#### Agora nginx não está apenas instalado, mas em execução. Podemos ver usando o comando:

*ps aux | grep nginx*

![image](https://user-images.githubusercontent.com/42981890/101866969-eaf4ba80-3b58-11eb-9049-d274075788ff.png)

#### O serviço já pode ser acessado pelo navegador colocando o ip da máquina. Os arquivos de configuração ficam em */etc/nginx*:
*ls -l /etc/nginx*

### Instalando via código fonte:

#### No site nginx.org encontramos o código fonte atualizado. Vamos baixar e desempacotar:

- *wget http://nginx.org/download/nginx-1.19.5.tar.gz*
- *tar -zxvf nginx-1.19.5.tar.gz*
- *Cd nginx-1.19.5.tar.gz*

#### Agora vamos configurar nosso código fonte. Para isso vamos rodar o script “configure” que está no diretório:

![image](https://user-images.githubusercontent.com/42981890/101867501-0f9d6200-3b5a-11eb-8ff4-a03ba7c51d16.png)

#### Agora vemos o erro "Compilador C não encontrado". 

![image](https://user-images.githubusercontent.com/42981890/101867563-33f93e80-3b5a-11eb-8d1b-61c5846b3548.png)

#### Para resolver isso, vamos ter que instalar um compilador para compilar nosso código fonte:

*Apt-get install build-essential*

#### Após instalar o compilador, vamos rodar novamente o script ./configure:

![image](https://user-images.githubusercontent.com/42981890/101867647-6dca4500-3b5a-11eb-8511-d0cd723b667c.png)

#### Após rodar o script. Já no fim vemos que temos pendência de alguns pacotes. Vamos instalar esses pacotes para nossa dependência:

*Apt-get install libpcre3 libpcre3-dev zlib1g zlib1g-dev libssl-dev*

#### Consultando a documentação, é indicado que algumas flags devem estar presentes ao rodarmos o ./configure. Vamos seguir conforme o que diz a documentação:

*./configure –-sbin-path=/usr/bin/nginx –conf-path=/etc/nginx/nginx.conf –error-log-path=/var/log/nginx/error.log --http-log-path=/var/log/nginx/access.log –with-pcre –pid-path=/var/run/nginx.pid –with-http_ssl_module*

#### Agora sim podemos compilar o código e fazer a instalação:

* - Make*
*- Make install*

#### Agora vamos iniciar o serviço e verificar seu status:

*- nginx*
*- ps aux | grep nginx*

#### Agora vamos adicionar o serviço do nginx como um serviço do sistema:

- Paramos o serviço do nginx: nginx -s stop
-	Criamos o arquivo nginx.service no caminho: touch /lib/systemd/system/nginx.service
- Cole o seguinte script no arquivo usando qualquer editor e salve o arquivo:

![image](https://user-images.githubusercontent.com/42981890/101868430-1927c980-3b5c-11eb-8e74-2b20b238f14c.png)

##### Ele pode ser encontrado nesse link:
<https://www.nginx.com/resources/wiki/start/topics/examples/systemd/>

##### O script possui alguns erros, corrija as seguintes linhas:

- PIDFile=/var/run/nginx.pid
- ExecStarPre=/usr/bin/nginx -t
- ExecStar=/bin/nginx

#### Pronto, agora podemos utilizar o systemctl do systemd para manipular o serviço do nginx. Contudo, pode ocorrer do servidor reiniciar por algum motivo. Caso isso ocorra, o serviço precisa reiniciar junto com o sistema operacional. Então vamos habilitar:

*systemctl enable nginx*

##### Para testar podemos reiniciar o servidor. Após reiniciar usamos o comando para ver o status do serviço:

*systemctl status nginx*




