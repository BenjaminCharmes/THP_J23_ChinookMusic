<h1 align="center">Day 23 of The Hacking Project: Ruby On Rails - SQL to ActiveRecord</h1>

Here is exercise 2 in Ruby on Rails from day 23 of The Hacking Project: For this exercise, we have a DB on which we will work... 

<h2 align="center">🎉 Day 8 of the Full Stack training 🎉</h2>

### a) Niveau facile

- Quel est le nombre total d'objets Album contenus dans la base (sans regarder les id bien sûr) ?

Réponse: `=> 347`
```
Album.count
```
ou
```
Album.all.length
```

- Qui est l'auteur de la chanson "White Room" ?

Réponse: `=> Eric Clapton`
```
Track.find_by(title: "White Room").artist
```

- Quelle chanson dure exactement 188133 milliseconds ?

Réponse: `=> Perfect`
```
Track.find_by(duration: 188133).title
```

- Quel groupe a sorti l'album "Use Your Illusion II" ?

Réponse: `=> Gun N Roses`
```
Album.find_by(title: "Use Your Illusion II").artist
```


### b) Niveau Moyen

- Combien y a t'il d'albums dont le titre contient "Great" ?

Réponse: `=> 13`
```
Album.where("title Like ?", "%Great%").count
```
ou
```
Album.where("title Like ?", "%Great%").length
```

- Supprime tous les albums dont le nom contient "music".

Réponse: `=> 4 Album Destroy`
```
Album.where("title Like ?", "%music%").destroy_all
```

- Combien y a t'il d'albums écrits par AC/DC ?

Réponse: `=> 2`
```
Album.where(artist: "AC/DC").count
```
ou
```
Album.where(artist: "AC/DC").length
```

- Combien de chanson durent exactement 158589 millisecondes ?

Réponse: `=> 0`
```
Track.where(duration: 158589).count
```
ou
```
Track.where(duration: 158589).length
```

### c) Niveau Difficile

Pour ces questions, tu vas devoir effectuer des boucles dans la console Rails. C'est peu commun mais c'est faisable, tout comme dans IRB.

- puts en console tous les titres de AC/DC.


- puts en console tous les titres de l'album "Let There Be Rock".


- Calcule le prix total de cet album ainsi que sa durée totale.


- Calcule le coût de l'intégralité de la discographie de "Deep Purple".


- Modifie (via une boucle) tous les titres de "Eric Clapton" afin qu'ils soient affichés avec "Britney Spears" en artist.

