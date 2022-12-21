# Projet B

Déploiement d'une application sous forme de Pipeline avec Jenkins.
Ici, application simple avec une page html sur un serveur Apache.

# Contexte
Ici, nous allons utiliser 2 machines virtuelles. Une machine control node qui hébergera ansible et Jenkins et une machine managed node.


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
 - Lancer un build automatiquement après chaque commit.
 - Grâce à une pipeline Jenkins.

### Middleware et services

-   **Github** : Notre gestionnaire de code source.
-   **Ansible version 2.10.8*** : Installé sur le control node.
-  **jenkins version 2.375.1**: Installé sur le managed node.

## Organisation du travail dans le temps

**20 Jours** de projet. 

-   Installation manuelle du produit + rédaction de la documentation
    -   **Outils** : _git_, ansible, jenkins,_linux_, _bash_, _apache_, _html_, etc ..
    - 
-   Automatisation avec Ansible
    -   **Outils** : _git_, apache,_ansible_.
    -   **Ce qu'il faut faire** : Il faut à présent développer un playbook ansible qui permet d'automatiser la création d'une page html dans différents environnements sur un serveur apache.
  
-   Installation Jenkins sur VMware avec Ubuntu 22.04
    -   wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -
    - sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
    - sudo apt update
    - sudo apt install jenkins
    - sudo systemctl start jenkins
    - sudo systemctl status jenkins
  - Ouvrir le pare-feu 
  - sudo ufw allow 8080
  - sudo ufw allow OpenSSH
sudo ufw enable
        
    -   **Outils** : _git_, _vagrant_, _virtualbox_, _vmware_, _bash_
        
       - Installation des différents plugins suggérés + installation plugin ansible.
       
- Réalisation Pipeline : Jenkins_Pipeline sur JenkinsFile.