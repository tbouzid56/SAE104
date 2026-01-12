//
// TP4  Le SGBD Rel et le langage relationnel Tutorial D
//

L'objectif de ce TP est de construire une base de données relationnelle, d'initialiser cette base, puis d'en extraire des informations. 
Vous mettrez en œuvre le langage relationnel Tutorial D dans le contexte du SGBD Rel présenté en cours magistral et en TD.


// Question 1 : Définition et initialisation de la relation <<clients>>


//a) Schéma de la relation <<clients>>

// Définir la variable relationnelle de nom <<clients>> dont la liste des attributs est numcli, nom et adrcli; La clé de cette relation est numcli.
var clients real relation {numcli INTEGER, nomcli CHAR,  adrcli CHAR} key{numcli};
//b) Initialiser la relation <<clients>> avec les tuples suivants :
 
clients := relation	{ tuple{numcli 1, nomcli "Arniel",  adrcli "Servel - Lannion"},
	  tuple{numcli 2, nomcli "Legudec", adrcli "Brel. - Lannion"},
	  tuple{numcli 3, nomcli "Bolin",  adrcli "Ker Huel - Lannion"},
	  tuple{numcli 4, nomcli "Durand",  adrcli "Bd dArmor - Lannion"},
	  tuple{numcli 5, nomcli "Mazer",  adrcli "La Clarte - Perros"},
	  tuple{numcli 6, nomcli "Murton",  adrcli "Ker Huel - Lannion"},
	  tuple{numcli 7, nomcli "Legros",  adrcli "La Clarte - Perros"},
	  tuple{numcli 8, nomcli "Duchemin",  adrcli "Brel. - Lannion"},
	  tuple{numcli 9, nomcli "Guidroc",  adrcli "Ker Huel - Lannion"},
	  tuple{numcli 10, nomcli "Podrez",  adrcli "Bd dArmor - Lannion"}};


// Question 2 : 

//Suivre les étapes identiques à celles de la question 2 pour définir :

//- la variable relationnelle de nom <<stock>> dont la liste des attributs est numart, nomart, typart, prixart et qtstock; La clé de cette relation est numart.
var stock real relation {numart INTEGER, nomart CHAR, typart CHAR, prixart INTEGER, qtstock INTEGER } key{numart};

//- la variable relationnelle de nom <<commande>> dont la liste des attributs est datcom, numart, numcli et qtart; La clé de cette relation est (datcom, numart, numcli). 
var commande real relation {datcom INTEGER, numart INTEGER, numcli INTEGER, qtart INTEGER} key{numart, numcli, datcom};
// puis initialiser les 2 variables relationnelles respectivement avec les tuples :

// la variable <<stock>> avec les tuples suivants :

stock := relation{ tuple{numart 1, nomart "Mathematiques : Algebre", typart "Sciences", prixart 40, qtstock 20},
	  tuple{numart 2, nomart "Mathematiques : Analyse", typart "Sciences", prixart 12, qtstock 20},
	  tuple{numart 3, nomart "Perception et Realite", typart "Philosophie", prixart 23, qtstock 400},
	  tuple{numart 4, nomart "Le moi", typart "Philosophie", prixart 2, qtstock 900},
	  tuple{numart 5, nomart "Vie de Zograffi", typart "Litterature", prixart 20, qtstock 400},
	  tuple{numart 6, nomart "Terre des Hommes", typart "Litterature", prixart 19, qtstock 40},
	  tuple{numart 7, nomart "Voyages Imaginaires", typart "Litterature", prixart 1, qtstock 300},
	  tuple{numart 8, nomart "1984", typart "Litterature", prixart 8, qtstock 80},
	  tuple{numart 9, nomart "Germinal", typart "Litterature", prixart 40, qtstock 20},
	  tuple{numart 10, nomart "La Programmation", typart "Sciences", prixart 40, qtstock 25}};

// la variable <<commande>> avec les tuples suivants :

commande:= relation{ tuple{datcom 20121130, numart 1, numcli 5, qtart 10},
	  tuple{datcom 20120622, numart 3, numcli 6, qtart 10},
	  tuple{datcom 20120604, numart 4, numcli 6, qtart 20},
	  tuple{datcom 20120608, numart 5, numcli 6, qtart 20},
	  tuple{datcom 20130101, numart 2, numcli 5, qtart 40},
	  tuple{datcom 20130103, numart 4, numcli 2, qtart 1},
	  tuple{datcom 20130109, numart 4, numcli 4, qtart 2},
	  tuple{datcom 20130115, numart 3, numcli 1, qtart 10},
	  tuple{datcom 20130127, numart 1, numcli 3, qtart 10},
	  tuple{datcom 20130303, numart 8, numcli 1, qtart 30},
	  tuple{datcom 20130304, numart 8, numcli 1, qtart 5},
	  tuple{datcom 20130308, numart 5, numcli 2, qtart 10},
	  tuple{datcom 20130317, numart 1, numcli 4, qtart 10},
	  tuple{datcom 20130318, numart 3, numcli 7, qtart 20},
	  tuple{datcom 20130322, numart 4, numcli 7, qtart 10},
	  tuple{datcom 20130322, numart 3, numcli 8, qtart 20},
	  tuple{datcom 20130402, numart 2, numcli 7, qtart 55},
	  tuple{datcom 20130403, numart 2, numcli 5, qtart 90},
	  tuple{datcom 20130412, numart 3, numcli 1, qtart 2},
	  tuple{datcom 20130419, numart 7, numcli 2, qtart 8},
	  tuple{datcom 20130419, numart 4, numcli 2, qtart 3}};


