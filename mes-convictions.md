## Mes convictions professionnelles

Ce sont des convictions, pas des dogmes. Pour chacune : ce que j'y mets, et où je lâche du lest.
Il y a ici des méthodologies, des bonnes pratiques, pas mal de choses très bien décrites par d'autre, mais le but ici est juste d'y faire référence pour que tu comprennes comment je fonctionne.

### 🎯 Pas de solution parfaite, une solution pratique pour le besoin actuel
Une solution qui résout le problème d'aujourd'hui et qui est livrée vaut mieux qu'une solution idéale qui ne sort jamais.
- **En pratique** : je cherche le « suffisamment bon », je le livre, et j'itère sur des retours réels.
- **Limite** : pragmatique ne veut pas dire bâclé. La sécurité, les tests, la documentation et la lisibilité ne sont pas négociables pour aller plus vite.

### ✂️ On ne code pas pour des cas qui ne sont pas encore arrivés (YAGNI / KISS)
Le code écrit « au cas où » doit être maintenu, testé et compris, pour un besoin qui n'arrivera peut-être jamais.
- **En pratique** : je code pour le besoin connu, le plus simplement possible. Quand le nouveau cas arrive, on refactorise, et les tests sont là pour ça.
- **Limite** : je ne ferme pas volontairement des portes évidentes (un choix d'architecture difficile à défaire mérite d'anticiper un peu).

### 🗑️ Ne pas garder ce qui est inutile
On surestime ce qu'on possède déjà et ce qu'on y a investi. Du code mort, un test que plus personne ne comprend, du code commenté, un job CI que personne ne regarde, une doc périmée : ça coûte, même si « ça ne gêne pas ».
- **En pratique** : je supprime. Le code mort, les feature flags oubliés, les tests désactivés depuis des mois. Git s'en souvient pour nous.
- **Limite** : supprimer n'est pas deviner. Si je ne sais pas à quoi sert un élément, je cherche ou je demande avant.

### 🏕️ La règle du camp scout
Laisse le code un peu plus propre que tu ne l'as trouvé.
- **En pratique** : je renomme, j'extrais, j'ajoute le test manquant quand je passe dans un fichier.
- **Limite** : pas de refacto opportuniste qui gonfle une PR de correctif. Si c'est gros, ça mérite son propre ticket.

### ⬅️ Shift-left testing
Plus un défaut est détecté tôt, moins il coûte à corriger.
- **En pratique** : les cas de test sont pensés **dès l'écriture du ticket**, pas après le développement. Lint et analyse statique avant le commit, CI qui échoue vite.
- **Limite** : on ne trouve pas tout en amont. Ça ne dispense pas de surveiller ce qui se passe en production.

### 🔴🟢 Test first, avec pragmatisme
- **En pratique** : les tests sont définis avec le ticket, et je les code avant le code. Ils décrivent le comportement attendu avant qu'on se demande comment l'implémenter.
- **Limite** : pas sur l'exploratoire. Quand je ne sais pas encore ce que je cherche (spike, prototype, découverte d'une API), je code d'abord, et je teste ce qui est conservé.

### 💎 Le diamant plutôt que la pyramide des tests
La pyramide classique (beaucoup d'unitaires, un peu d'intégration, peu d'E2E) pousse souvent à tester des détails d'implémentation et à tout mocker.
Je préfère mettre le gros de l'effort sur les **tests d'intégration** : ils vérifient chaque brique dans son ensemble en mode "boite noire".
- **En pratique** : peu d'E2E, fiables et ciblés sur les parcours critiques ; une large base de tests d'intégration ; des tests unitaires là où il y a de la vraie logique métier.
- **Limite** : le bon ratio dépend du projet. Une librairie de calcul n'a pas la même forme de tests qu'une application web.

### 📚 La doc et les tests sont aussi importants que le code
Un code sans tests, on n'ose pas le modifier. Un code sans doc, personne d'autre ne peut le reprendre, ou ne le comprend pas en rentrant de vacances.
- **En pratique** : un ticket n'est pas terminé tant que les tests et la doc utile ne sont pas à jour. La doc vit au plus près du code, qui à la générée automatiquement.
- **Limite** : « utile » est le mot important. Je préfère trois paragraphes justes à trente pages que personne ne lit (voir « Ne pas garder ce qui est inutile »).

### 🤖 On automatise à la troisième fois
La première fois, on fait. La deuxième, on remarque. La troisième, on automatise.
- **Pourquoi pas avant** : à la deuxième fois, on ne sait pas encore ce qui est stable et ce qui varie. Automatiser trop tôt, c'est figer une mauvaise abstraction.
- **Limite** : si une tâche est risquée ou source d'erreurs, je l'automatise (ou au moins je la scripte) plus tôt.

### 🔍 Revues de code
Une revue de code n'est pas là pour que le code ressemble à ce que le relecteur aurait écrit. Elle sert à répondre à deux questions :
1. **Est-ce que ça répond au besoin, et seulement au besoin ?** Un cas oublié, une règle métier mal comprise, ou au contraire du code qui dépasse le périmètre du ticket.
2. **Est-ce que c'est sûr ?** Les limites et les dangers : cas aux bornes, erreurs non gérées, sécurité, performance, effets de bord, tests absents ou qui ne testent rien.

Ce que je ne fais pas, et que je n'attends pas de toi : « j'aurais fait autrement ». Si deux approches sont valables, c'est celle de l'auteur qui gagne.
Une alternative a sa place seulement si elle apporte quelque chose d'argumenté : plus simple, plus sûre, plus lisible.
