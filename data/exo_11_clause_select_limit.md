# Exercice 11 - Les clauses SELECT et LIMIT

## Enoncé - Mise en pratique

Récupérez les colonnes **title** et **vote_average** de la table **movie** dans la base de données **movies** et limitez à 10 résultats.

## Ma solution

```sql
USE movies;

SELECT title, vote_average
FROM movie
LIMIT 10;
```
