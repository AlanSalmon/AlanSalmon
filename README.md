# Salut, moi c'est Alan 👋

**Ingénieur infrastructure / DevOps en construction**, étudiant en Master TRI (Télécom, Réseaux, Informatique) à l'Université Savoie Mont-Blanc, en alternance au Département de la Savoie.

J'aime l'informatique quand elle a une matérialité : des switches, des serveurs, des VMs, des conteneurs… et des réseaux qui tombent. Mon parcours n'a rien de linéaire (maintenance industrielle → réseaux → développement → systèmes → DevOps), et c'est justement ce qui me plaît : comprendre une infra de bout en bout, du câble jusqu'au déploiement.

J'apprends surtout en construisant : la plupart de ce qui est ci-dessous tourne (ou a tourné) sur mon homelab.

🌐 [alansalmon.fr](https://www.alansalmon.fr) · 💼 [LinkedIn](https://www.linkedin.com/in/alan-salmon-a09b50234) · ✉️ contact@alansalmon.fr

---

## 🔭 En ce moment

- ☸️ J'apprends **Kubernetes** sur un cluster k3s monté sur mon Proxmox, provisionné avec **Terraform**
- 🛰️ Je construis **Verkko**, un outil pour cartographier les réseaux privés de mon homelab
- 🇫🇮 J'apprends le **finnois** — *opettelen suomea !* — avec en tête un projet d'installation en Finlande après mon master

---

## 🧱 Projets

| Projet | En bref | Stack |
|---|---|---|
| 🛰️ **Verkko** | Outil web qui scanne mes réseaux privés et liste les appareils connectés : IP, état des VMs, du NAS, plage DHCP. Conçu en POO, documenté avec Sphinx. | Python · POO · Sphinx |
| 🇫🇮 **Opi!** | Plateforme d'apprentissage du finnois (verbes, phrases, vocabulaire), déployée comme une vraie appli en prod sur mon homelab. | Flask · Redis · Docker · k3s · Terraform |
| 🏠 **Homelab** | Mon terrain de jeu : virtualisation, conteneurs, réseau privé monté à la main, cluster Kubernetes. [Voir le schéma ↓](#-homelab) | Proxmox · Debian · Synology · Tailscale |
| 📦 **HomeStock** | Application mobile d'inventaire (iOS/Android) : produits et catégories en CRUD complet, persistance locale, filtrage par catégorie. Construite version après version pour apprendre React Native proprement. | React Native · Expo · TypeScript · SQLite |
| 🛒 **[ContApp](https://www.alansalmon.fr/projects/contapp.html)** | Projet DevOps de groupe (BUT R&T) : déploiement de bout en bout d'une appli e-commerce en microservices. | Python · Flask · NATS · Docker · Kubernetes · OpenStack |
| 🔇 **[Silence Remover](https://www.alansalmon.fr/projects/silence_remover.html)** | Traitement audio : détecte et supprime les silences d'un fichier, avec visualisation des échantillons. | Python · Matplotlib |

> Mes projets sont privés pour l'instant : je les construis avant tout pour apprendre. Je les présente plus en détail sur [mon site](https://www.alansalmon.fr), et je suis toujours partant pour en parler !

---

## 🏠 Homelab

```mermaid
flowchart LR
    internet((Internet)) --> wifi[Wi-Fi partagé]
    wifi --> routeur[Routeur + switchs<br/>réseau privé monté à la main]
    tailscale{{Tailscale<br/>accès à distance}} -.-> routeur

    routeur --> beelink
    routeur --> nas

    subgraph beelink[Mini PC Beelink · Proxmox VE]
        direction TB
        subgraph k3s[Cluster k3s · Terraform]
            vm1[VM Debian]
            vm2[VM Debian]
            vm3[VM Debian]
        end
        lab[VMs de lab<br/>CentOS · Windows]
    end

    subgraph nas[NAS Synology DS923+]
        disques[(Disques des VMs)]
        cm[Container Manager]
    end

    beelink -. stockage .-> disques
    k3s --> opi[Opi!]
```

Quelques choix et contraintes :
- **Pas d'accès à la box** (Wi-Fi partagé en appartement) → j'ai monté mon propre réseau privé derrière, et j'y accède à distance via **Tailscale**
- **Disques des VMs sur le NAS** → le mini PC reste léger, le stockage est centralisé
- **Terraform** pour créer les VMs du cluster plutôt que de les cliquer à la main

---

## 🛠️ Stack

**Infra & systèmes**

![Proxmox](https://img.shields.io/badge/Proxmox-E57000?style=for-the-badge&logo=proxmox&logoColor=white)
![Debian](https://img.shields.io/badge/Debian-A81D33?style=for-the-badge&logo=debian&logoColor=white)
![CentOS](https://img.shields.io/badge/CentOS-262577?style=for-the-badge&logo=centos&logoColor=white)
![Windows Server](https://img.shields.io/badge/Windows%20Server-0078D6?style=for-the-badge&logo=windows&logoColor=white)
![Synology](https://img.shields.io/badge/Synology-B5B5B6?style=for-the-badge&logo=synology&logoColor=black)

**Conteneurs & IaC**

![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)
![k3s](https://img.shields.io/badge/k3s-FFC61C?style=for-the-badge&logo=k3s&logoColor=black)
![Terraform](https://img.shields.io/badge/Terraform-844FBA?style=for-the-badge&logo=terraform&logoColor=white)

**Réseaux & monitoring**

![Cisco](https://img.shields.io/badge/Cisco-1BA0D7?style=for-the-badge&logo=cisco&logoColor=white)
![Tailscale](https://img.shields.io/badge/Tailscale-242424?style=for-the-badge&logo=tailscale&logoColor=white)
![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=for-the-badge&logo=prometheus&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-F46800?style=for-the-badge&logo=grafana&logoColor=white)

**Dev & données**

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![Bash](https://img.shields.io/badge/Bash-4EAA25?style=for-the-badge&logo=gnubash&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-000000?style=for-the-badge&logo=flask&logoColor=white)
![React Native](https://img.shields.io/badge/React%20Native-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=for-the-badge&logo=redis&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)

---

<sub>🏒 Hors écran : fan des Brûleurs de Loups et des Oulun Kärpät.</sub>
