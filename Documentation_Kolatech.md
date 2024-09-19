# **KOLATECH** 

## Configuration 

* **Hyperviseur PROXMOX**

    * information
      * nom : root
      * mot de passe : Admlocal1
      * IP : 192.168.1.2:8006
    
    * Que doit on faire pour pouvoir supprimer une OU 
      * Activer l'affichage de fonctionnalités avancées 
      * Faire un clique droit puis propriété sur l'OU souhaité
      * allez sur l'onglet objet 
      * décocher l'option protégé l'objet des suppressions accidentées

    * Comment activé la corbeille sur l'active directory 
      * il faut aller sur le centre d'administration de l'active directory 
      * il faut faire un clique droit sur le contrôleur de domaine souhaité puis presser sur activer la corbeille
      * maintenant quand vous effacerez un utilisateur, un groupe, une OU vous pourrez les restaurés dans la corbeille 
 

    * Que faire si on arrive pas à se connecter 
       * regarder si les 2 cartes réseau de VMware et celui de virtual box n'a pas une IP 192.168.1
       * Vérifier que le cable est bien brancher au switch 
       * Vérifier que le serveur DHCP est bien allumé 
         * changer l'IP de la carte ethernet en IP fixe 
        * Appeler macéo  

    * Serveur De fichier Trunas
        * IP : 192.168.1.5
        * Nom d'utilisateur : admin
        * Système de sauvegarde
        * Système de stockage
   
   * Serveur ADDS DNS DHCP
     * Admin : Administrateur
     * IP : 192.168.1.3
     * masque : 255.255.254.0
     * Domaine contrôleur 
        * AD
        * DNS
        * DHCP 
     
   
   * Serveur VPN
     * openvpn
       * IP : 192.168.1.7
       * Admin : openvpn
     * Ubuntu 22.04.3
       * Admin : Proxmox
   
   * Serveur d'impression
   * Serveur Web
   * Superviseur réseau
   * 3 Connexion simultanées au serveur ADDS DNS DHCP 
   * Serveur de Base de donnée
    
## Matériel 
* pc mathys 
  * IP Wifi : 192.168.1.12


* Emprunté
    * 2 Machine
        * AIF-101303 
        * AIF-101305
    * 2 Switch 
         * IP : 192.168.0.13
         * IP : 192.168.0.12
         * AIF-100948-030
         * AIF-100811-014
         * VLAN
         * nom d'utilisateur : cisco 
    * 1 Multi-prise
         * AIF-MP-08
    * 1 routeur
        * No VLAN
        * AIF-SWT-08
        * Port 4 ouvert
        * IP : 192.168.1.1  
    * 3 Nuc
        * IP macéo : 192.168.1.34
        * IP mathys : 192.168.0.17
          * Compte utilisateur Macéo (W11)
            * Compte Admin_macéo 
          * Compte utiisateur Mathys (W11)
            * Compte Admin_mathys
          * Compte utilisateur Olivia (W11)
            * Compte Admin_olivia
        * Nom d'admin = Kolatech
        * AIF-101100 
        * AIF-101016
        * AIF-101097
        * si on arrive pas à se connecter au domaine il faut mettre une IP fixe 
        
        
* Fictif
    * 40 PC 
    * 3 PC portable 
    * 4 Imprimante 

## Securitée



