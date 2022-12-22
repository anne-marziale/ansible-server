# Projet B

Déploiement d'Ansible sous forme de Pipeline avec Jenkins.
Ici, nous avons une application simple c'est à dire une page html qui sera héberger sur un serveur Apache.

L'objectif de cette application est d'herberger une page HTML sur différents environnements (Recette 1, Recette 2, etc ...). , grâce à la configuration d'un serveur apache avec Ansible.

![Capture d’écran 2022-12-21 222645](https://user-images.githubusercontent.com/85136214/209154722-dda763f9-4b87-4d49-ad25-b4d29c70ba05.png)


# Contexte
Ici, nous allons utiliser 2 machines virtuelles. Une machine control node qui hébergera Ansible et Jenkins et une machine managed node sur laquelle les tâches ansible seront exécuter.

## Coté Ansible ##

Dans un premier temps nous allons réaliser le dépôt d'un fichier template HTML dans la configuration d'apache grâce au rôle Déploiement qui éxécutera les tâches du rôle sur le playbook.yml. 

Dans les différentes tâches du rôle nous pouvons voir la création et le dépot d'un fichier sur les différents environnements. 

J'ai également modifier la configuration des différents fichiers de configurations d'apache tel que apache.conf (situé dans templates) par exemple, afin de mettre le fichier html direcetement sur le serveur apache. 

Le playbook Ansible s'éxecute grâce à la commande **"ansible-playbook playbooks/playbook.yml"**.

## Coté Jenkins ##

L'objectif va être de déployer via une Pipeline Jenkins le playbook ansible grâce au jenkinsfile.


# Outils utilisés

 -   Ansible
 -  Jenkins
 -   Git
 -   Vmware workstation (Ubuntu 22.04)
 -   Linux (Shell Bash)

## Objectif

 - Installer Ansible
 - Réaliser un git Clone.
 - Déployer playbook ansible 
 - Lancer un build automatiquement après chaque commit, tout ça grâce à une pipeline Jenkins.

### Middleware et services

-   **Github** : Notre gestionnaire de code source.
-   **Ansible version 2.10.8*** : Installé sur le control node.
-  **jenkins version 2.375.1**: Installé sur le managed node.

## Organisation du travail dans le temps

**20 Jours** de projet. 

-   Installation manuelle du produit + rédaction de la documentation
    -   **Outils** : _git_, ansible, jenkins,_linux_, _bash_, _apache_, _html_, etc ..

-   ### Installation OpenSSH pour permettre le remote server sur VSCode. ###

   - sudo apt update && sudo apt upgrade
   - sudo apt install openssh-server
   - sudo systemctl enable --now ssh
   - sudo systemctl status ssh

   - ssh anne@192.168.142.133

-  ### Automatisation avec Ansible. ###
    -   **Outils** : _git_, apache,_ansible_.
    -   **Ce qu'il faut faire** : Il faut à présent développer un playbook ansible qui permet d'automatiser la création d'une page html dans différents environnements sur un serveur apache.

    Lancement playbook Ansible : ansible-playbook playbooks/playbook.yml
  
-   ### Installation Jenkins sur VMware avec Ubuntu 22.04: ###

    -   wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -
    - sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
    - sudo apt update
    - sudo apt install jenkins
    - sudo systemctl start jenkins
    - sudo systemctl status jenkins

  Ouvrir le pare-feu 

    - sudo ufw allow 8080
    - sudo ufw allow OpenSSH
    - sudo ufw enable
        
### JENKINS ###

- Installation des différents plugins suggérés + installation plugin ansible.
- Configuration outil Ansible.
- Mise en place Build Trigger pour que le Build se lance après chaque commit du repository.

![Capture d’écran 2022-12-21 235628](https://user-images.githubusercontent.com/85136214/209156249-65eeba2d-9dff-41c5-a6fc-c9fd9e20c6cd.png)


- Création JenkinsFile

![Capture d’écran 2022-12-21 234815](https://user-images.githubusercontent.com/85136214/209155679-387c1232-29f6-4758-b4c7-d79fc7c6e246.png)

       
- Réalisation Pipeline : Jenkins_Pipeline.

![Capture d’écran 2022-12-22 001124](https://user-images.githubusercontent.com/85136214/209155728-9c6a3f34-be14-496f-999e-d5e0e14ff631.png)
