PRACTICA DE ANSIBLE GRUPAL - openSUSE 16.0

a) Enlace a GitHub
   https://github.com/Tempra123/ansible-aso-lamp-samba
   (proyecto compartido con gcussi@yahoo.com)

b) Pasos para ejecutar el proyecto de Ansible

1. En la VM 01 (Master) (en la VM 02 solo sshd, firewalld y root login):
     zypper install ansible sshpass git unzip openssh-server-config-rootlogin
     systemctl start sshd
     systemctl disable firiewalld

2. Copiar el proyecto a /etc/ansible (elegir UNA opcion) y entrar:

   OPCION A - Descargando el ZIP:
     (en GitHub: boton Code > Download ZIP, y dejar el archivo en la VM 01)
     unzip ansible-aso-lamp-samba-main.zip
     mkdir -p /etc/ansible
     cp -r ansible-aso-lamp-samba-main/. /etc/ansible/
     cd /etc/ansible
   (si se usa el zip de la entrega: unzip ansible-aso.zip y
    cp -r ansible-aso/. /etc/ansible/)

   OPCION B - Con Git:
     git clone https://github.com/Tempra123/ansible-aso-lamp-samba.git
     mkdir -p /etc/ansible
     cp -r ansible-aso-lamp-samba/. /etc/ansible/
     cd /etc/ansible

3. Poner las IP de las maquinas en inventory/hosts.ini:
     vim inventory/hosts.ini

4. Acceso SSH sin contraseña:
     ssh-keygen -t ed25519
     ssh-copy-id root@IP_DE_CADA_MAQUINA

5. Poner las contraseñas en group_vars/servidor/vault.yml y cifrarlo:
     vim group_vars/servidor/vault.yml
     ansible-vault encrypt group_vars/servidor/vault.yml

6. Ejecutar todo (siempre desde /etc/ansible):
     ansible-playbook site.yml --ask-vault-pass
   O solo un rol:
     ansible-playbook site.yml --tags lamp --ask-vault-pass
     ansible-playbook site.yml --tags samba --ask-vault-pass
     ansible-playbook site.yml --tags postgresql --ask-vault-pass
