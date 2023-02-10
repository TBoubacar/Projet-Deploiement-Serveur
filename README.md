# Projet-Deploiement-Serveur
Création de deux mini-site web avec le framework Django et Laminas suivi d'un déploiement sur un serveur web. 

# Préambule
Il faudrait créer un environnement virtuel en python
Installer toutes les outils nécessaires à la création de notre plateforme web (Python<3>, Django, PHP<8.1>, etc.)
Suivre les informations permettant la mise en place de notre site via le cours CultureGNULinux

#### BEFORE INSTALLATION
change the file hosts.yml to be able to modify your KVM.

#### INSTALLATION OF LAMINAS
ansible-playbook install_laminas_project.yml -i hosts.yml

#### INSTALLATION OF DJANGO
ansible-playbook install_django_project.yml -i hosts.yml

#### INSTALLATION OF APACHE
ansible-playbook install_apache.yml -i hosts.yml

#### LAUNCH DJANGO'S SERVER
On your KVM, launch this command :
uwsgi --ini /root/uwsgi.ini
