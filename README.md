# Instalación de MariaDB 11.5 en Debian 12

Este documento proporciona una guía paso a paso para instalar **MariaDB 11.5** en **Debian 12** de manera segura y eficiente.

## 📌 Requisitos previos
- Un sistema Debian 12 con privilegios de superusuario (`sudo`).
- Conexión a Internet.

## 🔄 Eliminar versiones anteriores (si las hay)
Si tienes una versión previa de MariaDB instalada, es recomendable eliminarla antes de proceder:

```bash
sudo systemctl stop mariadb  # Detener el servicio
sudo apt remove --purge mariadb-server mariadb-client -y  # Eliminar paquetes
sudo apt autoremove -y  # Eliminar dependencias no utilizadas
```

## 🔧 Instalar paquetes necesarios
Antes de agregar el repositorio oficial de MariaDB, instala los paquetes requeridos:

```bash
sudo apt install curl software-properties-common dirmngr -y
```

## 📥 Descargar y configurar el repositorio oficial
MariaDB proporciona un script para configurar su repositorio oficial de manera sencilla:

```bash
curl -LsS -O https://downloads.mariadb.com/MariaDB/mariadb_repo_setup
bash mariadb_repo_setup --mariadb-server-version=11.5  # Especificamos la versión
```

## 📦 Instalar MariaDB 11.5
Una vez agregado el repositorio, instala MariaDB con los siguientes comandos:

```bash
sudo apt update  # Actualizar lista de paquetes
sudo apt install mariadb-server -y  # Instalar MariaDB
```

## 🚀 Habilitar y asegurar la instalación
Para asegurarte de que MariaDB se inicie automáticamente y aplicar medidas de seguridad básicas:

```bash
sudo systemctl enable mariadb  # Habilitar el servicio en el arranque
mysql_secure_installation  # Configurar opciones de seguridad
```

## ✅ Verificar la instalación
Para comprobar que MariaDB está funcionando correctamente, ejecuta:

```bash
systemctl status mariadb
```
Si el servicio está activo y en ejecución, la instalación se ha realizado correctamente. Puedes acceder a MariaDB con:

```bash
mysql -u root -p
```

## 📝 Notas adicionales
- Si necesitas instalar otra versión de MariaDB, simplemente cambia el número en el comando `mariadb_repo_setup`.
- Para administrar MariaDB, puedes usar herramientas como **phpMyAdmin**, **DBeaver**, o directamente la CLI de MariaDB.

---

📢 **Si esta guía te ha sido útil, no olvides darle ⭐ en GitHub!**

#MariaDB #Debian #SysAdmin #OpenSource #BasesDeDatos #Linux
