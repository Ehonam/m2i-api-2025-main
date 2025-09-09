# Instructions pour tester l'image Docker

## Prérequis
- Docker Desktop installé et démarré
- Port 8080 disponible sur votre machine

## Option 1: Utiliser docker build et docker run

### 1. Construire l'image
```bash
docker build -t m2i-api:latest .
```

### 2. Démarrer le conteneur
```bash
docker run -d -p 8080:8080 --name m2i-api-container m2i-api:latest
```

### 3. Vérifier que l'application fonctionne
```bash
# Vérifier les logs
docker logs m2i-api-container

# Tester l'application (une fois qu'elle a démarré)
curl http://localhost:8080
```

### 4. Arrêter et nettoyer
```bash
docker stop m2i-api-container
docker rm m2i-api-container
```

## Option 2: Utiliser docker-compose (Recommandé)

### 1. Démarrer l'application
```bash
docker-compose up -d
```

### 2. Vérifier les logs
```bash
docker-compose logs -f
```

### 3. Tester l'application
```bash
curl http://localhost:8080
```

### 4. Arrêter l'application
```bash
docker-compose down
```

## Commandes utiles pour le débogage

### Entrer dans le conteneur
```bash
docker exec -it m2i-api-container /bin/bash
```

### Vérifier l'état du conteneur
```bash
docker ps
```

### Voir les images disponibles
```bash
docker images
```

## Notes
- L'application Spring Boot démarre généralement sur le port 8080
- Le processus de build peut prendre quelques minutes lors du premier lancement
- Les dépendances Maven sont mises en cache pour accélérer les builds suivants