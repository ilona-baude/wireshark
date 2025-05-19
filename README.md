# wireshark

Modèle OSI

<img width="469" alt="modele-OSI" src="https://github.com/user-attachments/assets/32db09bc-4aa9-410e-9f90-a3955442526f" />

Wireshark 


i- Utilisation 

  a- Logiciel
  
   Wireshark est un logiciel libre et gratuit qui permet la capture de paquet et l'analyse de traffic réseau. Wireshark peut être utilisé pour capture le traffic réeau en live ou pour analyser des fichiers de capture réseaux au format .pcap ou .pcapng. 
   Le format .pcapng est le nouveau format de fichier capture réseau qui est utilisé par défaut par wireshark depuis la mise à jour 1.8. Le format .pcap est moins détaillé mais est toujours compatible avec wireshark ainsi qu'avec d'autres logiciel de d'analyse de capture réseau.
   Wireshark peut également capturer le trafic provenant de divers types de médias, tels que Ethernet, LAN, USB, et Bluetooth. De plus, l’outil est également capable de lire les données en direct de toutes sortes de réseaux: Ethernet, IEEE, 802.11, Protocole point à point (PPP) et bouclage inclus.
   Wireshark prend en charge de nombreu protocol mais il est toujours possible d'ajouter un plug-in au logiciel pour analyser un protocol qui ne serait pas pris en charge par le logiciel de base. 
  
  b- pour qui et pour quoi ? 
  
Principalement, Wireshark est utilisé par les administrateurs pour résoudre les problèmes de performances du réseau. Si on remarque une anomalie sur le réseau tel qu'une augmentation de la latence, des paquets perdus, des problèmes de retransmission ou une menace malveillante, grâce à Wireshark ont peut enquêter. Il est important de noter que Wireshark en lui-même ne détecte pas les menaces ou irrégularité dans le réseau et ne fournira aucune alerte. Il revient donc au administrateur de détecter les menaces ou d'utiliser d'autres logiciel pour analyser les fichiers de captures réseau et détecter de potentiel menaces. 
  
ii - Capture Réseau 

![shark 2](https://github.com/user-attachments/assets/f62ef59a-40c3-4b5a-9ba0-057f8c307fe9)


  a- Protocoles ARP, UDP, TCP
  
  ARP : Address Resolution Protocol
  
  => un protocole qui se situe sur la couche 3 du modèle OSI. On l'assimile parfois à un protocole de couche 2 et demi, car il assure la liaison entre le protocole IP qui utilise les adresses IP pour construire ses paquets et les trames Ethernet qui elles utilisent les adresses MAC.
 
  ![shark 3](https://github.com/user-attachments/assets/81b78ecd-b7da-4389-976e-30e0ce8cd45e)

  UDP : User Datagram Protocol

  => un protocole de communication sans connexion, le protocole UDP envoie les données sans ce soucier de si oui ou non le destinataire a bien reçue l'ensemble des données. 
  De ce fait le protocol UDP est bien plus rapide que le protocol TCP. L'en-tête d'un segment UDP contient très peu de champs : le port source, le port de destination, la longueur totale du segment, la somme de contrôle (pour vérifier l'intégrité du segment envoyé par le réseau) et les données.

  ![shark 4](https://github.com/user-attachments/assets/1fae14ad-6183-46b8-9c9c-2e31072bebeb)

Le protocole UDP est souvent utilisé pour regarder des flux de vidéo en streaming, ce flux est transporté via le protocole UDP, car cela permet d'alléger la charge côté serveur et que c'est adapté à cet usage. Pour lire un flux diffusé par un serveur, le protocole UDP est idéal. Généralement, les protocoles qui utilisent UDP le font, car si un paquet est perdu ce n'est pas critique pour le reste de la transmission. Par exemple, s'il y a une perte d'une image lors de la lecture d'un flux en streaming, cela n'est pas grave et passera inaperçu.
Le protocole UDP peut aussi être utilisé pour :

- Le protocole DNS pour la résolution des noms (même si TCP peut être utilisé dans de rares cas)
- Le protocole SNMP pour la supervision des équipements
- Le protocole NTP pour la mise à jour de la date et l'heure via le réseau
- Le protocole TFTP pour le transfert de fichiers simplifié


TCP : Transmission Control Protocol

  =>
  
  
  b- schéma connexion 

  
iii - LAN 
  
  a- capture de paquets 
  
  b- analyse des fichiers
  
  
iv - tshark 

  a- script
  
  b- test
