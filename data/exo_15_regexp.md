# Exercice 15 - Expressions régulières

## Enoncé - Mise en pratique

1.  Sélectionner les films dont le titre commence par `The`
2.  Trouver les films dont le titre se termine par `man`
3.  Sélectionner les films dont le titre contient `a` **suivi de n'importe quel caractère**, puis `e`
4.  Trouver les films dont le titre contient une lettre entre `a` **et** `e` comme premier caractère.
5.  Sélectionner les films dont le titre commence par `Coll` ou `Call`
6.  Trouver les films dont le titre contient `oo` deux fois.
7.  Sélectionner les films dont le titre ne commence pas par une voyelle.
8.  Trouver les films dont le titre commence par `The` ou `A`.

## Ma solution

### 15.1

```sql
USE movies;

/**
 * Rappel énoncé
 * ------------------------------------------------------------------------------------------------------
 * 1.  Sélectionner les films dont le titre commence par "The"
 **/
SELECT title
FROM movie
WHERE
  title REGEXP "^The";
```

### 15.2

```sql
USE movies;

/**
 * Rappel énoncé
 * ------------------------------------------------------------------------------------------------------
 * 2.  Trouver les films dont le titre se termine par "man"
 **/
SELECT title
FROM movie
WHERE
  title REGEXP "man$";
```

### 15.3

```sql
USE movies;

/**
 * Rappel énoncé
 * ------------------------------------------------------------------------------------------------------
 * 3.  Sélectionner les films dont le titre contient "a" suivi de n'importe quel caractère, puis "e"
 **/
SELECT title
FROM movie
WHERE
  title REGEXP "(a.e)";
```

### 15.4

```sql
USE movies;

/**
 * Rappel énoncé
 * ------------------------------------------------------------------------------------------------------
 * 4.  Trouver les films dont le titre contient une lettre entre "a" et "e" comme premier caractère.
 **/
SELECT title
FROM movie
WHERE
  title REGEXP "^[a-e]";
```

### 15.5

```sql
USE movies;

/**
 * Rappel énoncé
 * ------------------------------------------------------------------------------------------------------
 * 5.  Sélectionner les films dont le titre commence par "Coll" ou "Call"
 **/
SELECT title
FROM movie
WHERE
  title REGEXP "^(Coll|Call)";
```

### 15.6

```sql
USE movies;

/**
 * Rappel énoncé
 * ------------------------------------------------------------------------------------------------------
 * 6.  Trouver les films dont le titre contient "oo" deux fois.
 **/
SELECT title
FROM movie
WHERE
  title REGEXP "oo.*oo"
```

### 15.7

```sql
USE movies;

/**
 * Rappel énoncé
 * ------------------------------------------------------------------------------------------------------
 * 7.  Sélectionner les films dont le titre ne commence pas par une voyelle.
 **/
SELECT title
FROM movie
WHERE
  title REGEXP "^[^aeiouy]";
```

### 15.8

```sql
USE movies;

/**
 * Rappel énoncé
 * ------------------------------------------------------------------------------------------------------
 * 8.  Trouver les films dont le titre commence par "The" ou "A"
 **/
SELECT title
FROM movie
WHERE
  title REGEXP "^(The|A)";
```
