# Exercice 13 - Conditions composées

## Enoncé - Mise en pratique

1.  Sélectionnez les titres et la note moyenne (**vote_average**) des films dont le **budget** est supérieur à 50 millions (50 000 000) et dont la note moyenne est supérieur à 7.
2.  Trouvez les films dont le **budget** est de plus de 100 millions (100 000 000) et sortis après 2010 ou ceux ayant un **popularity** supérieur à 100.
3.  Sélectionnez les films qui ne sont pas en `post-production` (**movie_status**) et qui ont un **budget** de plus de 250 millions (250 000 000).
4.  Trouvez les films dont le titre commence par `A` et qui ont soit un **vote_count** supérieur à 500 soit un **runtime** inférieur à 120 minutes.
5.  Sélectionnez les films qui ne sont ni `Candelled` ni `Post Production` et dont la note moyenne est soit inférieure à 5, soit supérieur à 8.

## Ma solution

### 13.1

```sql
USE movies;

/**
 * Rappel énoncé
 * ------------------------------------------------------------------------------------------------------
 * 1.  Sélectionnez les titres et la note moyenne (vote_average) des films dont
 *     le budget est supérieur à 50 millions (50 000 000) et dont la note moyenne est supérieur à 7.
 **/
  SELECT title, vote_average
  FROM movie
  WHERE
    budget > 50000000 AND vote_average > 7;
```

### 13.2

```sql
USE movies;

/**
 * Rappel énoncé
 * ------------------------------------------------------------------------------------------------------
 * 2.  Trouvez les films dont le budget est de plus de 100 millions (100 000 000) et sortis après 2010
 *     ou ceux ayant une popularity supérieur à 100.
 **/
SELECT title, budget, release_date, popularity
FROM movie
WHERE
  budget > 100000000 AND
  release_date >= "2011-01-01" OR
  popularity > 100;
```

### 13.3

```sql
USE movies;

/**
 * Rappel énoncé
 * ------------------------------------------------------------------------------------------------------
 * 3.  Sélectionnez les films qui ne sont pas en post-production et qui ont un budget
 *     de plus de 250 millions. (250 000 000)
 **/
SELECT title, movie_status, budget
FROM movie
WHERE
  movie_status != "post-production" AND
  budget > 250000000;
```

### 13.4

```sql
USE movies;

/**
 * Rappel énoncé
 * ------------------------------------------------------------------------------------------------------
 * 4.  Trouvez les films dont le titre commence par 'A' et qui ont soit un vote_count supérieur à 500
 *     soit un runtime inférieur à 120 minutes.
 **/
SELECT title, vote_count, runtime
FROM movie
WHERE
  title LIKE "A%" AND
  (vote_count > 500 OR runtime < 120);
```

### 13.5

```sql
USE movies;

/**
 * Rappel énoncé
 * ------------------------------------------------------------------------------------------------------
 * 5.  sélectionnez les films qui ne sont ni 'Cancelled' ni 'Post Production' et dont la note moyenne
 *     est soit inférieur à 5, soit supérieur à 8
 **/
SELECT title, movie_status, vote_average
FROM movie
WHERE
  NOT movie_status IN ("Cancelled", "Post Production") AND
  (vote_average < 5 OR vote_average > 8);
```
