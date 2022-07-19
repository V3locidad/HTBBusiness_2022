Breakout

Le CCSS a subi une attaque par ransomware qui a compromis le fichier médical numérique unique (EDUS) et le système national d'ordonnances pour les pharmacies publiques. Ils ont rapporté que leur infrastructure avait été compromise et qu'ils ne pouvaient pas y accéder. Cependant, l'APT a laissé son interface implantaire exposée, et vous devrez y pénétrer et découvrir comment cela fonctionne. REMARQUE : ce défi est destiné à être résolu avant "Breakin".

Nous avons accès au site web exposer

Nous remarquons directement un fichier à la racine nommé " bkd "
Nous décidons de le télécharger

<img width="1512" alt="Capture d’écran 2022-07-19 à 08 53 56" src="https://user-images.githubusercontent.com/109574266/179687312-d9286c59-8a20-472e-910d-35245681f78a.png">

Comme c'est un binaire, nous avons choisi de l'extraire avec binwalk

<img width="1328" alt="Capture d’écran 2022-07-19 à 08 58 49" src="https://user-images.githubusercontent.com/109574266/179688081-42ba8336-8fc4-49f1-a71e-3582e975c4cf.png">

Après l'extraction il nous donne un autre binaire nommé " 0 "
Nous effectuons un " strings 0 " sur celui-ci

<img width="1328" alt="Capture d’écran 2022-07-19 à 09 01 03" src="https://user-images.githubusercontent.com/109574266/179688375-0450580b-176d-4673-bf6f-eb47a146378a.png">

Nous recherchons " HTB " avec la commande " grep "HTB{" " sur le résultat du strings et nous avons directement le flag en clair

<img width="95" alt="Capture d’écran 2022-07-19 à 09 02 20" src="https://user-images.githubusercontent.com/109574266/179688650-ba05761a-cd1f-414c-89c2-3eb4ed6a37c3.png">

FLAG : HTB{th3_pr0c_f5_15_4_p53ud0_f1l35y5t3m_wh1ch_pr0v1d35_4n_1nt3rf4c3.....}
