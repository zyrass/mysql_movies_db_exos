# Exercice 16 - Trier les résultats

## Enoncé - Mise en pratique

1.  Trier les films par date de sortie la plus récente. Pour les films sortis le même jour, les trier par note moyenne décroissante.
2.  Calculer le revenu net (revenue - budget) pour chaque film et trier les résultats par revenue net décroissant. Inclure uniquement les films avec un revenu net positif.
3.  Calculer le RIO et cibler exclusivement que les films qui ont eu un bénéfice de x2 et maximum de x5.
    Organiser le tout par titre ascendant.

## Ma solution

### 16.1

```sql
USE movies;

/**
 * Rappel énoncé
 * ------------------------------------------------------------------------------------------------------
 * 1.  Trier les films par date de sortie la plus récente.
 *     Pour les films sortis le même jour, les trier par note moyenne décroissante.
 **/
SELECT title, vote_average, release_date
FROM movie
WHERE
  title REGEXP "^[a-z]" -- Pour éviter d'avoir les films avec des caractères chinoix/japonais etc.
ORDER BY
  release_date DESC, vote_average DESC
```

### 16.2

```sql
USE movies;

/**
 * Rappel énoncé
 * ------------------------------------------------------------------------------------------------------
 * 2.  Calculer le revenu net (revenue - budget) pour chaque film
 *     et trier les résultats par revenue net décroissant.
 *     Inclure uniquement les films avec un revenu net positif.
 **/
    SELECT title, revenue, budget, (revenue - budget) as profit, (revenue / budget) as ROI_Retour_Sur_Investissement
    FROM movie
    WHERE
    title REGEXP "^[a-z]" AND
    (revenue - budget) > 0
    ORDER BY
    (revenue - budget) DESC
```

### 16.3 - BONUS

```sql
USE movies;

/**
 * Rappel énoncé
 * ------------------------------------------------------------------------------------------------------
 * 3.  Calculer le RIO et cibler exclusivement que les films qui ont eu un bénéfice de x2 et maximum de x5.
 *     Organiser le tout par titre ascendant.
 **/
SELECT title, revenue, budget, (revenue - budget) as profit, (revenue / budget) as ROI
FROM movie
WHERE
  title REGEXP "^[a-z]" AND
  ((revenue / budget) BETWEEN 2 AND 5)
ORDER BY title;
```
