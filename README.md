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

  => un protocole orienté connexion, qui vérifie la connexion entre l'hôte et le destinataire via la méthode de "Three Way Handshake" identifiable par les protocoles TCP SYNC, ACK et FIN. L'hôte source va créer une session de connexion avec l'hôte distant afin de le prévenir qu'il va recevoir des données.Une fois que la connexion est établie, l'échange de  données peut commencer. Pendant cet échange de données, les paquets (correspondants aux données) sont envoyés dans l'ordre, et le protocole TCP va s'assurer que tous les paquets sont bien transmis, et si ce n'est pas le cas, il est capable de renvoyer les paquets manquants. C'est l'un des avantages du protocole TCP.
Cette connexion sera maintenue jusqu'à ce qu'elle soit fermée, ce qui signifie qu'elle sera active à minima jusqu'à la fin de l'échange de données entre les deux hôtes. Elle peut être maintenue afin d'être prête dès que les deux hôtes auront besoin de communiquer ensemble.
  
  
  b- schéma connexion 

![shark 5](https://github.com/user-attachments/assets/7e2b72c9-9ad8-45f8-869d-ac313c4a8ec7)

  
iii - LAN 
  
  a- capture de paquets 
   ![shark 6](https://github.com/user-attachments/assets/320b210e-ee1d-434f-8d94-5eac9ea70be2)
   
   ![shark 7](https://github.com/user-attachments/assets/9aa7b38a-b89f-487c-8d99-ff2254d65685)
  
  b- analyse des fichiers
  - mDNS : Multicast DNS

    -> un service conçu pour aider à la résolution de noms dans les petits réseaux. A la différence du protocole DNS qui sollicite un serveur de nom
    le protocole mDNS adresse directement tout les participants du réseau. Le client correspondant envoie un multicast dans le réseau et demande à quel participant du réseau le nom d’hôte correspond. Le multicast est une forme de communication spécifique dans laquelle un seul message est adressé à un groupe de destinataires. Le groupe peut par exemple être constitué de l’ensemble du réseau ou d’un sous-réseau.

    De cette façon, la requête est également envoyée au membre du groupe qui possède le nom d’hôte recherché. Il répond alors à l’ensemble du réseau également via le Multicast. De cette façon, tous les participants sont informés de la connexion entre le nom et l’adresse IP et peuvent effectuer une entrée correspondante dans leur cache mDNS. Ainsi, tant que cette entrée est valable, personne dans le réseau n’a besoin de demander ce nom d’hôte.

    Le Multicast DNS génère un trafic relativement important, mais il permet d’économiser activement les ressources du réseau
  - FTP : File Transfer Protocol

    -> un protocole de transfert de fichiers qui permet d'envoyer et recevoir des fichiers et qui fonctionne sur le mode client/serveur. Un client FTP va établir une connexion TCP avec un serveur FTP dans le but d'échanger des données.
    Cette connexion s'appuie sur deux canaux différents :

    - Un canal de contrôle qui sert à l'authentification, à l'envoi des commandes FTP ou encore à la navigation dans l'arborescence du serveur FTP
    - Un canal de données qui sert tout simplement au transfert des données, que ce soit pour envoyer ou recevoir
   
    Le protocol FTP en lui-même n'est pas sécurisé ou crypté donc pour protéger ses données d'authentification et les fichiers échanger
    il faut rajouter un protocole de sécurité par dessus tel que le SSL/TLS ou SSH par example qui permttra de crypté les données du serveur de fichier et dans ce cas on parle de protocole FTPS ou SFTP


  - SMB : Serveur Message Block
    
    -> un protocole client-serveur qui permet d'accéder à des ressources via le réseau, et particulièrement l'accès à des fichiers et des dossiers. Il existe plusieurs version du protocole SMB, la plus récente étant SMB v3.1. Si deux machines exploitent une version différente la plus ancienne sera utilisé pour communiquer. SMB v1 n'est plus pris en charge et est obsolète et déprécié depuis 2014 et il est déconseiller de l'utiliser à cause d'une faille trouver en 2017, EternalBlue - CVE-2017-0144 qui a nottement été exploité par des ransomwares ravageurs comme WannaCry. 
    

  - HTTPS : Hypertext Transfer Protocol Secure

    ->  la version sécurisée du protocole HTTP, principal protocole utilisé pour l’envoi de données entre un navigateur Web et un site Web. HTTPS est chiffré afin de renforcer la sécurité du transfert de données. HTTPS est le protocole HTTP avec une surcouche TLS pour la protection des données.
  - TLSv1.2 : Transport Layer Security

    -> un protocole de sécurité largement adopté et conçu pour faciliter la confidentialité et la sécurité des données sur les communications Internet. Il est principalement utilisé pour chiffrer la communication entre les applications web et les serveurs, comme les navigateurs web chargeant un site web, par exemple. Le TLS également être utilisé pour chiffrer d'autres communications, comme les e-mails, les services de messagerie et la voix sur IP (VoIP).
  
  
iv - tshark 

  a- script
  
  tshark -D #pour lister les interfaces
  
  tshark -i "interface" -c "nb de paquet à capturer" -f "filtre"

  ![tshark 2](https://github.com/user-attachments/assets/69b0d831-0d98-4677-aa48-594b2157f5d8)

  
  b- test

  ![tshark 1](https://github.com/user-attachments/assets/b670c581-6455-4fdb-ab9f-280eeda82c0c)

