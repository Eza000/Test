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



Mais alors, combien est-ce qu'il y a vraiment de musées dans la ville de Paris ?

Une première recherche m’a amené sur la page Wikipédia de la Catégorie:Musée à Paris. Cette page présente 96 liens vers des pages qui ne sont pas toutes celles de musées.

Que faire ? Consulter les 96 liens et vérifier, pour chacun, s’il s’agit bien de la page d'un musée ? Ou alors, faire une requête SPARQL sur Wikidata Query Service permettant de recenser les musées situés à Paris ? 

Go sur Wikidata !

```sparql
# Listes des musées situés à Paris,
...
```


## Première visualisation
<iframe title="Les Musées De France situés à Paris" aria-label="Tableau" id="datawrapper-chart-y6Jis" src="https://datawrapper.dwcdn.net/y6Jis/2/" scrolling="no" frameborder="0" style="width: 0; min-width: 100% !important; border: none;" height="2099" data-external="1"></iframe><script type="text/javascript">!function(){"use strict";window.addEventListener("message",(function(a){if(void 0!==a.data["datawrapper-height"]){var e=document.querySelectorAll("iframe");for(var t in a.data["datawrapper-height"])for(var r=0;r<e.length;r++)if(e[r].contentWindow===a.source){var i=a.data["datawrapper-height"][t]+"px";e[r].style.height=i}}}))}();
</script>

*Ici : Map des Musées de France à Paris*
<iframe width="100%" height="600px" frameborder="0" allowfullscreen allow="geolocation" src="//umap.openstreetmap.fr/fr/map/map_v3_1015509?scaleControl=true&miniMap=true&scrollWheelZoom=true&zoomControl=true&editMode=disabled&moreControl=true&searchControl=true&tilelayersControl=null&embedControl=null&datalayersControl=true&onLoadPanel=caption&captionBar=true&captionMenus=true&fullscreenControl=true&measureControl=true"></iframe><p><a href="//umap.openstreetmap.fr/fr/map/map_v3_1015509?scaleControl=true&miniMap=true&scrollWheelZoom=true&zoomControl=true&editMode=disabled&moreControl=true&searchControl=true&tilelayersControl=null&embedControl=null&datalayersControl=true&onLoadPanel=caption&captionBar=true&captionMenus=true&fullscreenControl=true&measureControl=true">Voir en plein écran</a></p>

## Deuxième visualisation
*Ici : Fréq des Musées de France à Paris*
<div class="flourish-embed flourish-chart" data-src="visualisation/16527002"><script src="https://public.flourish.studio/resources/embed.js"></script></div>

## Troisième visualisation
*Ici : Timeline des à Paris*
Analyse
<script type="text/javascript" src="https://www.gstatic.com/charts/loader.js"></script>

  <script type="text/javascript">
    google.charts.load("current", {packages:["timeline"]});
    google.charts.setOnLoadCallback(drawChart);
    function drawChart() {
      var container = document.getElementById('example7.1');
      var chart = new google.visualization.Timeline(container);
      var dataTable = new google.visualization.DataTable();
      dataTable.addColumn({ type: 'string', id: 'Room' });
      dataTable.addColumn({ type: 'string', id: 'Name' });
      dataTable.addColumn({ type: 'date', id: 'Start' });
      dataTable.addColumn({ type: 'date', id: 'End' });
      dataTable.addRows([
        [ 'Magnolia Room', 'Google Charts', new Date(0,0,0,14,0,0), new Date(0,0,0,15,0,0)],
        [ 'Magnolia Room', 'App Engine',    new Date(0,0,0,15,0,0), new Date(0,0,0,16,0,0)]]);

      var options = {
        timeline: { showRowLabels: false },
        avoidOverlappingGridLines: false
      };

      chart.draw(dataTable, options);
    }

  </script>

  <div id="example7.1" style="height: 200px;"></div>


```sparql
#defaultView:Timeline
SELECT ?entite ?entiteLabel ?dateCreation
WHERE {
  VALUES ?entite { wd:Q1667022 wd:Q1572452 wd:Q88640485 wd:Q860166 wd:Q3330482 wd:Q2445818 wd:Q2919066 wd:Q726781 wd:Q1538826 wd:Q178065 wd:Q1782606 wd:Q2597719 wd:Q547789 wd:Q85854194 wd:Q2915606 wd:Q1094332 wd:Q2613771 wd:Q106448129 wd:Q1955698 wd:Q1998638 wd:Q1124095 wd:Q838691 wd:Q650519 wd:Q88645654 wd:Q2714932 wd:Q3330260 wd:Q1632912 wd:Q1319378 wd:Q19675 wd:Q977732 wd:Q549143 wd:Q3329213 wd:Q23402 wd:Q2715373 wd:Q857276 wd:Q167863 wd:Q1579504 wd:Q1094302 wd:Q1128657 wd:Q743206 wd:Q1996069 wd:Q1954498 wd:Q2296362 wd:Q2599177 wd:Q640447 wd:Q43688220 wd:Q820892 wd:Q860994 wd:Q3329915 
}  # Remplacez ces QIDs par votre liste d'entités
  OPTIONAL { ?entite wdt:P571 ?dateCreation. }
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }
}
ORDER BY ?dateCreation
```

<iframe style="width: 80vw; height: 50vh; border: none;" src="https://query.wikidata.org/embed.html#%23defaultView%3ATimeline%0ASELECT%20%3Fentite%20%3FentiteLabel%20%3FdateCreation%0AWHERE%20%7B%0A%20%20VALUES%20%3Fentite%20%7B%20wd%3AQ1667022%20wd%3AQ1572452%20wd%3AQ88640485%20wd%3AQ860166%20wd%3AQ3330482%20wd%3AQ2445818%20wd%3AQ2919066%20wd%3AQ726781%20wd%3AQ1538826%20wd%3AQ178065%20wd%3AQ1782606%20wd%3AQ2597719%20wd%3AQ547789%20wd%3AQ85854194%20wd%3AQ2915606%20wd%3AQ1094332%20wd%3AQ2613771%20wd%3AQ106448129%20wd%3AQ1955698%20wd%3AQ1998638%20wd%3AQ1124095%20wd%3AQ838691%20wd%3AQ650519%20wd%3AQ88645654%20wd%3AQ2714932%20wd%3AQ3330260%20wd%3AQ1632912%20wd%3AQ1319378%20wd%3AQ19675%20wd%3AQ977732%20wd%3AQ549143%20wd%3AQ3329213%20wd%3AQ23402%20wd%3AQ2715373%20wd%3AQ857276%20wd%3AQ167863%20wd%3AQ1579504%20wd%3AQ1094302%20wd%3AQ1128657%20wd%3AQ743206%20wd%3AQ1996069%20wd%3AQ1954498%20wd%3AQ2296362%20wd%3AQ2599177%20wd%3AQ640447%20wd%3AQ43688220%20wd%3AQ820892%20wd%3AQ860994%20wd%3AQ3329915%20%0A%7D%20%20%23%20Remplacez%20ces%20QIDs%20par%20votre%20liste%20d'entit%C3%A9s%0A%20%20OPTIONAL%20%7B%20%3Fentite%20wdt%3AP571%20%3FdateCreation.%20%7D%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%7D%0AORDER%20BY%20%3FdateCreation%0A" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups"></iframe>


# Conclusion
Conclusion générale

---
