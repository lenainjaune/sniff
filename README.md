# sniff
sniff all relative tcpdump tshark wireshark

# tcpdump
Brouillon de commandes utiles
    # nota : le filtre de fin n'est là que pour éviter d'encombrer l'affichage, il ne supprime aucune donnée

    # voir le contenu direct du "payload" des packets (https://www.commandlinefu.com/commands/view/4371/see-entire-packet-payload-using-tcpdump.)
    tcpdump -nnvvXSs 1514 -i <device> <filters>

    # voir tout ce qui est relatif à l'hôte user-tosh et n'est pas du ssh
    tcpdump host user-tosh.local and not port ssh

    # voir tout ce qui est envoyé depuis user-tosh sur le port 49200 (ici minidlna) et enregistrer l'activité dans un fichier analysé par la suite
    tcpdump -w /root/tcpdump src user-tosh.local and port 49200

    # lire les "payload" de chaque paquet précédemment dumpés dans un fichier
    tcpdump -vvXSs 1514 -r /root/tcpdump

    # Afficher les trames et réseau par nombre => MACs, IPs et ports
    -e (voir [ici](https://stackoverflow.com/questions/53150610/tcpdump-only-display-in-or-out-mac-address-how-to-display-both))
    root@host:~# tcpdump -en host 192.168.1.5 and port 465
