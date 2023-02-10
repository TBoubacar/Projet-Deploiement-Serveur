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

### Ouvrir le projet Django et modifier le fichier urls.py de l'application <Django/environment/myProjetGNUWebSite/myProjetGNUWebSite/urls.py>
Remplacer : urlpatterns = [
    path('polls/', include('polls.urls')),
    path("admin/", admin.site.urls),
]
Par : 
urlpatterns = [
    path('django/', include('polls.urls')),
    path("django/admin/", admin.site.urls),
]

### Ouvrir le projet Laminas et modifier le fichier module.php de l'application
  1. Modifier le fichier (module/Application/config/module.config.ph) en remplaçant la valeur de route :
            'route'    => '/laminas/'
  2. Modifier le fichier (module/Application/view/layout/layout.phtml) :
            ->prependStylesheet($this->basePath('laminas/css/style.css'))
            ->prependStylesheet($this->basePath('laminas/css/bootstrap.min.css'))
            Et partout ou il y a /img -> /laminas/img, etc.
  3. Modifier le fichier (module/Album/config/module.config.php) :
            'route' => '/laminas/album[/:action[/:id]]',

