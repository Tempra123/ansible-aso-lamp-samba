<div align="center">

# ☁️ Ansible ASO

### 🛠️ Automatización de LAMP, Samba y PostgreSQL en openSUSE 16.0

<img src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&size=20&pause=1000&color=58A6FF&center=true&vCenter=true&width=650&lines=Configurando+servidores+con+Ansible...;Roles+para+LAMP%2C+Samba+y+PostgreSQL...;Practica+grupal+de+ASO" />

<br>

<p>
  <img src="https://img.shields.io/badge/Ansible-Automation-EE0000?style=for-the-badge&logo=ansible"/>
  <img src="https://img.shields.io/badge/openSUSE-16.0-73BA25?style=for-the-badge&logo=opensuse"/>
  <img src="https://img.shields.io/badge/Apache-PHP_8-D22128?style=for-the-badge&logo=apache"/>
  <img src="https://img.shields.io/badge/MariaDB-Database-003545?style=for-the-badge&logo=mariadb"/>
  <img src="https://img.shields.io/badge/PostgreSQL-Remote-4169E1?style=for-the-badge&logo=postgresql&logoColor=white"/>
  <img src="https://img.shields.io/badge/Samba-Shares-1E90FF?style=for-the-badge"/>
</p>

</div>

## 👥 Equipo de Trabajo

<!-- 📷 FOTOS 2, 3, 4, 5: una foto por integrante -> assets/leonardo.jpeg, integrante2.jpg, integrante3.jpg, integrante4.jpg -->

<table>
<tr>

<td width="50%">
<table><tr>
<td><img src="./assets/leonardo.jpeg" width="90"/></td>
<td>

**🧑‍💻 Leonardo Mena**<br>
Grupo 1<br>
🎓 Codsis: 202201743<br>
📱 +591 69588990

</td>
</tr></table>
</td>

<td width="50%">
<table><tr>
<td><img src="./assets/perfil.png" width="90"/></td>
<td>

**🧑‍🎨 Dylan Temprano**<br>
Grupo 1<br>
🎓 Codsis: 202201667<br>
📱 +591 71426919

</td>
</tr></table>
</td>

</tr>
<tr>

<td width="50%">
<table><tr>
<td><img src="./assets/imagen para aso.jpeg" width="90"/></td>
<td>

**⚙️ Areacely Alcon**<br>
Grupo 1<br>
🎓 Codsis: 202501435<br>
📱 +591 75965338

</td>
</tr></table>
</td>

<td width="50%">
<table><tr>
<td><img src="./assets/integrante4.jpg" width="90"/></td>
<td>

**🧩 Nombre Apellido**<br>
Grupo X<br>
🎓 Codsis: 000000000<br>
📱 +591 7XXXXXXX

</td>
</tr></table>
</td>

</tr>
</table>

---

## 📖 Descripción del Proyecto

Proyecto de **Ansible** que configura de forma remota, desde una máquina Master (VM 01), las demás máquinas virtuales con **openSUSE 16.0**.

Se organiza en **roles**, uno por servicio:

| Rol | Qué configura |
|---|---|
| 🌐 `lamp` | Apache, PHP 8, phpMyAdmin y MariaDB (clave de root, base `ventas`, tabla `emp`) |
| 📁 `samba` | Usuario del sistema, usuario de Samba, directorio compartido y `create mask` |
| 🐘 `postgresql` | PostgreSQL, `php8-pgsql`, clave de `postgres`, usuario nuevo, conexiones remotas y clave cifrada |

---

## ✅ Tareas cubiertas

| Tarea | Descripción | Dónde está |
|---|---|---|
| **Tarea 3** | LAMP y Samba con roles, inventario sin contraseñas y optimización | `roles/lamp`, `roles/samba`, `ansible.cfg`, `group_vars/` |
| **Tarea 4** | Scripts y archivos de configuración en GitHub | Este repositorio |
| **Tarea 5** | Rol de PostgreSQL | `roles/postgresql` |

---

## 🧱 Estructura del Proyecto

```text
.
├── ansible.cfg              → Configuración y optimización de Ansible
├── site.yml                 → Playbook principal
├── requirements.yml         → Colecciones necesarias (zypper)
├── inventory/
│   └── hosts.ini            → Solo las IP de las máquinas
├── group_vars/servidor/
│   ├── vars.yml             → Variables (sin contraseñas)
│   └── vault.yml            → Contraseñas cifradas con ansible-vault
├── configuraciones/         → Archivos de configuración reales a copiar
│   ├── php.ini
│   ├── smb.conf
│   ├── postgresql.conf
│   ├── pg_hba.conf
│   ├── info.php
│   └── prueba.php
└── roles/
    ├── lamp/
    ├── samba/
    └── postgresql/
```

