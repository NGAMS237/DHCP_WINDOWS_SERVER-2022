# DHCP_WINDOWS_SERVER-2022
Configuration d'un Serveur DHCP sur Windows Server 2022


## 📌 Objectif
Ce projet documente l'installation et la configuration d'un serveur **DHCP** sur **Windows Server 2022**. Il montre comment centraliser la distribution d'adresses IP dans un réseau et remplacer un serveur DHCP existant (ex. un routeur IPFire).

---

## 🛠️ Prérequis

- **Windows Server 2022** installé et configuré.
- **Accès administrateur** sur le serveur.
- **Un routeur (IPFire ou autre)** avec le DHCP désactivé.

---

## 🔹 Étape 1 : Installation du rôle DHCP
1. Ouvrir le **Gestionnaire de serveur**.
2. Aller dans **Ajouter des rôles et fonctionnalités**.
3. Sélectionner **Installation basée sur un rôle ou une fonctionnalité** et cliquer sur **Suivant**.
4. Choisir le serveur et cliquer sur **Suivant**.
5. Cocher **Serveur DHCP** puis **Suivant** jusqu’à l’installation.
6. Une fois terminé, fermer l’assistant.

---

## 🔹 Étape 2 : Configuration du DHCP
1. Retourner dans le **Gestionnaire de serveur**.
2. Cliquer sur la notification indiquant une configuration requise et sélectionner **Terminer la configuration DHCP**.
3. Ouvrir **DHCP Manager** (`dhcpmgmt.msc`).
4. Faire un clic droit sur le serveur DHCP et sélectionner **Nouvelle étendue**.
5. Configurer :
   - **Nom de l’étendue** : `LAN-Clients`
   - **Plage d’adresses IP** : `192.168.1.100 - 192.168.1.200`
   - **Masque de sous-réseau** : `255.255.255.0`
   - **Passerelle** : `192.168.1.1` (IP du routeur/IPFire)
   - **Serveurs DNS** : `8.8.8.8`, `8.8.4.4` (ou IP locale d’un serveur DNS)
6. Activer l’étendue et **appliquer les changements**.

---

## 🔹 Étape 3 : Désactiver le DHCP d’IPFire
1. Accéder à **IPFire** via `https://<IP_IPFire>:444`.
2. Aller dans **Network > DHCP Server**.
3. Désactiver **Enabled** et enregistrer.
4. Redémarrer IPFire pour appliquer les changements.

---

## ✅ Vérification
- Redémarrer un PC client et exécuter `ipconfig /all`.
- Vérifier qu’il reçoit bien une IP de **Windows Server 2022**.
- S’assurer que **IPFire ne distribue plus d’IP**.
- Vérifier que le pare-feu Windows autorise les ports **UDP 67 et 68**.

---

## 📢 Partage
📌 Ce projet est documenté pour aider les **administrateurs système** et les **étudiants en IT** à implémenter un serveur DHCP sous **Windows Server 2022**.

📌 **N’hésitez pas à partager vos retours et améliorations !** 🚀

📌 Retrouvez-moi sur **LinkedIn** pour plus de projets IT : www.linkedin.com/in/blaisenganbou237


