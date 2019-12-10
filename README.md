# Schrijf en installeer uw zoek-plugins voor Firefox
Vroeger was het leven gemakkelijker. Ge moest uw zoekplugins gewoon kopiëren naar de directory _searchPlugins_ van uw Firefox profiel. Zo'n gemak, dat mocht niet blijven duren van de ontwikkelaars. Nu kunt ge eigenlijk alleen nog zoekplugins installeren uit de eigen verzameling van Firefox, of vanop de website zelf van website-schrijvers die op de hoogte zijn van die mogelijkheid. Dit project biedt een uitweg om uw eigen zoekplugins te schrijven, volgens uw eigen voorkeuren, en ze zelf te installeren.
## Schrijven
Een zoek-plugin is een simpel leesbaar _.xml_-bestand. Hier vindt ge meer over de [syntax van een zoek-plugin](https://developer.mozilla.org/en-US/docs/Web/OpenSearch). In deze github repository vindt ge een paar voorbeelden.

De prentjes bij zo'n zoekplugin zijn eigenlijk gewone _.png_-bestanden, maar omgevormd naar leesbare tekst in _base64_ codering. Linux-gebruikers kunnen daarvoor het programma `base64 --wrap=0 mijn.png` gebruiken, maar Google leidt u naar ettelijke websites die de omzetting voor u willen doen.

Als uw zoek-plugin klaar is, open dan dat _.xml_-bestand in Firefox, om te controleren dat die het kan lezen zonder fouten. Firefox klaagt b.v. soms wel, soms niet over het gebruik van meer dan 1 parameter in de _template_ van de `&lt;url&gt;`-_tag_. Scheidt die parameters daarom van elkaar door een &amp;amp; i.p.v. door een &amp;, of beter nog: als er na de url meer parameters nodig zijn dan alleen die met de zoekterm (b.v. _http://url/zoeken.php?vraag={searchTerms})_, zet ze dan allemaal in een eigen _tag_ `&lt;Param name="naam" value="waarde"&gt; tussen de `&lt;url&gt;`- en de `&lt;/url&gt;`-_tags_, i.p.v.  als opties in de `&lt;url&gt;`-_tag_ zelf. Een voorbeeld daarvan vindt ge in het bestand [](imdb-20091031.xml)

## Installeren

### De zoekplugin toevoegen aan dit installatie-bestand
Zet voor elke zoek-plugin een link-sectie in de header van het bestand [](index.html).

### De zoekplugin installeren
Ge moet nu het bestand [](index.html) openen in Firefox, maar met het _file://_-protocol lukt de installatie niet: dat moet via het _http://_-protocol. Start daarom een private locale webserver, b.v. die van php met `php -S localhost:8000 -t mijnDirectory`, en vraag die om het bestand [index.html](http:localhost:8000/index.html) in Firefox.

Kies dan welke plugins te installeren:

	* ofwel door te klikken op de ... van de adresbalk en te kiezen in "Add search engine"
	* ofwel in de zoek-balk een keuze in "Add search engine" te maken
