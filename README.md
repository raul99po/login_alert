# 🔐 SSH Login Alert via Telegram Bot

Este script envía una alerta a tu cuenta de Telegram cada vez que alguien inicia sesión por SSH en tu servidor. Es ideal para monitorear accesos no autorizados o simplemente estar al tanto de quién entra a tu sistema.

![GitHub](https://img.shields.io/badge/Version-1.0-blue)
![License](https://img.shields.io/badge/License-MIT-green)

## 📦 Requisitos

- Servidor Linux con acceso root
- `curl` instalado (`sudo apt install curl` para Debian/Ubuntu)
- Cuenta de Telegram
- Bot de Telegram creado con [@BotFather](https://t.me/BotFather)


## 🚀 Instalación

1. **Clona el repositorio**:
   ```bash
   git clone https://github.com/raul99po/login_alert.git
   cd login_alert
   
2. **Edita el script con tu BOT_TOKEN y CHAT_ID**:
   ```bash
   nano ssh-login-notifier.sh

4. **Dale permisos de ejecución**:
   ```bash
   chmod +x ssh-login-notifier.sh
   
6. **Ubica el script en el archivo SSHRC del sistema**:
   Copia el contenido del script dentro de /etc/ssh/sshrc o enlázalo con:
   ```bash
   sudo cp ssh-login-notifier.sh /etc/ssh/sshrc
   sudo chmod +x /etc/ssh/sshrc
   
8. **Crea el archivo de log si no existe**:
   ```bash
   sudo touch /var/log/login_alert.log
   sudo chmod 644 /var/log/login_alert.log

# 🛠️ Cómo obtener tu BOT_TOKEN y CHAT_ID
1. **Crear un bot con @BotFather**
  Habla con @BotFather
  Envía /newbot y sigue los pasos.
  Guarda el TOKEN que te da.

2. **Obtener tu CHAT_ID**
Habla con tu bot (envía cualquier mensaje)
Luego ve a:
https://api.telegram.org/bot<BOT_TOKEN>/getUpdates
Busca tu id en "chat":{"id":XXXXXXXX}

## 🔐 Seguridad
No publiques tu BOT_TOKEN ni CHAT_ID en GitHub. Usa variables de entorno o un archivo .env si vas a subirlo públicamente.

## 📬 Prueba manual del script
Para probarlo sin conectarte por SSH:
```bash
SSH_CONNECTION="<IP_CLIENTE> 22 <IP_SERVIDOR> 22" ./ssh-login-notifier.sh

