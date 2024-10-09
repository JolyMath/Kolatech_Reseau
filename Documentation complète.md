# **KOLATECH** 

## Configuration 

* ### **Hyperviseur PROXMOX**

    * information
      * Nom : root
      * Mot de passe : Admlocal1
      * IP : 192.168.1.2:8006
    
    * Que faire si on arrive pas à se connecter a Proxmox ?

        * Regarder si les 2 cartes réseau de VMware et celui de Virtual Box n'a pas une IP 192.168.1
        * Vérifier que le cable est bien brancher au switch 
        * Vérifier que le serveur DHCP est bien allumé 
        * Changer l'IP de la carte ethernet en IP fixe 
        * Appeler Macéo

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
        * Services d'impressions
        * Services de fichiers et de stockage    

    * **Serveur VPN**
        * IP : 192.168.1.7
        * Admin : openvpn
        * Installation : Ubuntu 22.04.3
        * Non d'utilisateur Ubuntu : Proxmox

    * **Serveur Firewall**
        * IP : 192.168.1.254
        * Admin : root
        * Installation : OpenSense    

* ### **Serveur De fichier Trunas**
     * IP : 192.168.1.5
        *  Système de sauvegarde
        * Système de stockage
            * 3 disque en RAID1 virtuel  
            * Partage SMTP
            * Mapper et accèssible pas tous user ad
        * Base de donnée MARIADB
            * 192.168.1.4

   * **Superviseur réseau Zabbix**
      * Admin : Admin
      * IP : 192.168.1.4
    
   * Serveur Web
    
## Matériel 

* ### **Emprunté**

    * 2 Machines
        * Hyperviseur Proxmox : AIF-101303 
        * Trunas : AIF-101305

    * 1 switch
      * Catalyst 2960 series Poe-2024
      * IP : 192.168.0.1

    * 1 Routeur
        * AIF-SWT-03
            * IP : 192.168.1.1
        * No VLAN

    * 3 Nucs
        * 3 Connexions simultanées (chacun peut être sur le serveur AD/ DNS / DHCP)
            * AIF-101098 (PC Mathys)
                * Compte utiisateur Mathys (W11)
                    * Compte Admin_mathys 
            * AIF-101016 (PC Olivia)
                * Compte utilisateur Olivia (W11)
                    * Compte Admin_olivia     
            * AIF-101097 (PC Macéo)
                * Compte utilisateur Macéo (W11)
                    * Compte Admin_macéo 
            * Nom d'admin = Kolatech

            * Si on arrive pas à se connecter au domaine il faut mettre une IP fixe 
        
* ### **Fictifs**

    * 40 ordinateurs
    * 3 PC portable 
    * 3 Imprimantes 

## Securitée

## Nouvel utilisateur 

* Elliot le con

