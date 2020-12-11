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





