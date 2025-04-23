# mongodb_docker

# INSTALLATION DE MONGODB AVEC DOCKER

Lien visuel du projet (Excalidraw) : [https://app.excalidraw.com/l/xeZ46ZHduM/6BRjTlhGznt](https://app.excalidraw.com/l/xeZ46ZHduM/6BRjTlhGznt)

---

## 1. Télécharger MongoDB Compass

Accéder au téléchargement officiel :  
 [https://www.mongodb.com/products/tools/compass](https://www.mongodb.com/products/tools/compass)

---

## 2. Rechercher MongoDB sur Docker Hub

Accéder : [https://hub.docker.com/](https://hub.docker.com/)  
Dans la barre de recherche, taper : `mongodb`

- **Récupérer l'image** : application
- **Conteneur** = application configurée et déployée

---

## 3. Depuis VS Code

- Ouvrir ton dossier projet
- Installer l'extension Docker :  
  [VS Code Docker Extension](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-docker)

---

## 4. Créer un fichier `docker-compose.yml`

Documentation officielle MongoDB Docker :  
 [https://hub.docker.com/\_/mongo](https://hub.docker.com/_/mongo)

```yaml
version: "3.8" # Version du fichier Compose

services:
  mongodb:
    image: mongo:7.0.8 # Version stable de MongoDB
    restart: always # Redémarrage automatique du conteneur
    ports:
      - "8090:27017" # Port local:port interne MongoDB
    environment:
      MONGO_INITDB_ROOT_USERNAME: utilisateur
      MONGO_INITDB_ROOT_PASSWORD: motdepasse
```

> Comme tu utilises Docker Compose, pas besoin de `docker run`, utilise simplement :

```bash
docker-compose up -d
```

---

## 5. Ouvrir Docker Desktop

Si Docker ne se lance pas :
[https://www.docker.com/products/docker-desktop/](https://www.docker.com/products/docker-desktop/)

---

## 6. Connexion avec MongoDB Compass

1. Cliquer sur **"New Connection"**
2. Remplacer :
   ```
   mongodb://localhost:27017/
   ```

```
   par :
```

mongodb://utilisateur:motdepasse@localhost:8090

````
3. Dans "Options" > "Authentication" :
   - Username : `utilisateur`
   - Password : `motdepasse`
   (ce sont les identifiants définis dans `docker-compose.yml`)

---

##  Pour réutiliser le projet plus tard (relancer tout)

1. Ouvrir Docker Desktop
    Ou le télécharger si absent : [https://www.docker.com/products/docker-desktop/](https://www.docker.com/products/docker-desktop/)
2. Ouvrir le dossier VS Code (`mongodb_docker`)
3. Dans un terminal VS Code :
```bash
docker-compose up -d
````

4. Ouvrir MongoDB Compass et utiliser la connexion enregistrée

---

## Port par défaut MongoDB

- Doc officielle : [https://www.mongodb.com/docs/manual/reference/default-mongodb-port/](https://www.mongodb.com/docs/manual/reference/default-mongodb-port/)
- Par défaut : `27017`, mais ici redirigé en `8090:27017` dans Docker

---

## Tags et versions MongoDB Docker

Voir toutes les versions ici :  
 [https://hub.docker.com/\_/mongo/tags](https://hub.docker.com/_/mongo/tags)

---
