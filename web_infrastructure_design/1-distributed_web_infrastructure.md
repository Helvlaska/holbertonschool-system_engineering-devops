# 1. Infrastructure web distribuée

## 📌 Description

Cette infrastructure distribuée héberge `www.foobar.com` en utilisant **trois serveurs** et un **load balancer**.
Elle améliore la disponibilité et permet de répartir le trafic entrant.

L’infrastructure comprend :

- **Un load balancer (HAProxy)**
- **Deux serveurs**, chacun contenant :
  - Un serveur web (**Nginx**)
  - Un serveur applicatif
  - Les fichiers de l’application (code)
  - Une base de données (**MySQL**)

---

## 🌍 Fonctionnement (flux utilisateur)

1. L’utilisateur tape `www.foobar.com` dans son navigateur.
2. Le **DNS** résout le nom de domaine vers l’adresse IP du load balancer.
3. Le **load balancer (HAProxy)** reçoit la requête et la distribue à l’un des deux serveurs.
4. Chaque serveur traite la requête :
   - **Nginx** reçoit la requête HTTP.
   - Le **serveur applicatif** exécute la logique et interroge la **base de données MySQL** si nécessaire.
   - La réponse est renvoyée à Nginx.
5. Le serveur envoie la réponse au **load balancer**.
6. Le load balancer renvoie la réponse finale au navigateur de l’utilisateur.

---

## 🔧 Explication des composants

- **Load balancer (HAProxy)** → répartit le trafic entre plusieurs serveurs pour éviter la surcharge.
- **Algorithme de répartition** → round-robin, least-connections, ou IP-hash.
- **Active-Active vs Active-Passive** :
  - *Active-Active* : les deux serveurs traitent le trafic simultanément.
  - *Active-Passive* : un serveur est actif, l’autre en attente.
- **Cluster de base de données (primaire-réplique)** :
  - *Nœud primaire* : gère les écritures et mises à jour.
  - *Nœud réplique* : gère les lectures, pour améliorer les performances et assurer une redondance.

---

## ⚠️ Problèmes et limites

- **SPOF** :
  - Le load balancer lui-même peut être un point de défaillance unique.
- **Sécurité** :
  - Pas de pare-feu.
  - Pas de HTTPS.
- **Pas de monitoring** :
  - Les pannes ou problèmes de performance ne sont pas détectés.

---

## 📸 Diagramme (Infrastructure distribuée)

```mermaid
  flowchart TD
    U[Client] --> DNS[(DNS)]
    DNS --> LB["Load Balancer - HAProxy"]

    LB --> S1
    LB --> S2

    subgraph S1 [Server 1]
        N1["Nginx"]
        A1[App Server]
        C1[App Files]
        D1[(MySQL DB - Primary)]
        N1 --> A1 --> C1
        A1 --> D1
    end

    subgraph S2 [Server 2]
        N2["Nginx"]
        A2[App Server]
        C2[App Files]
        D2[(MySQL DB - Replica)]
        N2 --> A2 --> C2
        A2 --> D2
    end

    %% Synchronisation DB
    D1 --> D2

```
