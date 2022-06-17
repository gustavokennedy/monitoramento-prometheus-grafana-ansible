<p align="center">
   <br/>
   <h1 align="center">Prometheus, AlertManager, Node_Exporter e Grafana usando Ansible</h1>
   <p align="center">
   Repositório criado para automatizar processo de monitoramento com Prometheus, AlertManager, Node_Exporter e Grafana usando Ansible. Utilizando Ubuntu Server 20.04LTS.
   </p>
   <p align="center" style="align: center;">
        <img alt="AWS" src="https://img.shields.io/badge/Amazon_AWS-232F3E?style=for-the-badge&logo=amazon-aws&logoColor=white">
        <img alt="Nginx" src="https://img.shields.io/badge/Nginx-009639?style=for-the-badge&logo=nginx&logoColor=white">
        <img alt="Ansible" src="https://img.shields.io/badge/Ansible-000000?style=for-the-badge&logo=Ansible&logoColor=white">
        <img alt="Prometheus`" src="https://img.shields.io/badge/Prometheus-E6522C?style=for-the-badge&logo=prometheus&logoColor=white">
   </p>
</p>

### Estruturas
* Nginx - Webserver
* Prometheus
* Grafana
* AlertManager
* Node_Exporter

## Como iniciar
### 1. Clone o repositório e instale as dependências no servidor de monitoramento

```
git https://github.com/gustavokennedy/monitoramento-prometheus-grafana-ansible.git
cd monitoramento-prometheus-grafana-ansible
```
Para evitar erros, instale o Ansible e o SSHPASS:

```
sudo apt-get install ansible

sudo apt-get install sshpass
```

Caso houver erro de status do Nginx:

```
sudo /etc/init.d/apache2 stop
sudo systemctl restart nginx
```

### 2. Configurando variáveis

Abra o arquivo inventory e altere para os IPs específicos:

```
[all:children]
nginx

[nginx]
192.168.0.132 ansible_ssh_pass=root ansible_ssh_user=usuario

[prometheus]
192.168.0.132 ansible_ssh_pass=root ansible_ssh_user=usuario

[node_exporter]
192.168.0.132 ansible_ssh_pass=root ansible_ssh_user=usuario

[alertmanager]
192.168.0.132 ansible_ssh_pass=root ansible_ssh_user=usuario

[grafana]
192.168.0.132 ansible_ssh_pass=root ansible_ssh_user=usuario
```

### Iniciar / Executar no Servidor de Monitoramento

Para inciar o playbook, execute:

```
ansible-playbook playbook.yml
```

Caso ainda aconteça erro de permissão tente:

```
sudo ansible-playbook playbook.yml -kK 
```

Pode acontencer [erro Missing Sudo Password](https://github.com/gustavokennedy/resolvendo-missing-sudo-password-ansible);

### Servidor cliente

Para inciar o playbook no servidor do cliente, execute:

> NOTE: Lembrar de liberar portas para Prometheus, AlertManager, Node_Exporter e Grafana.

```
ansible-playbook playbook-cliente.yml
```
