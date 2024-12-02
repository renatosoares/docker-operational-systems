
Caminho do arquivo
```bash
vim /etc/ssh/sshd_config 
```

Alterar as seguinte variáveis para:
```
PubkeyAuthentication yes
AuthorizedKeysFile .ssh/authorized_keys
PasswordAuthentication no 
MaxAuthTries 16 
```

Crie o diretório .ssh:

```bash
mkdir -p /root/.ssh
```

Crie o arquivo authorized_keys:
```bash
touch /root/.ssh/authorized_keys
```

Defina as permissões apropriadas:
```bash
chmod 700 /root/.ssh
chmod 600 /root/.ssh/authorized_keys
```

Adicione sua chave pública ao arquivo authorized_keys:
```bash
echo "sua-chave-publica-ssh" >> /root/.ssh/authorized_keys
```

---

Acessar via ssh
```bash
ssh -i ~/.ssh/docker-ubuntu-django django-user@localhost -p 2222
```

---

---

_(Local)_ gerar chave pública para o servidor
```bash
ssh-keygen -f ~/.ssh/docker-ubuntu-django -t rsa -b 4096
```

---

_(Local)_ pega a chave gerada e adiciona no servidor
```bash
cat ~/.ssh/docker-ubuntu-django.pub
```

---

---

_(local)_ A chave privada deve ter as permissões corretas no sistema de arquivos do seu computador.
```bash
chmod 600 ~/.ssh/docker-ubuntu-django
```
