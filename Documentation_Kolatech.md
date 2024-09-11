# **KOLATECH** 

## Configuration 

* **Hyperviseur PROXMOX**

    * information
      * nom : root
      * mot de passe : Admlocal1
      * IP : 192.168.1.2:8006

    * Que faire si on arrive pas à se connecter 
       * regarder si les 2 cartes réseau de VMware et celui de virtual box n'a pas une IP 192.168.1
       * Vérifier que le cable est bien brancher au switch 
       * Vérifier que le serveur DHCP est bien allumé 
         * changer l'IP de la carte ethernet en IP fixe 
        * Appeler macéo  

    * Domaine contrôleur 
        * AD
        * DNS
        * DHCP 

    * Serveur De fichier
        * Système de sauvegarde
        * Système de stockage
   
   * Serveur ADDS DNS DHCP
     * Admin : Administrateur
     
   
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

* Emprunté
    * 2 Machine
        * AIF-101303 
        * AIF-101305
    * 1 Switch 
         * AIF-100811-014
         * VLAN
    * 1 Multi-prise
         * AIF-MP-08
    * 1 routeur
        * No VLAN
        * AIF-SWT-08
        * Port 4 ouvert  
    * 1 Nuc
        * Hyperviseur Proxmox 
          * Compte utilisateur Macéo (W11)
          * Compte utilisateur Mathys (W11)
          * Compte utilisateur Olivia (W11)
        * Nom d'admin = Kolatech
        * AIF-101100 
        * si on arrive pas à se connecter au domaine il faut mettre une IP fixe 
        
        
* Fictif
    * 40 PC 
    * 3 PC portable 
    * 4 Imprimante 

## Securitée



