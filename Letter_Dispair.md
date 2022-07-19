LETTER_DISPAIR

Un individu politique de haut niveau a été victime d'une attaque de spear-phishing. Le courriel provenait d'une entité gouvernementale légitime dans une nation où nous n'avons pas compétence. Cependant, nous avons retracé le courrier d'origine à un serveur web du gouvernement. Une énumération plus poussée a révélé un index de répertoire ouvert contenant un script de messagerie PHP qui, selon nous, a été utilisé pour envoyer l'e-mail. Nous avons besoin d'accéder au serveur pour lire les journaux et connaître l'auteur réel. Pouvez-vous aider ?


Nous avons un site web qui nous est proposé avec les fichiers suivants

<img width="756" alt="Capture d’écran 2022-07-19 à 07 42 15" src="https://user-images.githubusercontent.com/109574266/179676006-844c7011-9adb-45a9-95ef-50c1a4308d89.png">

Le fichier mailer.php se présente comme ceci

<img width="1502" alt="Capture d’écran 2022-07-19 à 07 42 56" src="https://user-images.githubusercontent.com/109574266/179676211-1bb425df-f3b4-487f-930c-11324b3f186e.png">

Après une recherche sur internet, nous découvrons une CVE sur le PHPMailer datant de 2016

https://www.exploit-db.com/exploits/40969
https://legalhackers.com/advisories/PHPMailer-Exploit-Remote-Code-Exec-CVE-2016-10045-Vuln-Patch-Bypass.html

<img width="1360" alt="Capture d’écran 2022-07-19 à 07 45 14" src="https://user-images.githubusercontent.com/109574266/179676367-3574601c-3d61-471f-916c-e57417404ca3.png">

Nous décidons d'essayer de l'exploiter.
Nous allons d’abord essayer quelque chose de simple, comme afficher le PHPinfo

<img width="1470" alt="Capture d’écran 2022-07-19 à 07 51 09" src="https://user-images.githubusercontent.com/109574266/179676658-18b9baba-fb02-4f97-8039-98203c0220a8.png">

Quand nous revenons à la racine, nous pouvons voir que le fichier a bien été upload sur le serveur.

<img width="1512" alt="Capture d’écran 2022-07-19 à 08 04 22" src="https://user-images.githubusercontent.com/109574266/179677039-dcf23dc2-5cb5-4a09-bc25-5083697f36e7.png">

Et qu'il nous affiche bien le PHPinfo

<img width="1498" alt="Capture d’écran 2022-07-19 à 07 51 52" src="https://user-images.githubusercontent.com/109574266/179677233-e6fc6907-0143-455f-8607-eed84be55c02.png">

Nous décidons alors d'uploader un fichier nommé reverse.php avec la commande : <?=`$_GET[1]`?>

<img width="1498" alt="Capture d’écran 2022-07-19 à 07 53 20" src="https://user-images.githubusercontent.com/109574266/179677396-988f0e17-0ba9-436f-a008-d9ad0ccc62d2.png">

Cela nous permet d'exécuter des commandes sur le serveur et d'aller voir le flag avec un : cat /flag.txt

<img width="1512" alt="Capture d’écran 2022-07-19 à 07 55 14" src="https://user-images.githubusercontent.com/109574266/179677521-d59840cd-3a10-46be-9436-5a4702137fb2.png">

FLAG : HTB{4_l3tt3r_0f_h0p3_c0nqu3r1ng_d1sp4ir!}
