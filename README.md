PS UART TOOL - DESCRIPTION (FRANCAIS)
=====================================
(English version below / Version anglaise plus bas)

PRESENTATION
------------
PS UART Tool est un petit logiciel Windows qui lit les codes d'erreur
detailles des consoles PlayStation (PS3, PS4, PS5) via la liaison UART,
avec un adaptateur USB-TTL en 3,3 V.

Il sert de "lecteur de codes" : il envoie la commande errlog a la console,
affiche les reponses et traduit les codes quand ils figurent dans la liste
codes.txt. Il ne repare rien et ne remplace pas un diagnostic complet.


AUTEUR ET REPRISE DU PROJET
---------------------------
Ce logiciel a ete ecrit par Claude, un assistant IA cree par Anthropic,
a la demande de son utilisateur, a partir d'informations publiques
(forums de reparation, documentation communautaire).

Toute personne qui souhaite reprendre, modifier, ameliorer ou republier ce
projet peut le faire librement. Les contributions sont les bienvenues,
notamment : tests sur de vraies consoles, correction du format de lecture
PS4, ajout de l'authentification syscon PS3, enrichissement de codes.txt.
Aucune licence formelle n'est jointe : si tu republies le projet, pense a
en choisir une (par exemple MIT).


FONCTIONNALITES
---------------
- Detection automatique du port COM de l'adaptateur (CP210x, CH340, FTDI,
  PL2303).
- Choix de la console : PS4, PS5 ou PS3 (terminal brut).
- Calcul automatique du checksum des commandes (PS4 / PS5).
- Bouton "Lire les erreurs" : envoie errlog 0, errlog 1, etc. et s'arrete
  a la fin du journal (FFFFFFFF ou "No Error Codes").
- Resume des codes trouves, avec description si elle est dans codes.txt.
- Decodage de la structure des codes PS3 (etape, categorie, erreur).
- Bouton "Effacer errlog console" (avec confirmation).
- Champ de commande libre pour envoyer ses propres commandes.
- Export du rapport complet en fichier texte.
- Mode ecoute : une fois connecte, tout ce que la console emet s'affiche.


CONTENU DU DOSSIER
------------------
build.bat       Cree l'executable PS_UART_Tool.exe (Python requis).
uart_tool.py    Code source du logiciel.
codes.txt       Liste des codes connus (format CODE=description). Modifiable.
DESCRIPTION.txt Ce fichier.


INSTALLATION
------------
1. Extraire le zip sur le PC.
2. Installer Python (python.org) en cochant "Add Python to PATH".
   Pour Windows 7, utiliser Python 3.8.
3. Double-cliquer sur build.bat.
4. Recuperer PS_UART_Tool.exe et codes.txt dans le dossier dist.
   Garder codes.txt dans le meme dossier que l'exe.


UTILISATION
-----------
1. Brancher l'adaptateur USB-TTL en 3,3 V UNIQUEMENT (jamais 5 V).
2. Relier GND, et croiser TX/RX (TX adaptateur -> RX console et inversement).
3. Console branchee au secteur.
4. Choisir la console et le port, cliquer sur "Connecter".
5. Cliquer sur "Lire les erreurs", puis "Exporter le rapport" si besoin.

Si rien ne s'affiche : inverser TX et RX, verifier GND et l'alimentation.
Si du texte illisible s'affiche : la vitesse n'est pas la bonne.


LIMITES (A LIRE)
----------------
- Le logiciel n'a PAS ete teste sur une vraie console. Des ajustements
  peuvent etre necessaires.
- PS5 : format de lecture base sur des sources de forums et de documentation
  communautaire. Le plus susceptible de fonctionner.
- PS4 : aucun format ni liste de codes materiels confirmes. Les reponses
  s'affichent en brut, sans description.
- PS3 : terminal brut uniquement. L'authentification du syscon, necessaire
  pour lire errlog, n'est pas geree.
- Le calcul du checksum est base sur le format connu, non confronte au code
  d'autres outils.
- codes.txt est une liste partielle et indicative : un code designe une
  zone du circuit, pas forcement la piece defectueuse.
