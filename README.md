﻿# TCPmultithreading
**Objectif de l’exercice : Ecrire un serveur TCP permettant de traiter 10 (au max) clients en parallèle. Le traitement consiste à inverser une chaine de caractère, ajouter des sleep (avec thread.sleep) pour bloquer le client en attente et utiliser BufferReader et PrintWriter pour la gestion des streams. 
**Importation des classes: 
   + la classe BufferedReader pour la lecture des données d'entrée
   + la classe IOException pour la gestion des erreurs d'entrée/sortie
   + la classe InputStreamReader pour lire les caractères d'un flux d'entrée
  +la classe PrintWriter pour l'écriture de données formatées
  + la classe ServerSocket pour créer un serveur socket
  + la classe Socket pour créer un socket client/serveur
**Les étapes :
*Définition d'une constante pour le nombre maximal de clients
*Création d'un ServerSocket écoutant sur le port 9999
 *Attente et acceptation de la connexion : Le serveur est en attente qu'un client se connecte en utilisant la méthode accept() du ServerSocket. Lorsqu'une connexion est établie, le serveur accepte la connexion, créant un nouveau socket dédié à la communication avec le client.
 *Vérification si le nombre de threads actifs dépasse le nombre maximal de clients par la méthode Thread.activeCount() et si c’est le cas un message d’erreur est affiché et la connexion avec le client sera fermé par la méthode clientSocket.close()
*Création d'un thread pour gérer la connexion du client
         +Création d'une instance de ClientHandler avec le Socket client
   +Démarrage du thread ClientHandler pour gérer la connexion
 *gestion d’erreur : Capture des exceptions liées aux entrées/sorties et afficher Affichage de la trace de la pile d'exécution en cas d'erreur
* Bloc de code exécuté quelle que soit l'issue du bloc try :
   +Vérification si le ServerSocket a été initialisé
    + Bloc try pour gérer les exceptions liées à la fermeture du ServerSocket
        - Fermeture du ServerSocket
        - Capture des exceptions liées aux entrées/sorties et afficher Affichage de la trace de la pile d'exécution en cas d'erreur.
* Définition d'une classe interne ClientHandler étendant Thread pour gérer les connexions clients
* Méthode run() pour exécuter les opérations du thread
* Création des flux de communication : Crée des flux d'entrée et de sortie pour envoyer et recevoir des objets sur le socket.
* Lecture de la chaîne de caractères du client : Lecture de la première ligne envoyée par le client
* Simulation du traitement avec un délai :  par un pause de 1 seconde .
* Inversion de la chaîne de caractères
* Envoi de la chaîne inversée au client via PrintWriter.
* Fermeture des flux et de la connexion : Fermeture du BufferedReader et PrintWriter.
* Fermeture du Socket client.
* Capture des exceptions liées aux entrées/sorties ou à  l'interruption du thread
* Affichage de la trace de la pile d'exécution en cas d'erreur par la méthode printStackTrace().











