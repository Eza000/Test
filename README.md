# Musées ou pas musées, telle est la question.

# 1. Tableau

_[Source : Région Île-de-France](https://data.iledefrance.fr/explore/dataset/liste_des_musees_franciliens/information/?disjunctive.region_administrative&disjunctive.departement&basemap=mbs-5ffe02&location=8,48.73083,3.06793)_

**Dans un premier temps, je veux juste voir les musées situés à Paris et labélisés "Musées de France" :**

<iframe title="Musées situés à Paris labélisés &quot;Musée de France&quot;" aria-label="Tableau" id="datawrapper-chart-mbgXq" src="https://datawrapper.dwcdn.net/mbgXq/1/" scrolling="no" frameborder="0" style="width: 0; min-width: 100% !important; border: none;" height="887" data-external="1"></iframe><script type="text/javascript">!function(){"use strict";window.addEventListener("message",(function(a){if(void 0!==a.data["datawrapper-height"]){var e=document.querySelectorAll("iframe");for(var t in a.data["datawrapper-height"])for(var r=0;r<e.length;r++)if(e[r].contentWindow===a.source){var i=a.data["datawrapper-height"][t]+"px";e[r].style.height=i}}}))}();
</script>


# 2. Requête Wikidata

**Je veux faire une requête permettant de recenser tout les musées situés à Paris et affciher les résultats :**

```sparql
# Listes des musées situés à Paris et leur coordonnées géographiques (latitude, longitude) 
SELECT DISTINCT ?musee ?museeLabel ?lat ?long (CONCAT(STR(?lat),", ",STR(?long)) as ?lat_long)
WHERE {
  ?musee wdt:P31 wd:Q33506. # Instance de musée (Q33506) ou ses sous-classes (P31/wdt:P279*)
  ?musee wdt:P131 wd:Q90. # Situé à (P131) Paris (Q90)

  OPTIONAL { 
    ?musee wdt:P625 ?coordonees. # P625: Coordonnées géographiques
    ?musee p:P625 ?declaration.
    ?declaration psv:P625 ?coord_geo.
    ?coord_geo wikibase:geoLatitude ?lat.
    ?coord_geo wikibase:geoLongitude ?long.    
  }
  
  SERVICE wikibase:label { bd:serviceParam wikibase:language "fr,en". }
}
ORDER BY ?museeLabel
```

<iframe style="width: 80vw; height: 50vh; border: none;" src="https://query.wikidata.org/embed.html#%23%20Listes%20des%20mus%C3%A9es%20situ%C3%A9s%20%C3%A0%20Paris%20et%20leur%20coordonn%C3%A9es%20g%C3%A9ographiques%20(latitude%2C%20longitude)%20%0ASELECT%20DISTINCT%20%3Fmusee%20%3FmuseeLabel%20%3Flat%20%3Flong%20(CONCAT(STR(%3Flat)%2C%22%2C%20%22%2CSTR(%3Flong))%20as%20%3Flat_long)%0AWHERE%20%7B%0A%20%20%3Fmusee%20wdt%3AP31%20wd%3AQ33506.%20%23%20Instance%20de%20mus%C3%A9e%20(Q33506)%20ou%20ses%20sous-classes%20(P31%2Fwdt%3AP279*)%0A%20%20%3Fmusee%20wdt%3AP131%20wd%3AQ90.%20%23%20Situ%C3%A9%20%C3%A0%20(P131)%20Paris%20(Q90)%0A%0A%20%20OPTIONAL%20%7B%20%0A%20%20%20%20%3Fmusee%20wdt%3AP625%20%3Fcoordonees.%20%23%20P625%3A%20Coordonn%C3%A9es%20g%C3%A9ographiques%0A%20%20%20%20%3Fmusee%20p%3AP625%20%3Fdeclaration.%0A%20%20%20%20%3Fdeclaration%20psv%3AP625%20%3Fcoord_geo.%0A%20%20%20%20%3Fcoord_geo%20wikibase%3AgeoLatitude%20%3Flat.%0A%20%20%20%20%3Fcoord_geo%20wikibase%3AgeoLongitude%20%3Flong.%20%20%20%20%0A%20%20%7D%0A%20%20%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22fr%2Cen%22.%20%7D%0A%7D%0AORDER%20BY%20%3FmuseeLabel%0A" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups"></iframe>


# 3. Map

**Je veux afficher les musées parisiens sur une carte, avec une distinction entre les "Musées de France" et les musées tout court :**

<iframe width="100%" height="800px" frameborder="0" allowfullscreen allow="geolocation" src="//umap.openstreetmap.fr/fr/map/les-musees-parisiens_1015509?scaleControl=true&miniMap=true&scrollWheelZoom=true&zoomControl=true&editMode=disabled&moreControl=true&searchControl=true&tilelayersControl=null&embedControl=null&datalayersControl=true&onLoadPanel=caption&captionBar=true&captionMenus=true&fullscreenControl=true&locateControl=false&editinosmControl=false&starControl=false"></iframe><p><a href="//umap.openstreetmap.fr/fr/map/les-musees-parisiens_1015509?scaleControl=true&miniMap=true&scrollWheelZoom=true&zoomControl=true&editMode=disabled&moreControl=true&searchControl=true&tilelayersControl=null&embedControl=null&datalayersControl=true&onLoadPanel=caption&captionBar=true&captionMenus=true&fullscreenControl=true&locateControl=false&editinosmControl=false&starControl=false">Voir en plein écran</a></p>


# 4. Timeline

**Je veux voir la création des "Musées de France" de Paris, du plus ancient au plus récent et réparti par arrondissement. Cependant je n'arrive pas à chosir quelle option de visualisation est la plus pertinente :**


## Option 1
*L'axe des X (les dates) reste le même pour chaque option mais l'axe des Y change. Ici, il s'agit des arrondissments dans l'ordre. 
*On peut ainsi voir sur chaque ligne la création des musées, du plus ancien au plus récent. 
*On peut isoler dans la légende un arrondissment pour voir la chronologie de la création des musées dans cet arrdt spécifique ou chercher un musée précis dans la liste déroulante.
*La couleur dépend de l'arrdt du musuée.
<div class="flourish-embed flourish-scatter" data-src="visualisation/16601496"><script src="https://public.flourish.studio/resources/embed.js"></script></div>

## Option 2
*Ici, l'axe des Y est le même mais l'ordre est celui de la création des musées.
*On peut ainsi voir directment sur l'axe que le premier musée de France créé est dans le 4ème arrdt et le dernier dans le 15ème.
*On peut isoler dans la légende un musée spécifique ou chercher un arrdt dans la liste déroulante pour voir la chronologie de la création des musées dans cet arrdt.
*La couleur dépend du nom du musuée.
<div class="flourish-embed flourish-scatter" data-src="visualisation/16601384"><script src="https://public.flourish.studio/resources/embed.js"></script></div>

## Option 3
*Ici, l'axe des Y est la liste des musées du plus ancien au plus récent.
*On peut ainsi voir l'ordre de la création des musées peut importe l'arrdt.
*On peut isoler dans la légende un arrondissment pour voir la chronologie de la création des musées dans un arrdt ou chercher un musée spécifique la liste déroulante.
*La couleur dépend de l'arrdt du musée.
<div class="flourish-embed flourish-scatter" data-src="visualisation/16600049"><script src="https://public.flourish.studio/resources/embed.js"></script></div>


# Fréquentation des musées : Top 10 de 2011 à 2021

_[Source : Ministère de la Culture](https://data.culture.gouv.fr/explore/dataset/frequentation-des-musees-de-france/export/?disjunctive.nomdep)_

**Je veux voir les 10 musées les plus visités chaqhue années de 2011 à 2021 avec la part des entrées gratuite et des entrées payantes :**
<div class="flourish-embed flourish-chart" data-src="visualisation/16601101"><script src="https://public.flourish.studio/resources/embed.js"></script></div>


# Fréquentation des musées : Evolution de 2001 à 2011

_[Source : Ministère de la Culture](https://data.culture.gouv.fr/explore/dataset/frequentation-des-musees-de-france/export/?disjunctive.nomdep)_

**Je veux voir les tendances d'évolution de la fréquentation des musées de 2001 à 2021 avec les musées les plus visités et les moins visités chaque année :**
<div class="flourish-embed flourish-bar-chart-race" data-src="visualisation/16601092"><script src="https://public.flourish.studio/resources/embed.js"></script></div>

---

<3
