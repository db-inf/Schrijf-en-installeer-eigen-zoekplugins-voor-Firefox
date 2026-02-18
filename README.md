# Schrijf en installeer uw zoek-_plugins_ voor Firefox
Vroeger was het leven gemakkelijker. Ge moest uw zoek-_plugins_ gewoon kopiëren naar de _directory_ _searchPlugins/_ van uw Firefox-profiel. Zo'n gemak, dat mocht niet blijven duren van de ontwikkelaars. Nu kunt ge eigenlijk alleen nog zoek-_plugins_ installeren uit de eigen verzameling van Firefox, of vanop de website zelf van website-schrijvers die op de hoogte zijn van die mogelijkheid. Dit project biedt een uitweg om uw eigen zoek-_plugins_ te schrijven, volgens uw eigen voorkeuren, en ze zelf te installeren.

## Schrijven
Een zoek-_plugin_ is een simpel leesbaar _.xml_-bestand. In deze github repository vindt ge een paar voorbeelden. Lees [hier](https://developer.mozilla.org/en-US/docs/Web/OpenSearch) meer over de syntax van een zoek-_plugin_.

De prentjes bij zo'n zoek-_plugin_ zijn eigenlijk gewone _.png_-bestanden, maar omgevormd naar leesbare tekst in _base64_-codering. Linux-gebruikers kunnen daarvoor het programma `base64 --wrap=0 mijn.png` gebruiken, maar Google leidt u naar ettelijke websites die de omzetting voor u willen doen.

Als uw zoek-_plugin_ klaar is, open dan even zijn _.xml_-bestand in Firefox, om te controleren dat die het kan lezen zonder fouten. Firefox klaagt b.v. soms wel, soms niet over het gebruik van meer dan 1 parameter in de optie _template=waarde_ van de `<url>`-_tag_. Scheidt die parameters daarom van elkaar door een `&amp;` i.p.v. door een `&`, of beter nog: als er na de url meer parameters nodig zijn dan alleen die met de zoekterm (b.v. `http://url/zoeken.php?vraag={searchTerms})`, zet ze dan allemaal in een eigen _tag_ `<Param name="naam" value="waarde">` tussen de `<url>`- en de `</url>`-_tags_, i.p.v. in de waarde van de _template_-optie in de `<url>`-_tag_ zelf. Een voorbeeld daarvan vindt ge in het bestand [imdb-20091031.xml](imdb-20091031.xml).

## Installeren

### De zoekplugin toevoegen aan dit installatie-bestand
Zet voor elke zoek-_plugin_ een link-sectie in de header van het bestand [index.html](index.html). Recente versies van Firefox lezen daarvan mogelijk enkel de bovenste paar _link_s; zet de te installeren zoek-_plugin_ daarom bovenaan.

### De zoekplugin installeren
Ge moet nu het bestand [index.html](index.html) openen in Firefox, maar met het _file://_-protocol lukt de installatie niet: dat moet via het _http://_-protocol. Bij de meeste internet-abonnementen krijgt ge ruimte om een beperke eigen website op te zetten; de zojuist gemaakte bestanden kunnen daar perfect even bij. Maar anders kunt ge ook een private locale webserver starten, die de bestanden uit een directory aanbieden aan uw webbrowser. Voorbeelden

* die van php met `php -S 127.0.0.1:8000 -t mijnDirectory`
* die van python 2.X met `cd mijnDirectory;python -m SimpleHTTPServer 8000`
* die van python 3 met `cd mijnDirectory;python3 -m http.server 8000`
* [TinyWeb](https://www.ritlabs.com/en/products/tinyweb/install.php) (enkel voor MS Windows)

en vraag die locale server in Firefox om het bestand [http://127.0.0.1:8000/index.html](http://127.0.0.1:8000/index.html).

Kies dan welke zoek-_plugins_ te installeren:

* ofwel door te klikken op de __...__ van de adresbalk en te kiezen in "Add search engine".
* ofwel door in de zoek-balk een keuze in "Add search engine" te maken.
