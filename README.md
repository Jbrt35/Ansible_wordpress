# Ansible_wordpress
Playbook Ansible pour le déploiement automatique de Wordpress seulement pour Debian. 

Ce playbook permet d'installer automatique Wordpress. Seule la configuration de MariaDB n'est pas automatisé

# Architecture
'''
Ansible_wordpress/
│
├── wordpress-config.php.yaml.j2 
├── wordpress.conf.j2
├── wordpress_install.yaml  
├── hosts.ini             
└── README.md
'''
# Prérequis

Installation de curl nécessaire avant d'éxécuter le playbook

# Lancement du script Ansible

Clonage du dépot Github:
'''
git clone https://github.com/Jbrt35/Ansible_wordpress.git
cd Ansible_wordpress
'''

sudo ansible-playbook -i hosts.ini wordpress_install.yml

L'automatisation de la configuration de la base de donnée MySQL n'a pas été automatisé, l'utilisateur doit donc la faire et la modifier dans le fichier /var/www/html/wordpress/wp-config.php en remplacant les identifiants par défault de la BDD par les siens

'''
sudo mysql -u root -p
CREATE DATABASE wordpress;
CREATE USER 'wordpress'@'localhost' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON wordpress.* TO 'wordpress'@'localhost';
FLUSH PRIVILEGES;
EXIT;

'''
