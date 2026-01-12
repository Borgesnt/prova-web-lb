# Prova Web com Balanceamento de Carga – AWS

## Descrição do Projeto
Este projeto foi desenvolvido para a prova prática da disciplina de **Serviços de Redes**.
O objetivo é disponibilizar uma página web estática simples, versionada com Git, publicada em duas instâncias EC2 com Apache e acessada por meio de um **Application Load Balancer (ALB)** na AWS, garantindo alta disponibilidade e balanceamento de carga.

Cada instância exibe sua identificação individual (web1 ou web2), permitindo validar o funcionamento do balanceamento.

---

## Instalação e Administração do Apache

### Atualização do sistema
```bash
sudo apt update
```

### Instalação do Apache
```bash
sudo apt install apache2 -y
```

### Inicialização do serviço
```bash
sudo systemctl start apache2
```

### Habilitar Apache na inicialização do sistema
```bash
sudo systemctl enable apache2
```

### Verificação do status do serviço
```bash
systemctl status apache2
```

---

## Publicação do Site
```bash
sudo rm -rf /var/www/html/*
sudo cp -r site/* /var/www/html/
sudo chown -R www-data:www-data /var/www/html
```

---

## DNS do Load Balancer
```
alb-prova-web-1847840527.us-east-1.elb.amazonaws.com
```

---

## Comandos de Teste

### Teste local na instância
```bash
curl http://localhost
```

### Teste via Application Load Balancer
```bash
curl http://alb-prova-web-1847840527.us-east-1.elb.amazonaws.com
```

Ao executar o comando várias vezes, é possível observar a alternância entre as instâncias `web1` e `web2`, comprovando o balanceamento de carga.

