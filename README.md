# TAREA07_SXE 🤌
---
### Creación y configuración del archivo.

<details>
<summary> <b> 1. Para crear y abrir un archivo: </b></summary>
<br>

```bash
# Abre el archivo para editarlo y lo crea si aún no existe
nano docker-compose.yaml
```
</details>

<details>
<summary> <b> 2. Configuración del archivo: </b></summary>
<br>

```yaml
services:
  mysql:
    image: mysql:latest
    volumes:
      - db_data:/var/lib/mysql
    container_name: base2_mysql
    restart: always
    environment:
      MYSQL_DATABASE: joomla_db
      MYSQL_ROOT_PASSWORD: admin
      MYSQL_USER: root
  joomla:
    depends_on:
      - mysql  
    image: joomla:latest
    ports:
      - 8080:80
    container_name: joomla
    restart: always
    environment:    
      JOOMLA_DB_HOST: mysql
      JOOMLA_DB_USER: root
      JOOMLA_DB_PASSWORD: admin
      JOOMLA_DB_NAME: joomla_db
    volumes:
      - joomla_data:/var/www/html
volumes:
  db_data:
  joomla_data:
```
Una vez terminado el archivo de configuración, lo lanzamos utilizando:
```bash
sudo docker compose up -d
```
**Importante hacerlo desde el directorio en el que se encuentra el archivo de configuración ⚠️**

![imagen](https://github.com/user-attachments/assets/8c41baca-c79c-4ee2-89b5-84dfe4e3f1c3)

</details>

<details>
<summary> <b> 3. Pruebas y configuración de PrestaShop: </b></summary>
<br>

```bash
# Utilizo en el navegador la ip de mi ordenador con el puerto seleccionado
10.0.9.153:8080
```
Una vez comprobado que todo funciona correctamente, me pongo a configurar todo desde el navegador ✅

**1. Instalador de Joomla:**
  ![imagen](https://github.com/user-attachments/assets/ef26ebd3-809e-4dbf-b17e-d391c86c54ca)

**2. Configurar datos de acceso.**
  ![imagen](https://github.com/user-attachments/assets/57ff0907-5f0b-4a60-a7c7-300189b7ded2)

**3. Configurar base de datos.**
  ![imagen](https://github.com/user-attachments/assets/808afb11-a47d-4ae5-8d79-081c1503fdff)
  
**4. Comienza la instalación.**
  ![imagen](https://github.com/user-attachments/assets/142c08cc-89c2-468c-96dd-1648c0d7ff86)
  
</details>