- Les points de test a souder dependent du modele et de la revision de
  carte ; le logiciel ne peut pas les identifier.


POUR ALLER PLUS LOIN
--------------------
Les outils communautaires (PS5CodeReader, guides ConsoleMods pour la PS3,
psdevwiki pour les listes de codes) sont plus complets. Les codes de
psdevwiki peuvent etre recopies dans codes.txt au format CODE=description.

AVERTISSEMENT : travailler sur une carte mere implique des risques pour la
console et pour soi-meme. Utilisation a ses propres risques.


################################################################
#                      ENGLISH VERSION                         #
################################################################

PS UART TOOL - DESCRIPTION (ENGLISH)
====================================

OVERVIEW
--------
PS UART Tool is a small Windows program that reads the detailed error
codes of PlayStation consoles (PS3, PS4, PS5) over the UART link, using a
3.3 V USB-TTL adapter.

It works as a "code reader": it sends the errlog command to the console,
displays the replies and translates the codes when they are listed in
codes.txt. It does not repair anything and does not replace a full
diagnosis.


AUTHOR AND PROJECT TAKEOVER
---------------------------
This software was written by Claude, an AI assistant made by Anthropic,
at the request of its user, using public information (repair forums and
community documentation).

Anyone who wants to take over, modify, improve or republish this project
is free to do so. Contributions are welcome, in particular: testing on
real consoles, fixing the PS4 read format, adding PS3 syscon
authentication, and expanding codes.txt. No formal license is included:
if you republish the project, consider choosing one (for example MIT).


FEATURES
--------
- Automatic detection of the adapter's COM port (CP210x, CH340, FTDI,
  PL2303).
- Console selection: PS4, PS5 or PS3 (raw terminal).
- Automatic checksum calculation for commands (PS4 / PS5).
- "Read errors" button: sends errlog 0, errlog 1, etc. and stops at the
  end of the log (FFFFFFFF or "No Error Codes").
- Summary of the codes found, with a description if it is in codes.txt.
- Decoding of the PS3 code structure (step, category, error).
- "Clear console errlog" button (with confirmation).
- Free command field to send your own commands.
- Export of the full report as a text file.
- Listen mode: once connected, everything the console sends is displayed.


FOLDER CONTENTS
---------------
build.bat       Builds the PS_UART_Tool.exe executable (Python required).
uart_tool.py    Source code of the program.
codes.txt       List of known codes (CODE=description format). Editable.
DESCRIPTION.txt This file.


INSTALLATION
------------
1. Extract the zip on your PC.
2. Install Python (python.org) and tick "Add Python to PATH".
   For Windows 7, use Python 3.8.
3. Double-click build.bat.
4. Get PS_UART_Tool.exe and codes.txt from the dist folder.
   Keep codes.txt in the same folder as the exe.


USAGE
-----
1. Connect the USB-TTL adapter at 3.3 V ONLY (never 5 V).
2. Connect GND, and cross TX/RX (adapter TX -> console RX and vice versa).
3. Console plugged into the wall outlet.
4. Choose the console and the port, then click "Connect".
5. Click "Read errors", then "Export report" if needed.

If nothing is displayed: swap TX and RX, check GND and power.
If garbled text is displayed: the baud rate is wrong.


LIMITATIONS (PLEASE READ)
-------------------------
- The software has NOT been tested on a real console. Adjustments may be
  needed.
- PS5: read format based on forum sources and community documentation.
  Most likely to work.
- PS4: no confirmed format or hardware code list. Replies are shown raw,
  without descriptions.
- PS3: raw terminal only. The syscon authentication, required to read
  errlog, is not handled.
- The checksum calculation is based on the known format and has not been
  compared with the code of other tools.
- codes.txt is a partial, indicative list: a code points to an area of
  the circuit, not necessarily to the faulty part.
- The test points to solder depend on the model and board revision; the
  software cannot identify them.


GOING FURTHER
-------------
Community tools (PS5CodeReader, ConsoleMods guides for the PS3, psdevwiki
for code lists) are more complete. Codes from psdevwiki can be copied into
codes.txt using the CODE=description format.

WARNING: working on a motherboard carries risks for the console and for
yourself. Use at your own risk.
