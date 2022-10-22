Sur quel couches du modèle OSI peut agir Traefik ?
R: Couche application

Qu'est qu'une ingress (vous pouvez faire le lien avec une ingress Kubernetes), un middleware et un plugin Traefik ?
R: Ingress: API qui gère l'accès externe aux services d'un cluster, généralement HTTP.
middleware : permet de changer les requêtes avant qu'elles ne soient envoyer à notre service
plugin : permet d'ajouter des fonctionnalités personnalisées

Quelles expressions d'ingress permettent de capter:
* mondomaine.com/api/* et mondomaine2.fr/api/*
* tondomaine.com/api/* 
?

R: Exemple pour mondomaine.com/api/*

apiVersion: networking.k8s.io/v1
kind: Ingress
spec:
  ingressClassName: nginx
  rules:
  - host: mondomaine.com
    http:
      paths:
      - path: /api/*
        pathType: Prefix
        backend:
          service:
            name: service1
            port:
              number: 80
