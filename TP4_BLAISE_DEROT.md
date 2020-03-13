# TP 4 - Utilisateurs, groupes et permissions

## Exercice 1. Gestion des utilisateurs et des groupes

1. Commencez par créer deux groupes groupe1 et groupe2

```
sudo addgroup groupe1  
sudo addgroup groupe2
```

2. Créez ensuite 4 utilisateurs u1,u2,u3,u4 avec la commande useradd, en demandant la création de leur dossier personnel et avec bash pour shell

```
sudo useradd -m u1
sudo useradd -m u2
sudo useradd -m u3
sudo useradd -m u4
```

3. Ajoutez les utilisateurs dans les groupes créés :  

-u1, u2, u4 dans groupe1  
-u2, u3, u4 dans groupe2

```
sudo usermod -a -G groupe1 u1
sudo usermod -a -G groupe1 u2
sudo usermod -a -G groupe1 u4

sudo usermod -a -G groupe1 u2
sudo usermod -a -G groupe1 u3
sudo usermod -a -G groupe1 u4
```

4. Donnez deux moyens d’aﬀicher les membres de groupe2



5. Faites degroupe1le groupe propriétaire de /home/u1 et /home/u2et de groupe 2 le groupe propriétairede /home/u3 et /home/u4

6. Remplacez le groupe primaire des utilisateurs :  

-groupe1pouru1etu2  
-groupe2pouru3etu4  

7. Créez deux répertoires/home/groupe1et/home/groupe2pour le contenu commun aux groupes, et mettez en place les permissions permettant aux membres de chaque groupe d’écrire dans le dossier associé.

8. Comment faire pour que, dans ces dossiers, seul le propriétaire d’un fichier ait le droit de renommer ou supprimer ce fichier?

9. Pouvez-vous vous connecter en tant queu1? Pourquoi?

10. Activez le compte de l’utilisateuru1et vérifiez que vous pouvez désormais vous connecter avec son compte.

11. Quels sont l’uid et le gid de u1?

12. Quel utilisateur a pour ui d1003?

13. Quel est l’id du groupe groupe1?


14. Quel groupe a pour guid 1002? (Rien n’empêche d’avoir un groupe dont le nom serait 1002...)

15. Retirez l’utilisateuru3du groupe groupe2. Que se passe-t-il? Expliquez.

16. Modifiez le compte de u4 de sorte que :
—il expire au1erjuin 2020  
—il faut changer de mot de passe avant 90 jours  
—il faut attendre 5 jours pour modifier un mot de passe  
—l’utilisateur est averti 14 jours avant l’expiration de son mot de passe  
—le compte sera bloqué 30 jours après expiration du mot de passe

17. Quel est l’interpréteur de commandes (Shell) de l’utilisateurroot?

18. à quoi correspond l’utilisateurnobody?

19. Par défaut, combien de temps la commande sudo conserve-t-elle votre mot de passe en mémoire? Quelle commande permet de forcer sudoà oublier votre mot de passe?


##Exercice 2. Gestion des permissions

1.Dans votre $HOME, créez un dossier test, et dans ce dossier un fichier fichier contenant quelqueslignes de texte. Quels sont les droits sur test et fichier?
 
2. Retirez tous les droits sur ce fichier (même pour vous), puis essayez de le modifier et de l’aﬀicher entant que root. Conclusion?  

3. Redonnez vous les droits en écriture et exécution sur fichier puis exécutez la commande echo "echoHello" > fichier. On a vu lors des TP précédents que cette commande remplace le contenu d’un fichier s’il existe déjà. Que peut-on dire au sujet des droits?

4. Essayez d’exécuter le fichier. Est-ce que cela fonctionne? Et avec sudo? Expliquez.

5. Placez-vous dans le répertoire test, et retirez-vous le droit en lecture pour ce répertoire. Listez lecontenu du répertoire, puis exécutez ou aﬀichez le contenu du fichier fichier. Qu’en déduisez-vous? Rétablissez le droit en lecture sur test

6. Créez dans test un fichier nouveau ainsi qu’un répertoire sstest. Retirez au fichier nouveauet au répertoire test le droit en écriture. Tentez de modifier le fichier nouveau. Rétablissez ensuite le droiten écriture au répertoire test. Tentez de modifier le fichier nouveau, puis de le supprimer. Que pouvez-vous déduire de toutes ces manipulations?

7. Positionnez vous dans votre répertoire personnel, puis retirez le droit en exécution du répertoire test.Tentez de créer, supprimer, ou modifier un fichier dans le répertoire test, de vous y déplacer, d’en lister le contenu, etc... Qu’en déduisez vous quant au sens du droit en exécution pour les répertoires?

8. Rétablissez le droit en exécution du répertoire test. Positionnez vous dans ce répertoire et retirez lui à nouveau le droit d’exécution. Essayez de créer, supprimer et modifier un fichier dans le répertoire test, de vous déplacer dans ssrep, de lister son contenu. Qu’en concluez-vous quant à l’influence des droits que l’on possède sur le répertoire courant? Peut-on retourner dans le répertoire parent avec ”cd..”? Pouvez-vous donner une explication?

9. Rétablissez le droit en exécution du répertoire test. Attribuez au fichier fichierles droits suﬀisants pour qu’une autre personne de votre groupe puisse y accéder en lecture, mais pas en écriture.

10. Définissez un umask très restrictif qui interdit à quiconque à part vous l’accès en lecture ou en écriture, ainsi que la traversée de vos répertoires. Testez sur un nouveau fichier et un nouveau répertoire

11. Définissez un umask très permissif qui autorise tout le monde à lire vos fichiers et traverser vos répertoires, mais n’autorise que vous à écrire. Testez sur un nouveau fichier et un nouveau répertoire.

12. Définissez un umask équilibré qui vous autorise un accès complet et autorise un accès en lecture aux membres de votre groupe. Testez sur un nouveau fichier et un nouveau répertoire.

13. Transcrivez les commandes suivantes de la notation classique à la notation octale ou vice-versa (vous pourrez vous aider de la commande stat pour valider vos réponses) :  
-chmod u=rx,g=wx,o=r fic  
-chmod uo+w,g-rx ficen sachant que les droits initiaux deficsontr--r-x---  
-chmod 653 ficen sachant que les droits initiaux deficsont711  
-chmod u+x,g=w,o-r ficen sachant que les droits initiaux deficsontr--r-x---

14. Aﬀichez les droits sur le programme passwd. Que remarquez-vous? En aﬀichant les droits du fichier /etc/passwd, pouvez-vous justifier les permissions sur le programme passwd?   

Pour les plus rapides :  

15. Access Control Lists (ACL): suivez le tutoriel de cette page :https://doc.ubuntu-fr.org/acl.

16. Quotas disques: suivez le tutoriel de cette page :https://doc.ubuntu-fr.org/quota.















