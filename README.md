# Test
Test

# Présentation du sujet

Parce qu’il n’y avait pas assez de données sur les Français descendants d’immigrés pakistanais en France. Un sujet qui me tient à cœur (pour des raisons évidentes si vous me connaissez).

Un autre sujet qui me tient à cœur est mon âge. Je suis sur le point d’avoir 26 ans et je me rends compte que les musées vont devenir payants pour moi. Je n’aime même pas allez au musée, sauf le Musée d’Orsay, bien sûr.

Cela ne m’empêche pas de me poser quelques questions :
    -	Combien il y a-t-il de musée dans la ville de Paris (où j’habite) ?
    -	Lesquels sont-ils ?
    -	Quel est le profil des gens qui les fréquentent ? 
            o	Quel groupe d’âge visite le plus les musées ? 
            o	Il y a-t-il plus de femmes que d’hommes ?
            o	Est-ce que l’envie d’aller au musée à un rapport avec le niveau et le domaine d’études ?
            o	Il y a-t-il plus de Parisiens que touristes ?

# Comment répondre à ces question ? Avec l’Open Data ! Peut-être…

## Les Musées

La plateforme open data de la Région Île-de-France m’a fourni un jeu de données initial : La liste des Musées de France.

Avec un filtre sur OpenRefine je me suis retrouvée avec les 49 musées dans le département de Paris. Ou plutôt, les 49 « institutions dotées de l'appellation "Musée de France" au sens du Code du patrimoine. »

*Ici : Map des Musées de France à Paris*


Mais alors, combien est-ce qu'il y a vraiment de musées dans la ville de Paris ?

Une première recherche m’a amené sur la page Wikipédia de la Catégorie:Musée à Paris. Cette page présente 96 liens vers des pages qui ne sont pas toutes celles de musées.

Que faire ? Consulter les 96 liens et vérifier, pour chacun, s’il s’agit bien de la page d'un musée ? Ou alors, faire une requête SPARQL sur Wikidata Query Service permettant de recenser les musées situés à Paris ? 

Go sur Wikidata !

```sparql
#defaultView:ImageGrid
SELECT
  ?arr
  (SAMPLE (?titleL) AS ?title)
  (SAMPLE (?img) AS ?image)
  (SAMPLE (?coord) AS ?coordinates) {

    {
      SELECT DISTINCT ?arr {
        ?arr  wdt:P131 wd:Q90;}
    }
    # title
    OPTIONAL { ?arr rdfs:label ?titleL filter (lang(?titleL) = "fr") }
   
    # image
    OPTIONAL { ?arr wdt:P18 ?img }
   
    # coordinates
    OPTIONAL { ?arr wdt:P625 ?coord }

} GROUP BY ?arr
LIMIT 1500 
```


<iframe style="width: 55vw; height: 50vh; border: none;" src="https://query.wikidata.org/embed.html#%23defaultView%3AImageGrid%0ASELECT%0A%20%20%3Farr%0A%20%20%28SAMPLE%20%28%3FtitleL%29%20AS%20%3Ftitle%29%0A%20%20%28SAMPLE%20%28%3Fimg%29%20AS%20%3Fimage%29%0A%20%20%28SAMPLE%20%28%3Fcoord%29%20AS%20%3Fcoordinates%29%20%7B%0A%0A%20%20%20%20%7B%0A%20%20%20%20%20%20SELECT%20DISTINCT%20%3Farr%20%7B%0A%20%20%20%20%20%20%20%20%3Farr%20%20wdt%3AP131%20wd%3AQ90%3B%7D%0A%20%20%20%20%7D%0A%20%20%20%20%23%20title%0A%20%20%20%20OPTIONAL%20%7B%20%3Farr%20rdfs%3Alabel%20%3FtitleL%20filter%20%28lang%28%3FtitleL%29%20%3D%20%22fr%22%29%20%7D%0A%20%20%20%0A%20%20%20%20%23%20image%0A%20%20%20%20OPTIONAL%20%7B%20%3Farr%20wdt%3AP18%20%3Fimg%20%7D%0A%20%20%20%0A%20%20%20%20%23%20coordinates%0A%20%20%20%20OPTIONAL%20%7B%20%3Farr%20wdt%3AP625%20%3Fcoord%20%7D%0A%0A%7D%20GROUP%20BY%20%3Farr%0ALIMIT%201500" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups" ></iframe>



# Jeu de données
Les jeux de données utilisés : ...

# OpenRefine & WikiData
Utilisation d'OpenRefine et WikiData

# Les Visualisations

## Première visualisation
Analyse

## Deuxième visualisation
Analyse

## Troisième visualisation
Analyse

# Conclusion
Conclusion générale

---