---

## ⚡ Optimización

| Cambio | Para qué sirve |
|---|---|
| 🔐 `ansible-vault` | Las contraseñas no quedan a la vista en el inventario |
| 🧑‍🤝‍🧑 `forks = 10` | Trabaja con 10 máquinas a la vez |
| 🚫 `gather_facts: false` | No recolecta datos innecesarios al iniciar |
| 📦 `pipelining = True` | Menos pasos por SSH en cada tarea |
| 🔁 `ControlPersist=60s` | Reutiliza la conexión SSH en vez de abrir una por tarea |

---

## 🛠️ Tecnologías Utilizadas

<div align="center">

<img src="https://img.shields.io/badge/Ansible-Roles-EE0000?style=for-the-badge&logo=ansible"/>
<img src="https://img.shields.io/badge/Linux-openSUSE-73BA25?style=for-the-badge&logo=opensuse"/>
<img src="https://img.shields.io/badge/PHP-8-777BB4?style=for-the-badge&logo=php"/>
<img src="https://img.shields.io/badge/MariaDB-SQL-003545?style=for-the-badge&logo=mariadb"/>
<img src="https://img.shields.io/badge/PostgreSQL-SQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white"/>

</div>

---

## 🖼️ Vista previa

<!-- 📷 FOTOS 6 a 10: capturas de pantalla del proyecto funcionando -> carpeta assets/ -->

### ▶️ Ejecución del playbook

<!-- 📷 FOTO 6: terminal con el resultado final (PLAY RECAP con failed=0) -> assets/playbook.png -->
<div align="center">
  <img src="./assets/playbook.png" width="800" />
</div>

### 🌐 LAMP funcionando

<!-- 📷 FOTO 7: navegador en http://IP/info.php -> assets/info-php.png -->
<!-- 📷 FOTO 8: navegador en http://IP/phpMyAdmin mostrando la base ventas -> assets/phpmyadmin.png -->
<div align="center">
  <img src="./assets/info-php.png" width="400" />
  <img src="./assets/phpmyadmin.png" width="400" />
</div>

### 📁 Samba funcionando

<!-- 📷 FOTO 9: terminal con smbclient -L //IP -U user01 -> assets/samba.png -->
<div align="center">
  <img src="./assets/samba.png" width="800" />
</div>

### 🐘 PostgreSQL remoto funcionando

<!-- 📷 FOTO 10: terminal con psql -U postgres -h IP desde otra máquina -> assets/postgresql.png -->
<div align="center">
  <img src="./assets/postgresql.png" width="800" />
</div>

---

## 🚀 Cómo ejecutar el proyecto

### 📥 1. En la VM 01 (Master)

```bash
zypper install ansible sshpass openssh-server-config-rootlogin
systemctl enable sshd
```

### 📂 2. Copiar el proyecto a `/etc/ansible` y entrar

```bash
unzip ansible-aso.zip
cp -r ansible-aso/* /etc/ansible/
cd /etc/ansible
```

### 📄 3. Copiar las configuraciones reales de la VM 01 a `configuraciones/`

```bash
cp /etc/php8/apache2/php.ini            configuraciones/
cp /etc/samba/smb.conf                  configuraciones/
cp /var/lib/pgsql/data/postgresql.conf  configuraciones/
cp /var/lib/pgsql/data/pg_hba.conf      configuraciones/
```

### 🌐 4. Poner las IP de las máquinas

Editar `inventory/hosts.ini`.

### 🔑 5. Acceso SSH sin contraseña

```bash
ssh-keygen -t ed25519
ssh-copy-id root@IP_DE_CADA_MAQUINA
```

### 🔐 6. Poner las contraseñas y cifrarlas

Editar `group_vars/servidor/vault.yml` y cifrarlo:

```bash
vim group_vars/servidor/vault.yml
ansible-vault encrypt group_vars/servidor/vault.yml
```

### ▶️ 7. Ejecutar

Todo:

```bash
ansible-playbook site.yml --ask-vault-pass
```

Solo un rol:

```bash
ansible-playbook site.yml --tags lamp --ask-vault-pass
ansible-playbook site.yml --tags samba --ask-vault-pass
ansible-playbook site.yml --tags postgresql --ask-vault-pass
```

---

<div align="center">

```text
🚀 Práctica de Ansible grupal — ASO
👥 Trabajo en equipo
✨ openSUSE 16.0 · 2026
```

</div>
