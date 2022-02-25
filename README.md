# DemarcheDevOpsOpenClassroom

- Le cours Openclassroom (OC) se trouve à l'adresse
   https://openclassrooms.com/fr/courses/2035736-mettez-en-place-lintegration-et-la-livraison-continues-avec-la-demarche-devops/6182806-planifiez-votre-developpement

Il utilise Gitlab (https://gitlab.com/users/sign_in)

### Section A: planification du developpement

- Creez un nouveau projet dan Gitlab (https://gitlab.com/flmon/spring-petclinic-microservices)
- Aller sur Project Information, Labels
- Creer Labels To Do et Doing ainsi que d'autres t.q Epic,
   User story...
- Aller sur Issues, Boards; creer listes To Do, Doing et In review
- Creer nouveau board (Product) et y mettre les listes Low, Medium, High, Rejected 
   Ce board representera le Product Backlog
- Creer une epic (un ensemble de user stories) en faisant en fait une issue.
   dans List, nouvelle Issue en mettant Epic comme label
- Repeter avec une user story
- Lier la user story a l'epic (Linked issues, ajouter numero p.ex. #2)
- On peut deplacer (dragAndDrop) les issues dans les boards p.ex. deplacer la user story de Open vers To Do (list)
   ou deplacer l'epic dans Medium (l'epic est liee au Product Backlog alors que la user story reste dans Board Development)
   avec Low, Medium, High, on peut prioriser les epic ou avec To Do,... on peut visualiser l'avancement des user stories
- Creer un Milestone (qui symbolisera un sprint)
- Sur l'issue user story, on peut modifier des parametres pour lier la milestone (sprint), assigner qqn, 
    faire du time tracking (avec spend/estimate : /spend 2d   /estimate 1w)

### Section B: integration continue

- Clonez projet petclinic sur poste local (https://github.com/spring-petclinic/spring-petclinic-microservices.git)
  creer projet à partir de version control (https://gitlab.com/flmon/spring-petclinic-microservices.git)
  ajouter code petclinic (et push sur gitlab)
  la page du projet montre tous les nouveaux fichiers
- activer CI/CD sur gitlab (set up CI/CD sur page d'accueil projet); cela cree un fichier gitlab-ci.yml (avec contenu par défaut)
- On peut tester le pipeline (CI/CD, Pipelines, run pipeline)
- Mettre à jour le fichier gitlab-ci.yml avec donnees de OC => le pipeline fails !! (Permission denied for maven)
- Donner droit exec a mvnw (dans build et dans test)  (voir fichier gitlab-ci.yml dans gitlab) => le pipeline passe (OK)
- Pour tester le build avec une erreur, creer une branche git et introduire une erreur dans un .java
  push code to gitlab => on peut voir un pipeline qui echoue avec l'erreur de build
- Dans un cas reel, on va sur le pipeline en erreur pour voir le detail du probleme et ainsi creer une issue associee
 (label bug, milestone sprint 1) en explicitant le probleme
- L'issue apparait dans la colonne Open sur le board Development; on peut la deplacer vers Doing
- Creer une merge request (committer changements de (nouvelle) branche vers branche master)
 remplir champs (assignee, milestone, description avec Closes #4  pour indiquer l'issue 4 associee)
- Corriger le bug, commit et push sur nouvelle branche => un pipeline de build se lance
- On peut alors merger (si pipeline OK) => les changements sur nouvelle branche sont sur master et un
 pipeline se lance encore; Sur board Development, on voit que l'issue 'bug' est automatiquement 'Closed'