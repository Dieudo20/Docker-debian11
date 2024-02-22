# Docker-debian11
# Installation et configuration de Docker sous l'environnement linux
# Mise à jour du système

    sudo apt update
    sudo apt upgrade -y

# Installation de Docker

# Nous allons maintenant installer Docker. Exécutez les commandes suivantes pour ajouter le référentiel officiel Docker à votre système et installer Docker :

    sudo apt install curl gnupg lsb-release
    curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
    echo \
    "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/debian \
    $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
    sudo apt update
    sudo apt install docker-ce docker-ce-cli containerd.io

# Une fois l'installation terminée, vérifiez si Docker est correctement installé en exécutant la commande ci-dessous :

    docker --version

# Cela devrait afficher la version actuelle de Docker installée sur votre système.
# Configuration de Docker
# Par défaut, le service Docker ne démarrera pas automatiquement après l'installation. 
# Pour démarrer le service Docker au démarrage du système, exécutez les commandes suivantes :

    sudo systemctl enable docker
    sudo systemctl start docker

# Vous pouvez également vérifier l'état du service Docker en utilisant la commande suivante :

    sudo systemctl status docker

# Pour éviter de taper sudo chaque fois que vous utilisez des commandes Docker, 
# vous pouvez ajouter votre utilisateur actuel au groupe docker. 
# Exécutez la commande suivante en remplaçant <your-username> par votre nom d'utilisateur actuel :

    sudo usermod -aG docker <your-username>

# Ensuite, quittez la session actuelle et connectez-vous à nouveau pour que les modifications prennent effet. 
# Vous pouvez vérifier si vous faites partie du groupe docker en exécutant la commande suivante :

    groups <your-username>

