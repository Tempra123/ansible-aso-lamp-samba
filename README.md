<div align="center">

# ☁️ Ansible ASO

### 🛠️ Automatización de LAMP, Samba y PostgreSQL en openSUSE 16.0

<img src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&size=20&pause=1000&color=58A6FF&center=true&vCenter=true&width=650&lines=Configurando+servidores+con+Ansible...;Roles+para+LAMP%2C+Samba+y+PostgreSQL...;Practica+grupal+de+ASO" />

<br>

<p>
  <img src="https://img.shields.io/badge/Ansible-Automation-EE0000?style=for-the-badge&logo=ansible"/>
  <img src="https://img.shields.io/badge/openSUSE-16.0-73BA25?style=for-the-badge&logo=opensuse"/>
  <img src="https://img.shields.io/badge/Apache-PHP_8-D22128?style=for-the-badge&logo=apache"/>
</p>

<p>
  <img src="https://img.shields.io/badge/MariaDB-Database-003545?style=for-the-badge&logo=mariadb"/>
  <img src="https://img.shields.io/badge/PostgreSQL-Remote-4169E1?style=for-the-badge&logo=postgresql&logoColor=white"/>
  <img src="https://img.shields.io/badge/Samba-Shares-1E90FF?style=for-the-badge"/>
</p>

</div>

<h2 align="center">👥 Equipo de Trabajo</h2>

<!-- 📷 FOTOS 2, 3, 4, 5: una foto por integrante -> assets/leonardo.jpeg, integrante2.jpg, integrante3.jpg, integrante4.jpg -->

<div align="center">
<table>
<tr>

<td align="center" valign="top" width="50%">
<img src="./assets/leonardo.jpeg" width="120"/><br>
<b>🧑‍💻 Leonardo Mena</b><br>
Grupo 1<br>
🎓 Codsis: 202201743<br>
📱 +591 69588990
</td>

<td align="center" valign="top" width="50%">
<img src="./assets/perfil.png" width="120"/><br>
<b>🧑‍🎨 Dylan Temprano</b><br>
Grupo 1<br>
🎓 Codsis: 202201667<br>
📱 +591 71426919
</td>

</tr>
<tr>

<td align="center" valign="top" width="50%">
<img src="./assets/imagen%20para%20aso.jpeg" width="120"/><br>
<b>⚙️ Areacely Alcon</b><br>
Grupo 1<br>
🎓 Codsis: 202501435<br>
📱 +591 75965338
</td>

<td align="center" valign="top" width="50%">
<img src="./assets/integrante4.jpg" width="120"/><br>
<b>🧩 Nombre Apellido</b><br>
Grupo X<br>
🎓 Codsis: 000000000<br>
📱 +591 7XXXXXXX
</td>

</tr>
</table>
</div>

---

<h2 align="center">📖 Descripción del Proyecto</h2>

<p align="center">
Proyecto de <b>Ansible</b> que configura de forma remota, desde una máquina Master (VM 01),<br>
las demás máquinas virtuales con <b>openSUSE 16.0</b>.<br><br>
Se organiza en <b>roles</b>, uno por servicio:
</p>

<div align="center">

| Rol | Qué configura |
|:---:|:---:|
| 🌐 `lamp` | Apache, PHP 8, phpMyAdmin y MariaDB (clave de root, base `ventas`, tabla `emp`) |
| 📁 `samba` | Usuario del sistema, usuario de Samba, directorio compartido y `create mask` |
| 🐘 `postgresql` | PostgreSQL, `php8-pgsql`, clave de `postgres`, usuario nuevo, conexiones remotas y clave cifrada |

</div>

---

<h2 align="center">✅ Tareas cubiertas</h2>

<div align="center">

| Tarea | Descripción | Dónde está |
|:---:|:---:|:---:|
| **Tarea 3** | LAMP y Samba con roles, inventario sin contraseñas y optimización | `roles/lamp`, `roles/samba`, `ansible.cfg`, `group_vars/` |
| **Tarea 4** | Scripts y archivos de configuración en GitHub | Este repositorio |
| **Tarea 5** | Rol de PostgreSQL | `roles/postgresql` |

</div>

---

<h2 align="center">🧱 Estructura del Proyecto</h2>

