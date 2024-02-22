# Exercice 12 - Clause WHERE et les opérateurs de comparaison communs

## Enoncé - Mise en pratique

1.  Sélectionnez tous les films ayant un **vote_average** supérieur à 8.
2.  Trouvez les films avec une **popularity** supérieur à 140 et un **vote_count** supérieur à 3000.
3.  Sélectionnez les films dont le temps de lecture est compris entre 90 et 120 minutes (**runtime**)
4.  Affichez les films dont le **movie_status** est soit `Rumored` soit `Post Production`
5.  Trouvez les films dont **overview** contient `god`
6.  Sélectionnez les films qui n'ont pas de **homepage**
7.  Affichez les films qui ne sont pas en statut `Released`
8.  Trouvez les films qui sont sortis après le **15 mars 2016**
9.  Trouvez les films qui ont soit un **budget** supérieur à 100 millions (100 000 000), soit un **revenue** supérieur à 300 millions (300 000 000)

## Ma solution

### 12.1

```sql
USE movies;

/**
 * Rappel énoncé
 * ------------------------------------------------------------------------------------------------------
 * 1.  Sélectionnez tous les films ayant un vote_average supérieur à 8.
 **/
SELECT title, note_average
FROM movie
WHERE
  vote_average > 8;
```

### 12.2

```sql
USE movies;

/**
 * Rappel énoncé
 * ------------------------------------------------------------------------------------------------------
 * 2.  Trouvez les films avec une popularity supérieur à 140 et un vote_count supérieur à 3000.
 **/
SELECT title, popularity, vote_count
FROM movie
WHERE
  popularity > 140 AND vote_count > 3000;
```

### 12.3

```sql
USE movies;

/**
 * Rappel énoncé
 * ------------------------------------------------------------------------------------------------------
 * 3.  Sélectionnez les films dont le temps de lecture est compris entre 90 et 120 minutes (runtime)
 **/
SELECT title, runtime
FROM movie
WHERE
  runtime BETWEEN 90 AND 120;
```

### 12.4

```sql
USE movies;

/**
 * Rappel énoncé
 * ------------------------------------------------------------------------------------------------------
 * 4.  Affichez les films dont le movie_status est soit `Rumored` soit `Post Production`
 **/
SELECT title, movie_status
FROM movie
WHERE
  movie_status IN ('Rumored', 'Post Production');
```

### 12.5

```sql
USE movies;

/**
 * Rappel énoncé
 * ------------------------------------------------------------------------------------------------------
 * 5.  Trouvez les films dont overview contient `god`
 **/
SELECT title, overview
FROM movie
WHERE
  overview LIKE "%god%";
```

### 12.6

```sql
USE movies;

/**
 * Rappel énoncé
 * ------------------------------------------------------------------------------------------------------
 * 6.  Sélectionnez les films qui n'ont pas de homepage
 **/
SELECT title, homepage
FROM movie
WHERE
  homepage = "";
  -- homepage LIKE "%"
```

### 12.7

```sql
USE movies;

/**
 * Rappel énoncé
 * ------------------------------------------------------------------------------------------------------
 * 7.  Affichez les films qui ne sont pas en statut Released
 **/
SELECT title, movie_status
FROM movie
WHERE
  movie_status != "Released";
  -- NOT movie_status "Released"
```

### 12.8

```sql
USE movies;

/**
 * Rappel énoncé
 * ------------------------------------------------------------------------------------------------------
 * 8.  Trouvez les films qui sont sortis après le 15 mars 2016
 **/
SELECT title, release_date
FROM movie
WHERE
  release_date > "2016-03-15";
```

### 12.9

```sql
USE movies;

/**
 * Rappel énoncé
 * ------------------------------------------------------------------------------------------------------
 * 9.  Trouvez les films qui ont soit un budget supérieur à 100 millions (100 000 000),
 *     soit un revenue supérieur à 300 millions (300 000 000)
 **/
SELECT title, budget, revenue
FROM movie
WHERE
  budget > 100000000 OR revenue > 300000000;
```
