# Conception d’infrastructure web

Ce projet fait partie du **curriculum Foundations v2.1 - Part 3** de Holberton School.
Il porte sur la conception et l’explication de différentes infrastructures web, leurs composants et leurs limites.

---

## 📚 Concepts abordés

- Bases du réseau
- Serveur
- Serveur web
- DNS
- Load balancer
- Monitoring
- Bases de données
- HTTPS et pare-feu
- Haute disponibilité et redondance

---

## 🎯 Objectifs pédagogiques

À la fin de ce projet, vous devez être capable d’expliquer (sans l’aide de Google) :

- Comment dessiner et décrire un diagramme d’infrastructure web.
- Le rôle de chaque composant de la pile.
- Ce que signifie la redondance système et comment l’atteindre.
- La signification des acronymes comme **LAMP**, **SPOF** et **QPS**.
- La différence entre un serveur web et un serveur applicatif.
- Les principaux types d’enregistrements DNS et leurs usages.
- Les bases de l’équilibrage de charge et du clustering de bases de données.
- Les problèmes courants liés à la sécurité, la montée en charge et le monitoring.

---

## 📝 Exigences

- Toutes les explications et diagrammes doivent être rédigés en **anglais** (pour l’évaluation Holberton).
- Chaque tâche nécessite un **schéma sur tableau blanc** (papier, logiciel ou outil de votre choix).
- Une **capture d’écran/photo** de chaque schéma doit être envoyée via un service d’hébergement d’images (ex : Imgur).
- Le lien vers la capture doit être inséré dans le fichier de réponse.
- Lors de la revue manuelle, vous devrez **présenter vos schémas au tableau** (sans notes ni ordinateur).
- Gardez vos explications claires et concises. Concentrez-vous uniquement sur ce qui est demandé.

---

## 📂 Dépôt

- **Dépôt GitHub :** `holbertonschool-system_engineering-devops`
- **Dossier :** `web_infrastructure_design`

---

## 📌 Tâches

### 0. Simple web stack

Concevoir une infrastructure à **un serveur** hébergeant `www.foobar.com`.

**Exigences :**

- Nom de domaine `foobar.com` avec un enregistrement `www` pointant vers l’IP du serveur `8.8.8.8`.
- Un serveur comprenant :
  - Un serveur web (**Nginx**)
  - Un serveur applicatif
  - Les fichiers de l’application (code)
  - Une base de données (**MySQL**)

**Être capable d’expliquer :**

- Ce qu’est un serveur.
- Le rôle d’un nom de domaine.
- Le type d’enregistrement DNS que représente `www`.
- Le rôle de chaque composant (serveur web, serveur applicatif, base de données).
- Comment le serveur communique avec l’ordinateur de l’utilisateur.
- Les limites de l’infrastructure : **SPOF**, indisponibilité lors de la maintenance, impossibilité de gérer beaucoup de trafic.

**Fichier :** `0-simple_web_stack`

---

### 1. Distributed web infrastructure

Concevoir une infrastructure à **trois serveurs** hébergeant `www.foobar.com`.

**Exigences :**

- Un **load balancer (HAProxy)**
- Deux serveurs, chacun comprenant :
  - Un serveur web (**Nginx**)
  - Un serveur applicatif
  - Les fichiers de l’application
  - Une base de données (**MySQL**)

**Être capable d’expliquer :**

- Pourquoi chaque nouvel élément est ajouté.
- Les algorithmes d’équilibrage de charge et la différence entre **active-active** et **active-passive**.
- Le fonctionnement d’un cluster de base de données **primaire-réplique (master-slave)**.
- La différence entre le nœud primaire et le nœud réplique.
- Les limites : présence de **SPOF**, absence de HTTPS/pare-feu, absence de monitoring.

**Fichier :** `1-distributed_web_infrastructure`

---

### 2. Secured and monitored web infrastructure

Concevoir une infrastructure à trois serveurs sécurisée, chiffrée et surveillée.

**Exigences :**

- Trois pare-feu
- Un certificat SSL pour le HTTPS
- Trois agents de monitoring (ex : Sumo Logic)

**Être capable d’expliquer :**

- Pourquoi chaque nouvel élément est ajouté.
- Le rôle des pare-feu.
- L’importance du HTTPS.
- L’utilité du monitoring et comment il collecte des données.
- Comment surveiller le **QPS** (requêtes par seconde).
- Les problèmes : terminaison SSL au niveau du load balancer, base MySQL unique pour l’écriture, serveurs identiques pouvant poser problème.

**Fichier :** `2-secured_and_monitored_web_infrastructure`

---

### 3. Scale up

Améliorer la scalabilité en séparant les composants.

**Exigences :**

- Un serveur supplémentaire.
- Un second load balancer en cluster (**HAProxy**).
- Séparer les rôles sur des serveurs dédiés :
  - Serveur web
  - Serveur applicatif
  - Base de données

**Être capable d’expliquer :**

- Pourquoi chaque nouvel élément est ajouté.

**Fichier :** `3-scale_up`

---

## ⚠️ Notes

- La clarté et la simplicité priment dans les schémas.
- Ne pas entrer dans des détails inutiles si ce n’est pas demandé.
- Toujours penser en termes de **SPOF, scalabilité et sécurité**.

---