```text
.
├── ansible.cfg              → Configuración y optimización
├── site.yml                 → Playbook principal
├── inventory/
│   └── hosts.ini            → Solo las IP de las máquinas
├── group_vars/servidor/
│   ├── vars.yml             → Variables (sin contraseñas)
│   └── vault.yml            → Contraseñas cifradas (ansible-vault)
├── configuraciones/         → Archivos de configuración a copiar
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

<h2 align="center">⚡ Optimización</h2>

<div align="center">

| Cambio | Para qué sirve |
|:---:|:---:|
| 🔐 `ansible-vault` | Las contraseñas no quedan a la vista en el inventario |
| 🧑‍🤝‍🧑 `forks = 10` | Trabaja con 10 máquinas a la vez |
| 🚫 `gather_facts: false` | No recolecta datos innecesarios al iniciar |
| 📦 `pipelining = True` | Menos pasos por SSH en cada tarea |
| 🔁 `ControlPersist=60s` | Reutiliza la conexión SSH en vez de abrir una por tarea |
| 🏃 `strategy: free` | Cada máquina avanza a su ritmo, sin esperar a la más lenta |
| ⏱️ `timeout = 5` y `ConnectTimeout=5` | Una IP caída falla en 5 segundos y sin reintentos (`ConnectionAttempts=1`) |
| 🤝 `host_key_checking = False` | No pregunta "¿confías en esta máquina?" al conectar por primera vez |
| 🧰 Paquetes en una sola tarea | Cada rol instala todos sus paquetes con un solo `zypper` |
| 🔔 `handlers` (`notify`) | Al copiar un archivo de configuración se avisa al handler que reinicia el servicio |

</div>

---

<h2 align="center">🛠️ Tecnologías Utilizadas</h2>

<div align="center">

<img src="https://img.shields.io/badge/Ansible-Roles-EE0000?style=for-the-badge&logo=ansible"/>
<img src="https://img.shields.io/badge/Linux-openSUSE-73BA25?style=for-the-badge&logo=opensuse"/>
<img src="https://img.shields.io/badge/PHP-8-777BB4?style=for-the-badge&logo=php"/>
<img src="https://img.shields.io/badge/MariaDB-SQL-003545?style=for-the-badge&logo=mariadb"/>
<img src="https://img.shields.io/badge/PostgreSQL-SQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white"/>

</div>

---

<h2 align="center">🖼️ Vista previa</h2>

<!-- 📷 FOTOS 6 a 10: capturas de pantalla del proyecto funcionando -> carpeta assets/ -->

<h3 align="center">▶️ Ejecución del playbook</h3>

<!-- 📷 FOTO 6: terminal con el resultado final (PLAY RECAP con failed=0) -> assets/playbook.png -->
<div align="center">
  <img src="./assets/playbook.png" width="90%" />
</div>

<h3 align="center">🌐 LAMP funcionando</h3>

<!-- 📷 FOTO 7: navegador en http://IP/info.php -> assets/info-php.png -->
<!-- 📷 FOTO 8: navegador en http://IP/phpMyAdmin mostrando la base ventas -> assets/phpmyadmin.png -->
<div align="center">
  <img src="./assets/phpadmin.png" width="45%" />
  <img src="./assets/lamp1.png" width="45%" />
</div>

<h3 align="center">📁 Samba funcionando</h3>

<!-- 📷 FOTO 9: terminal con smbclient -L //IP -U user01 -> assets/samba.png -->
<div align="center">
  <img src="./assets/samba.png" width="90%" />
</div>

<h3 align="center">🐘 PostgreSQL remoto funcionando</h3>

<!-- 📷 FOTO 10: terminal con psql -U postgres -h IP desde otra máquina -> assets/postgresql.png -->
<div align="center">
  <img src="./assets/postgres.png" width="90%" />
</div>

---

<h2 align="center">🚀 Cómo ejecutar el proyecto</h2>

<h3 align="center">📥 1. En la VM 01 (Master)</h3>

<p align="center">En la VM 02 solo hace falta <code>sshd</code>, <code>firewalld</code> y el acceso root.</p>

```bash
zypper install ansible sshpass git unzip openssh-server-config-rootlogin
systemctl start sshd
systemctl disable firewalld
```

<h3 align="center">📂 2. Copiar el proyecto a <code>/etc/ansible</code> y entrar</h3>

<p align="center">Elegir <b>una</b> de las dos opciones.</p>

<h4 align="center">📦 Opción A — Descargando el ZIP</h4>

<p align="center">En GitHub: botón <b>Code &gt; Download ZIP</b> y dejar el archivo en la VM 01.</p>

```bash
unzip ansible-aso-lamp-samba-main.zip
mkdir -p /etc/ansible
cp -r ansible-aso-lamp-samba-main/. /etc/ansible/
cd /etc/ansible
```

<h4 align="center">🐙 Opción B — Con Git</h4>

```bash
git clone https://github.com/Tempra123/ansible-aso-lamp-samba.git
mkdir -p /etc/ansible
cp -r ansible-aso-lamp-samba/. /etc/ansible/
cd /etc/ansible
```

<h3 align="center">🌐 3. Poner las IP de las máquinas</h3>

<p align="center">Editar <code>inventory/hosts.ini</code></p>

<h3 align="center">🔑 4. Acceso SSH sin contraseña</h3>

```bash
ssh-keygen -t ed25519
ssh-copy-id root@IP_DE_CADA_MAQUINA
```

<h3 align="center">🔐 5. Poner las contraseñas y cifrarlas</h3>

<p align="center">Editar <code>group_vars/servidor/vault.yml</code> y cifrarlo:</p>

```bash
vim group_vars/servidor/vault.yml
ansible-vault encrypt group_vars/servidor/vault.yml
```

<h3 align="center">▶️ 6. Ejecutar</h3>

<p align="center">Siempre desde <code>/etc/ansible</code></p>

<p align="center"><b>Todo:</b></p>

```bash
ansible-playbook site.yml --ask-vault-pass
```

<p align="center"><b>Solo un rol:</b></p>

```bash
ansible-playbook site.yml --tags lamp --ask-vault-pass
ansible-playbook site.yml --tags samba --ask-vault-pass
ansible-playbook site.yml --tags postgresql --ask-vault-pass
```

---

<div align="center">

**🚀 Práctica de Ansible grupal — ASO**<br>
👥 Trabajo en equipo<br>
✨ openSUSE 16.0 · 2026

</div>
