# Visualisation avec ggplot2

`ggplot2` utilise une "Grammar of Graphics" pour creer des graphiques en superposant des couches (layers) avec le signe `+`.

## 1. Structure de base

```r
ggplot(data = mon_df, mapping = aes(x = var_x, y = var_y, color = var_c)) +
  geom_XXX()
```

Les 3 elements essentiels :
1. **`ggplot(data = ...)`** : Le jeu de donnees
2. **`aes()`** : L'aesthetique (quelles variables sur quels axes, couleurs, etc.)
3. **`geom_XXX()`** : Le type de graphique

## 2. Les Principaux Geoms

### `geom_point()` - Nuage de points (Scatter plot)
Relation entre deux variables continues.
```r
ggplot(diamonds, aes(x = carat, y = price, color = cut)) +
  geom_point()
```

### `geom_bar()` - Diagramme a barres
Compter les frequences d'une variable categorielle.
```r
ggplot(diamonds, aes(x = cut)) +
  geom_bar()

# Avec remplissage par une autre variable
ggplot(diamonds, aes(x = cut, fill = clarity)) +
  geom_bar(position = "dodge")  # Barres cote a cote
```

### `geom_histogram()` - Histogramme
Distribution d'une variable numerique.
```r
ggplot(diamonds, aes(x = price)) +
  geom_histogram(binwidth = 500)
```

### `geom_boxplot()` - Boite a moustaches
Comparer les distributions entre groupes.
```r
ggplot(diamonds, aes(x = cut, y = price)) +
  geom_boxplot()
```

## 3. Personnalisation (Labels)

```r
ggplot(df, aes(x = var_x, y = var_y)) +
  geom_point() +
  labs(
    title = "Titre principal",
    subtitle = "Sous-titre",
    x = "Nom de l'axe X",
    y = "Nom de l'axe Y",
    color = "Titre de la legende couleur"
  )
```

## 4. Recap Rapide : Quel Geom Choisir ?

| Objectif | Geom | Variables |
|----------|------|-----------|
| Relation entre 2 variables continues | `geom_point()` | x = continue, y = continue |
| Distribution d'une variable numerique | `geom_histogram()` | x = continue |
| Frequences d'une variable categorielle | `geom_bar()` | x = categorielle |
| Comparer distributions entre groupes | `geom_boxplot()` | x = categorielle, y = continue |
| Tendance / evolution | `geom_line()` | x = continue/date, y = continue |
