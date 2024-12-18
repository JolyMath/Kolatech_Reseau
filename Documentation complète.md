# **KOLATECH**
   
* **Présentation de l'entreprise**

     * Nom de l'entreprise : Kolatech
     * Nombre d'employés : 50

     * Départements
        * Direction
        * RH
        * Administration
        * Recherche et Développement
        * Marketing
        * Juridique
        * Finance

## Matériel Emprunté et Configuration

* ### **Serveur Hyperviseur PROXMOX**

    * Numéro se série : AIF-101303
    * Nom : root
    * IP : 192.168.1.2
    
    * Que faire si on arrive pas à se connecter a Proxmox ?

        * Regarder si les 2 cartes réseau de VMware et celui de Virtual Box n'a pas une IP 192.168.1
        * Vérifier que le cable est bien brancher au switch 
        * Vérifier que le serveur DHCP est bien allumé 
        * Changer l'IP de la carte ethernet en IP fixe (sur notre poste)

    * **Serveur ADDS/ DNS/ DHCP**
        * Admin : Administrateur
        * IP : 192.168.1.3
        * masque : 255.255.254.0
        * Domaine contrôleur 
            * AD
                * Comment activé la corbeille sur l'active directory ? 

                    1. Il faut aller sur le centre d'administration de l'active directory 
                    2. Il faut faire un clique droit sur le contrôleur de domaine souhaité puis presser sur activer la corbeille
                    3. Maintenant quand vous effacerez un utilisateur, un groupe, une OU vous pourrez les restaurés dans la corbeille

                * Que doit on faire pour pouvoir supprimer une OU ?

                    1. Activer l'affichage de fonctionnalités avancées 
                    2. Faire un clique droit puis propriété sur l'OU souhaité
                    3. allez sur l'onglet objet 
                    4. décocher l'option protégé l'objet des suppressions accidentées     
            * DNS
            * DHCP
            * **ATTENTION si le client et le serveur sont décalés de 5 min sur l'horaire la connexion ne se fait pas !**  

    * **Serveur VPN**
        * Non d'utilisateur Ubuntu : Proxmox
        * IP : 192.168.1.7
        * Admin : openvpn
        * Installation : Ubuntu

    * **Serveur Firewall**
        * IP : 192.168.1.254
        * Admin : root
        * Installation : OpenSense

    * **Serveur téléphonique**
        * Admin : root
        * IP : 192.168.1.12   

* ### **Serveur De Fichiers Trunas**

    * Numéro de série : AIF-101305
    * Admin : admin
    * IP : 192.168.1.5
    * Système de sauvegarde
    * Système de stockage
        * 3 disque en RAID1 virtuel  
        * Partage SMTP
        * Mapper et accessible pas tous user AD

   * **Superviseur réseau Zabbix**
      * Admin : Admin
      * IP : 192.168.1.4
   
* ### **Serveur De Backups**
    * Numéro de série : AIF-101308
    * IP : 192.168.0.8

* #### **3 Nucs**
    * Installation Windows 11
    * 3 Connexions simultanées (chacun peut être sur le serveur AD/ DNS / DHCP)
        * AIF-101098 (PC Mathys)
            * Compte Admin_mathys 
        * AIF-101016 (PC Olivia)
            * Compte Admin_olivia     
        * AIF-101097 (PC Macéo)
            * Compte Admin_macéo
         
* #### **NAS**
    * TR-002    

*  #### **3 souris filaires**
    * AIF-SOU-05
    * AIF-SOU-06
    * AIF-SOU-07            

* ### **Matériel Réseau Emprunté**

* **Switch Cisco**
    * Numéro de série : Catalyst 2960 series Poe-2024
    * Admin : admin ou root
    * IP : 192.168.0.1

* **1 Routeur**
    * Numéro de série : AIF-SWT-03
    * IP : 192.168.1.1
    
* **11 câbles RJ45**

* **2 Multiprises**

* **1 rallonge**
        
* ### **Matériel Fictifs**

    * 40 ordinateurs
    * 3 PC portable 
    * 3 Imprimantes 

## Sécuritée
* ### **Mise en place GPO et Règle de mot de passe**

