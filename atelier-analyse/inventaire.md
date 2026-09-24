# Inventaire des points d'entrée

Le livrable de l'atelier d'analyse. Il dit ce que l'API devra **permettre** — pas comment on
l'écrira.

Une règle : tout ce qui figure ici doit se justifier par la lettre de mission ou par un écran
des maquettes. Si vous ne savez plus d'où vient une ligne, c'est peut-être qu'elle n'en vient
pas. (Seule exception : la section bonus, si vous en ajoutez une.)

---

## Ce que l'utilisateur peut faire
Une action par ligne, en français. Pas encore de chemins.

Sans être connecté:
x Rechercher des billets - ville de départ et arrivée, nb de passagers, date
x Consulter les détails d'un billet
x Se connecter
x S'inscrire 

En étant connecté:
x Rechercher des billets - ville de départ et arrivée, nb de passagers, date
x Mettre un ou plusieurs billets dans son panier
x Consulter son panier
x Consulter ses billets passés
x Régler son panier afin d'avoir les billets
x Acceder à son compte

-

## Les points d'entrée

| Ce que ça fait | Chemin proposé | Qui peut l'appeler |
________________________________________________________

| Rechercher un  | POST tickets/  | tout le monde      |
|  billet        | + filters      |                    |
|                |GET date, ville |                    |
--------------------------------------------------------
| Accéder à son  | GET users/{id} | user connecté à qui|
| compte         |                | appartient le      |
|                |                | compte             |
--------------------------------------------------------
| Consulter ses  | GET users/{id} | user connecté à qui|
| billets        | /tickets       | appartient le      |
|                |                | compte             |
--------------------------------------------------------
| Mettre un/des  | POST users/{id}| user connecté à qui|
|  billets dans  | /cart          | appartient le      |
| son panier     |                |  compte            |
--------------------------------------------------------
| Régler son/ses | POST user/{id} | user connecté à qui|
| billets        | /cart/pay      | appartient le      |
|                |                | compte             |
--------------------------------------------------------
| Consulter son  | GET users/{id} | user connecté à qui|
| panier         | /cart          | appartient le      |
|                |                | compte             |
--------------------------------------------------------
| Consulter le   | GET users/{id} | tout le monde      |
| détail d'un    | /ticket/{id}   |                    |
| billet         |                |                    |
--------------------------------------------------------
| Se connecter   | POST? GET users| tout le monde      |
--------------------------------------------------------
| S'inscrire     | POST users/{id}| user connecté à qui|
|                |                | appartient le      |
|                |                | compte             |
--------------------------------------------------------


## Les données qui circulent

Pour chaque point d'entrée : ce qu'il reçoit, ce qu'il renvoie. Nommez les données comme
l'Office les nomme — les traduire en identifiants techniques, c'est le travail de demain.

Se connecter -> reçoit 
S'inscrire -> reçoit infos user,
Rechercher un billet -> reçoit filtres de recherche, (optionel: id user si historique), renvoie liste de billets et leurs infos (villes et dates disponibles)
Consulter ses billets -> reçoit id user, renvoie les billets et leurs infos
Mettre un/des billets dans son panier -> reçoit id user, id billets, renvoie X
Consulter son panier -> reçoit id user, renvoie cart associé au user
Régler son/ses billets -> reçoit id user, id billet, renvoie billet matérialisé?
Accéder à son compte -> reçoit id user, renvoie infos user
Consulter le détail d'un billet -> reçoit id billet, renvoie infos du billet


## Ce dont on n'est pas sûrs

Les questions que la lettre et les maquettes ne tranchent pas. Une question notée vaut mieux
qu'une réponse inventée.

-
