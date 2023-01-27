# Ansible

O Ansible é uma ferramenta sem agentes, ou seja, não requer instalação de software para gerenciamento dos nós. Ele acessa seu inventário e lê as informações sobre quais máquinas você deseja gerenciar. O Ansible tem um arquivo de inventário padrão, mas você pode criar o seu próprio arquivo e definir quais servidores quer que sejam gerenciados. 

Ele usa o protocolo SSH para se conectar aos servidores e executar as tarefas. Por padrão, o Ansible usa chaves SSH com o ssh-agent e seu nome de usuário atual para se conectar a máquinas remotas.

## Documentação oficial

Para saber mais a respeito do processo de instalação e configuração, acesse a [documentação oficial do Ansible](https://docs.ansible.com/ansible/latest/installation_guide/index.html).

## Instalação e configuração (Ubuntu 22.04)


Adicione o repositório oficial do Ansible
```bash
sudo apt-add-repository ppa:ansible/ansible
```

Atualize os repositórios do sistema e instale o Ansible
```bash
sudo apt update -y
sudo apt install ansible
```
O diretório e os arquivos de configurações serão criados em `/etc/ansible`.

Antes de substituir o diretório de configuração gerado na instalação, realize um backup do mesmo.
```bash
sudo cp -r /etc/ansible /etc/ansible-bak
```
Após ter realizado a cópia do diretório, clone este repositório, para o mesmo local do anterior.
```bash
sudo git clone https://gitlab.deltasul.com.br/NicolasdaSilvaAraujo/ansible/ /etc/ansible
```
Após o processo, o Ansible estará pronto para uso, para rodar o playbook existente no diretório, rode o seguinte comando.
```bash
root@ansible:/etc/ansible# ansible-playbook -i inventories/production.yml 01-playbook.yml --ask-pass
```
*OBS: Lembrando que ao rodar o playbook sem editar a linha de `hosts`, o playbook será executado em **todos** os hosts presentes no inventário.*

