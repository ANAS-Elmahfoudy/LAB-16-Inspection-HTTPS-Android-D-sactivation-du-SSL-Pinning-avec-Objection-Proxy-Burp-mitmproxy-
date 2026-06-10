# LAB-16-Inspection-HTTPS-Android-D-sactivation-du-SSL-Pinning-avec-Objection-Proxy-Burp-mitmproxy-
# 🌐 LAB 16 : Inspection HTTPS — Désactivation Automatisée du SSL Pinning avec Objection Framework

## 📝 Description du Projet
Ce laboratoire approfondit les techniques d'**interception des flux chiffrés HTTPS** en mettant l'accent sur l'automatisation du contournement du **SSL Pinning**[cite: 10]. En utilisant le framework **Objection**, nous neutralisons à la volée les mécanismes de validation des certificats de l'application Android sans écrire de code, permettant une capture fluide du trafic via des proxys avancés comme **Burp Suite** ou **mitmproxy**[cite: 10].

---

## 🛠️ Stack Technique & Outils
* **Runtime Exploration Framework :** Objection (Frida-powered)[cite: 10]
* **Proxys d'interception :** Burp Suite / mitmproxy[cite: 10]
* **Environnement de Test :** Émulateur Android rooté connecté via ADB[cite: 10]
* **Objectif :** Automatisation du débogage réseau et audit de la couche de transport[cite: 10]

---

## 🚀 Étapes de l'Audit & Preuves en Images

### Étape 1 : Analyse préliminaire du trafic et configuration du Proxy
Mise en place de l'écouteur proxy sur la machine hôte et redirection du trafic de l'appareil Android pour identifier les endpoints cibles.
<img width="1533" height="404" alt="Configuration et écoute du proxy réseau" src="https://github.com/user-attachments/assets/47c2eb28-40e7-4c93-bf93-090368aa1e2e" />

### Étape 2 : Initialisation d'Objection et attachement au processus
Lancement du shell interactif d'Objection en s'attachant au package de l'application Android dès son démarrage.
<img width="1023" height="100" alt="Lancement du shell interactif Objection" src="https://github.com/user-attachments/assets/2ce3f5f8-0860-4bae-88da-26e9f5f045cd" />

### Étape 3 : Exécution de la commande de désactivation SSL (Bypass)
Injection de la commande intégrée `android sslpinning disable`. Objection se charge d'identifier et de hooker automatiquement les APIs réseaux de l'application pour accepter tous les certificats.
<img width="944" height="133" alt="Exécution du module android sslpinning disable" src="https://github.com/user-attachments/assets/deab7a01-0092-4892-9fb1-6722c8efb620" />

### Étape 4 : Interception et analyse complète des flux HTTPS en clair
Une fois le mécanisme désactivé, l'application transmet ses données de manière transparente à travers le proxy, permettant d'inspecter les requêtes (headers, payloads, tokens) en clair.
<img width="1473" height="347" alt="Capture et inspection du trafic HTTPS en clair" src="https://github.com/user-attachments/assets/e85ce466-04b6-45fa-ae94-1371c91d7837" />

---

## 📊 Informations du Rapport

* **Auditeur :** Anas El Mahfoudy
* **Établissement :** École Marocaine des Sciences de l'Ingénieur (EMSI)
* **Spécialité :** Sécurité Mobile / Analyse Dynamique des Protocoles[cite: 10]

---

## 🔍 Concepts Clés & Conclusion d'Expert
1. **L'efficacité d'Objection :** Ce lab montre la supériorité d'Objection pour le pentest rapide. Au lieu de chercher manuellement si l'application utilise *OkHttp3*, *Volley* ou des *WebViews*, la commande unifiée désactive globalement ces frameworks en une seule action[cite: 10].
2. **Vulnérabilité des architectures mobiles :** La réussite de ce bypass confirme que le SSL Pinning, bien que nécessaire, ne doit jamais être considéré comme une barrière absolue si l'attaquant maîtrise l'appareil client. La véritable sécurité des données doit être assurée par un contrôle strict des entrées/sorties côté serveur (API Security).
