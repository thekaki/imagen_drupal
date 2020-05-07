#En primer lugar iniciaremos mysql y apache
systemctl start apache2
systemctl start mysql

#Configuracion de la base de datos
sudo mysql -e "CREATE DATABASE bd CHARACTER SET utf8 COLLATE utf8_Spanish_ci;"
#Creamos el usuario
sudo mysql -e "CREATE USER 'usuario'@'bd' identified by 'usuario';"
#Otorgamos los privilegios
sudo mysql -e "GRANT ALL PRIVILEGES ON bd.* to 'usuario' IDENTIFIED BY 'usuario';"
sudo mysql -e "FLUSH PRIVILEGES;"

#Reiniciamos los servicios
systemctl restart apache2
systemctl restart mysql
