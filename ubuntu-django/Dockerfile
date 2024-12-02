FROM ubuntu:22.04

# Instale os pacotes necessários
RUN apt-get update \
    && apt-get install -y nginx openssh-server \
    && apt install -y vim

# Configure o SSH
RUN mkdir /var/run/sshd
RUN useradd -m -d /home/django-user -s /bin/bash django-user
RUN mkdir /home/django-user/.ssh
COPY authorized_keys /home/django-user/.ssh/authorized_keys
RUN chmod 700 /home/django-user/.ssh && chmod 600 /home/django-user/.ssh/authorized_keys
RUN chown -R django-user:django-user /home/django-user/.ssh
RUN sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin no/' /etc/ssh/sshd_config
RUN sed -i 's/#PasswordAuthentication yes/PasswordAuthentication no/' /etc/ssh/sshd_config
RUN sed -i 's/#PubkeyAuthentication yes/PubkeyAuthentication yes/' /etc/ssh/sshd_config
RUN echo "AllowUsers django-user" >> /etc/ssh/sshd_config

# Copie o arquivo de configuração do Nginx
COPY nginx.conf /etc/nginx/nginx.conf

# Exponha as portas 80 (Nginx) e 22 (SSH)
EXPOSE 80 22

# Comando para iniciar o Nginx e o SSH
CMD service ssh start && nginx -g 'daemon off;'