### 1. Gestion des utilisateurs
1. **Active Directory Administrative Center** > `mycompany` > `system` > `password settings container`
2. Pour déverrouiller un utilisateur :
   - Aller dans **Vue d’ensemble** > **Recherche globale** > chercher l’utilisateur
   - Dans l’onglet de droite, sélectionner **Déverrouiller**

### 2. Fond d’écran commun
1. Tapez `GPMC.msc`
2. Aller dans l'OU des utilisateurs (**OU_Users**)
3. Faites un clic droit sur l’OU et choisissez **Créer un objet GPO dans ce domaine, et le lier ici...**
4. Donnez un nom à la GPO (par exemple, "Fond d'écran").
5. Clic droit sur la GPO > **Modifier**
6. Naviguez vers : **Configuration utilisateur** > **Stratégies** > **Modèles d'administration** > **Bureau** > **Bureau**
7. Recherchez la stratégie appelée **Papier peint** et double-cliquez dessus.
8. Activez cette stratégie.
9. Dans le champ **Nom du papier peint**, entrez le chemin UNC vers l’image du fond d’écran (qui doit être sur le lecteur réseau).
10. Allez dans : **Configuration utilisateur** > **Stratégies** > **Modèles d'administration** > **Panneau de configuration** > **Affichage**
11. Activez l'option **Empêcher la modification du papier peint**

### 3. Thème sombre
1. **Créer une nouvelle GPO** :
   - Clic droit sur l'OU où vous souhaitez appliquer la GPO (par exemple, sur les utilisateurs concernés), puis cliquez sur **Créer un objet de stratégie de groupe** et donnez un nom à la GPO (par exemple, "Forcer thème sombre").
2. **Modifier la GPO** :
   - Clic droit sur la GPO que vous venez de créer, puis sélectionnez **Modifier**.
3. **Naviguer vers la section des préférences du registre** :
   - Allez dans **Configuration utilisateur** > **Préférences** > **Paramètres Windows** > **Registre**
   - Clic droit dans le volet de droite, puis sélectionnez **Nouveau** > **Valeur du Registre**
4. **Ajouter les clés de registre pour activer le thème sombre** :
   - **Clé 1** (Pour les applications en mode sombre) :
     - Chemin de la clé : `HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Themes\Personalize`
     - Mettre a jour
     - Valeur : `AppsUseLightTheme`
     - Type : `REG_DWORD`
     - Donnée : `0` (0 = sombre, 1 = clair)
   - **Clé 2** (Pour l'interface système en mode sombre) :
     - Chemin de la clé : `HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Themes\Personalize`
     - Mettre a jour
     - Valeur : `SystemUsesLightTheme`
     - Type : `REG_DWORD`
     - Donnée : `0` (0 = sombre, 1 = clair)

### 4. GPO pour bloquer l'accès au Panneau de configuration
Windows offre une stratégie de groupe intégrée pour désactiver l'accès au Panneau de configuration et à Paramètres.

#### Étapes :
1. **Créer une nouvelle GPO** :
   - Clic droit sur l'OU où vous souhaitez appliquer la GPO (par exemple, sur les utilisateurs concernés), puis cliquez sur **Créer un objet de stratégie de groupe** et nommez-le (par exemple, "Bloquer Panneau de configuration").
2. **Modifier la GPO** :
   - Clic droit sur la nouvelle GPO, puis sélectionnez **Modifier**.
3. **Naviguer vers les paramètres** :
   - Allez dans **Configuration utilisateur** > **Stratégies** > **Modèles d'administration** > **Panneau de configuration**.
4. **Configurer l'option de blocage** :
   - Recherchez le paramètre appelé **Interdire l'accès au panneau de configuration et aux paramètres PC**.
   - Double-cliquez dessus et sélectionnez **Activé**.
   - Cliquez sur **OK** pour appliquer.
5. **Appliquer la GPO** :
   - Fermez l'éditeur et assurez-vous que la GPO est liée à l'OU contenant les utilisateurs concernés.
6. **Forcer la mise à jour des GPO sur les postes clients** :
   - Exécutez `gpupdate /force` ou attendez l'application automatique.
```
