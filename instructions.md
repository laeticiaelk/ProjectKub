<<<<<<< HEAD

# Projet Conteneurisation et Orchestration

## I. Sujet

### Applications

L'objectif est le déploiement, la maintenance et la mise à jour de différents micro-services REST et applications web dans un environnement conteneurisé, avec un orchestrateur Kubernetes afin d'assurer la haute disponibilité des apps.

### Ce qui est fourni

Pour ce projet, je jouerai le rôle du développeur. Vous pourrez donc me poser des questions sur le fonctionnement des apps, ce qu'elles ont besoin en termes de ressources et de liaisons. Si nécessaire, je pourrai modifier le code des applications afin de les adapter à votre système (tant que ça reste de la configuration). Les applications sont disponibles sur le git du cours. Description des apps:

- **web**: application web qui consomme les services `applicants.api` et `jobs.api`
- **applicants.api**: service API REST fournissant des données d'une base de données
- **identity.api**: service API REST fournissant une authentification
- **jobs.api**: service API REST fournissant des données d'une base de données
- **sql.data**: base de données SqlServer et données
- **rabbitmq**: fournit une communication entre les services API REST

Les relations sont décrites dans le fichier `docker-compose`. C'est avec une bonne analyse de ce fichier que vous pourrez connaître les liens entre chaque application et les variables d'environnement.

### Conteneur

Vous devrez créer les fichiers afin de générer des images de conteneur de chaque app. Les apps étant réalisées sur des technologies différentes, il vous faudra bien préparer les images pour que les apps s'exécutent sans problèmes (image de base, ouverture de port, mise en réseau, etc.). Les Dockerfile de chaque élément vous sont fournis. Les images devront par la suite être envoyées vers un repo d'images privé (DockerHub ou Azure).

### Hébergement

Les apps devront être déployées dans Kubernetes. C'est à vous qu'appartient le choix de tous les paramètres (taille du cluster, nombre de nœuds, nombre de réplicas, réseau virtuel, volume physique, pods, services, ingress...) nécessaires pour chaque app. La mise en réseau des conteneurs devra se faire dans le cluster, seules les apps ayant besoin d'être appelées de l'extérieur devront être ouvertes à la communication extérieure. N'oubliez pas d'utiliser les étiquettes afin d'organiser vos éléments de manière plus simple.

Le cluster de production devra être un cluster managé sur Azure (AKS) ou en local.

### Performance

Afin de ne pas avoir de problèmes de surcharge, chaque pod devra avoir une limite de consommation CPU, mémoire et disque ainsi que des demandes de ressources définies. Les pods devront également redémarrer automatiquement s'ils tombent. Il vous faudra définir des "règles d'affinité" entre vos éléments afin d'en améliorer les performances dans les échanges. Ressources par app:

- **web**: CPU 4m, MEM 900Mi
- **applicants.api**: CPU 0.5, MEM 500Mi
- **identity.api**: CPU 0.5, MEM 500Mi
- **jobs.api**: CPU 0.5, MEM 500Mi
- **user.data**: CPU 4m, MEM 500Mi

Ressources limites par app:

- **web**: CPU 1, MEM 2000Mi
- **applicants.api**: CPU 1, MEM 1500Mi
- **identity.api**: CPU 1, MEM 1500Mi
- **jobs.api**: CPU 1, MEM 1500Mi

Affinité:

- **web**: jobs.api et applicants.api
- **jobs.api** et **applicants.api**: sql.data
- **identity.api**: user.data

### Bilan de santé

Votre cluster devra être sous surveillance! Vous devrez réaliser "un bilan de santé" de votre cluster en mettant en place les sondes de préparation et les sondes de vivacité. De même, vous devrez mettre en place les mesures par métrique, les métriques de l'état du cluster, les métriques de ressources des nœuds et des pods ainsi que les métriques de travail du plan de contrôle (Metrics server et kube-state-metrics). Les données seront affichées dans un Prometheus, installé au préalable sur le cluster.

### Sécurité

Vos apps devront être accessibles uniquement par le protocole HTTPS de l'extérieur. Il vous faudra donc générer un certificat (auto-signé) SSL, et l'associer à votre cluster.

### Logs

Les apps font remonter des logs dans la sortie standard. Afin de pouvoir les exploiter correctement, il vous faudra mettre en place une pile complète (EFK ou ELK) afin de fournir une gestion de logs avancée.

### Déploiement automatisé

Afin d'automatiser le déploiement sur d'autres clusters, vous allez mettre en place un système de déploiement automatisé via HELM. Votre paquet HELM devra contenir la création des pods, déploiements, services, ingress mais pas de contrôleur d'ingress.

### Groupes et fonctionnement

// ...additional details about groups and functioning...
=======
# ProjectKub
>>>>>>> 71065c6ea3b7432fc9f5cd54b400ab8f663a4092
