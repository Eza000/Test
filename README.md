# Test
Test

# Présentation du sujet

Parce qu’il n’y avait pas assez de données sur les Français descendants d’immigrés pakistanais en France. Un sujet qui me tient à cœur (pour des raisons évidentes si vous me connaissez).

Un autre sujet qui me tient à cœur est mon âge. Je suis sur le point d’avoir 26 ans et je me rends compte que les musées vont devenir payants pour moi. Je n’aime même pas allez au musée, sauf le Musée d’Orsay, bien sûr.

Cela ne m’empêche pas de me poser quelques questions :
* Combien il y a-t-il de musée dans la ville de Paris (où j’habite) ?
* Lesquels sont-ils ?
* Quel est le profil des gens qui les fréquentent ? 
    * Quel groupe d’âge visite le plus les musées ? 
    * Il y a-t-il plus de femmes que d’hommes ?
    * Est-ce que l’envie d’aller au musée à un rapport avec le niveau et le domaine d’études ?
    * Il y a-t-il plus de Parisiens que touristes ?

# Comment répondre à ces question ? Avec l’Open Data ! Peut-être…

## Les Musées

La plateforme open data de la Région Île-de-France m’a fourni un jeu de données initial : La liste des Musées de France.

Avec un filtre sur OpenRefine je me suis retrouvée avec les 49 musées dans le département de Paris. Ou plutôt, les 49 « institutions dotées de l'appellation "Musée de France" au sens du Code du patrimoine. »

*Ici : Map des Musées de France à Paris*
<iframe width="100%" height="300px" frameborder="0" allowfullscreen allow="geolocation" src="//umap.openstreetmap.fr/fr/map/new/?scaleControl=true&miniMap=false&scrollWheelZoom=true&zoomControl=true&editMode=disabled&moreControl=true&searchControl=true&tilelayersControl=null&embedControl=null&datalayersControl=true&onLoadPanel=undefined&captionBar=false&captionMenus=true&fullscreenControl=true"></iframe><p><a href="//umap.openstreetmap.fr/fr/map/new/?scaleControl=true&miniMap=false&scrollWheelZoom=true&zoomControl=true&editMode=disabled&moreControl=true&searchControl=true&tilelayersControl=null&embedControl=null&datalayersControl=true&onLoadPanel=undefined&captionBar=false&captionMenus=true&fullscreenControl=true">Voir en plein écran</a></p>


Mais alors, combien est-ce qu'il y a vraiment de musées dans la ville de Paris ?

Une première recherche m’a amené sur la page Wikipédia de la Catégorie:Musée à Paris. Cette page présente 96 liens vers des pages qui ne sont pas toutes celles de musées.

Que faire ? Consulter les 96 liens et vérifier, pour chacun, s’il s’agit bien de la page d'un musée ? Ou alors, faire une requête SPARQL sur Wikidata Query Service permettant de recenser les musées situés à Paris ? 

Go sur Wikidata !

```sparql
# Listes des musées situés à Paris, leurs coordonnées géographiques et leurs images
#defaultView:ImageGrid
SELECT ?musee ?museeLabel ?coordonnees ?image
WHERE {
  ?musee wdt:P31/wdt:P279* wd:Q33506. # Instance of: musée (Q33506) or subclass of museum
  ?musee wdt:P131 wd:Q90. # Located in: Paris (Q90)

  OPTIONAL {
    ?musee wdt:P625 ?coordonnees. # Coordinates
    ?museum wdt:P18 ?image.
  }

  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }
}
ORDER BY ?museeLabel
```


<iframe style="width: 55vw; height: 50vh; border: none;" src="https://query.wikidata.org/#%23%20Listes%20des%20mus%C3%A9es%20situ%C3%A9s%20%C3%A0%20Paris%2C%20leurs%20coordonn%C3%A9es%20g%C3%A9ographiques%20et%20leurs%20images%0A%23defaultView%3AImageGrid%0ASELECT%20%3Fmusee%20%3FmuseeLabel%20%3Fcoordonnees%20%3Fimage%0AWHERE%20%7B%0A%20%20%3Fmusee%20wdt%3AP31%2Fwdt%3AP279%2a%20wd%3AQ33506.%20%23%20Instance%20of%3A%20mus%C3%A9e%20%28Q33506%29%20or%20subclass%20of%20museum%0A%20%20%3Fmusee%20wdt%3AP131%20wd%3AQ90.%20%23%20Located%20in%3A%20Paris%20%28Q90%29%0A%0A%20%20OPTIONAL%20%7B%0A%20%20%20%20%3Fmusee%20wdt%3AP625%20%3Fcoordonnees.%20%23%20Coordinates%0A%20%20%20%20%3Fmuseum%20wdt%3AP18%20%3Fimage.%0A%20%20%7D%0A%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%7D%0AORDER%20BY%20%3FmuseeLabel" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups" ></iframe>



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
