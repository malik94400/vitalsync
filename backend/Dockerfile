# Multi-stage build pour optimiser la taille et la sécurité de l’image.
# Le premier stage installe les dépendances et exécute les tests.
# Le second stage produit une image plus légère de production, sans outils inutiles.

# -------- Stage 1 : test --------
FROM public.ecr.aws/docker/library/node:20-alpine AS builder

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .

RUN npm test

# -------- Stage 2 : production --------
FROM public.ecr.aws/docker/library/node:20-alpine

WORKDIR /app

COPY package*.json ./
RUN npm install --omit=dev

COPY server.js ./

EXPOSE 3000

CMD ["node", "server.js"]