// Question 4 : contraintes de clés étrangères

// Ajouter les lignes nécessaires pour permettre de définir les contraintes d'intégrité référentielle exprimant que les attributs numart et numcli de la relation <<commande>> sont des clés étrangères référençant respectivement les relations <<stock>> et <<clients>> 


// Question 5 : interrogation de la base de données


On souhaite obtenir :

1. tous les articles
stock

2. tous les clients
clients

3. toutes les commandes
commande

4. le nom de chaque article
stock{nomart}

5. le nom et l'adresse de chaque client
clients{nomcli,adrcli}

6. le nom et le numro des clients dont l'adresse est "La Clarte - Perros"
(clients where adrcli="La Clarte - Perros"){nomcli,numcli}

7. les articles de type "Philosophie"
stock where typart="Philosophie"

8. le nom, le type des articles de type "Philosophie" ou "Litterature"
(stock WHERE typart = "Philosophie" OR typart="Litterature"){nomart, typart}

9. le nom, le type des articles dont la quantité en stock est > 100
(stock where qtstock > 100){nomart, typart}

10. les articles de type Sciences dont la quantité en stock est < 100
(stock where qtstock < 100 AND typart="Sciences")

11. le nom des articles de type Sciences dont la quantité en stock est < 100
(stock where qtstock < 100 AND typart="Sciences"){nomart}

12. les noms des articles dont la valeur du stock est > 1000
(stock where qtstock > 1000){nomart}

13. le nom et le prix des articles dont le prix est > 20
(stock where prixart > 20){nomart, prixart}

14. le nom, type des articles dont le prix est < 40
(stock where prixart < 40){nomart, typart}

15. les noms des articles commandés
(commande JOIN stock){nomart}

16. les noms des clients ayant commandé
(clients JOIN stock){nomcli}

17. le numéro des clients n'ayant jamais commandé
clients{numcli} minus commande{numcli}

18. les numéros des clients et des articles commandés par ce client.
commande{numcli, numart}

19. les commandes concernant les articles qui ne sont pas de type "Philosophie"
(commande join stock) where typart <> "Philosophie"

20. le nom des articles de type Sciences dont au moins une commande a un montant > 800
((commande join stock) where qtstock > 800 and typart = "Sciences"){nomart}

(extend (stock join commande):
	{prixQte := prixart * qtart}
where prixQte > 800 and typart="Sciences"){nomart}

(stock join commande)

21. la valeur du stock
on entend la valeur financière du stock = on fait la somme, sur tous les tuples de stock, de (nombre d'articles * prix de l'article) 

//solution 0
sum(stock, prixart*qtstock)
 
//soluce 1
summarize stock : {total := sum(prixart*qtstock)}

//soluce 2
sum(extend stock : {total := prixart*qtstock, total})

//soluce 3
summarize
	(extend 
		stock 
			: {ValProduit := prixart*qtstock}
	)
	: {ValStock := sum(ValProduit)}

22. la somme des montants des commandes
sum(stock join commande, qtart$prixart)

summarize
(
	extend
	commande join stock
	:{ValCom := prixart...

23. les noms des clients ayant commandé (au moins un) article de type "Philosophie"
type "Philosophie"
((stock join commande join clients) where typart = "Philosophie")
{nomcli}

24. les numéros des articles commandés par au moins deux clients différents (sans SUMMARIZE)


25. les couples de numéros de clients (n1,n2) tels que les clients n1 et n2 soient différents et aient la même adresse.


26. le nombre de clients


27. la quantité minimale en stock


28. la quantité maximale en stock des articles de type "Philosophie"


29. la moyenne des quantités en stock
avg(stock, qtstock)

30. le nombre de commandes du client n°1
count(comande where numcli = 1)

31. le nom des articles commandés par les clients n°4 ou n°2


32. le nom des articles qui ne sont pas commandés par le client n°4 ou par le client n°2


33. le nom des articles tels qu'il existe au moins une commande de quantité supérieure à celle en stock


34. le numéro des articles qui ne sont commandés qu'une seule fois


35. la moyenne des quantités commandées des articles de type "Litterature"


36. le numéro des articles qui ne sont commandés que par un seul client


37. le nombre de commandes passées au premier semestre 2013


38. les numéros des articles commandés au premier trimestre 2013 


39. Parmi les articles du stocks, quels sont les numéros de ceux commandés au premier trimestre 2013


40. le nombre d'articles du stock qui n'ont pas été commandés au deuxième trimestre 2013 (les articles de mêmes numéros ne sont comptés qu'une seule fois)


41. le nombre total d'articles en stock par type d'article


42. le nombre total d'articles commandés par client (tout type confondu)





