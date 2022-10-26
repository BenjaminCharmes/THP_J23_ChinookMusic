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

Réponse: `=>
For Those About To Rock (We Salute You)
Put The Finger On You
Lets Get It Up
Inject The Venom
Snowballed
Evil Walks
C.O.D.
Breaking The Rules
Night Of The Long Knives
Spellbound
Go Down
Dog Eat Dog
Let There Be Rock
Bad Boy Boogie
Problem Child
Overdose
Hell Aint A Bad Place To Be
Whole Lotta Rosie`
``` Ruby
Track.where(artist: "AC/DC").each do |track|
  puts track.title
end
```

- puts en console tous les titres de l'album "Let There Be Rock".

Réponse: `=> 
Go Down
Dog Eat Dog
Let There Be Rock
Bad Boy Boogie
Problem Child
Overdose
Hell Aint A Bad Place To Be
Whole Lotta Rosie`
``` Ruby
Track.where(album: "Let There Be Rock").each do |track|
  puts track.title
end
```

- Calcule le prix total de cet album ainsi que sa durée totale.

Réponse: `=> 
price = 7.92
duration = 2453259`
``` Ruby
price = 0
duration = 0
Track.where(album: "Let There Be Rock").each do |track|
  duration += track.duration
  price += track.price
end
price
duration
```

- Calcule le coût de l'intégralité de la discographie de "Deep Purple".

Réponse: `=> 90.09`
``` Ruby
total_deep_purple_price = 0
Track.where(artist: "Deep Purple").each do |track|
  total_deep_purple_price += track.price
end
total_deep_purple_price
```

- Modifie (via une boucle) tous les titres de "Eric Clapton" afin qu'ils soient affichés avec "Britney Spears" en artist.

Réponse: `=> 👍`
``` Ruby
Track.where(artist: "Eric Clapton").each do |track|
  track.update(artist: "Britney Spears")
end
```