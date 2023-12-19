# Opdrachtbeschrijving

## Inleiding

Vorige week heb je het blogplatform Blogventure voor je vrienden Freek en Bernard opgezet. Omdat ze weten dat je geen
tijd hebt om óók nog de backend te bouwen, hebben ze dit door iemand anders laten doen. Jij kunt alle blogposts straks
opvragen door requests te maken naar [deze backend](https://github.com/hogeschoolnovi/frontend-fake-blog-database) (
webAPI).

![logo.png](src/assets/logo-black.png)

## Applicatie starten

Deze opdracht is een vervolg op [part 1](https://github.com/hogeschoolnovi/frontend-react-blog-part1), dus je kunt
verder werken in jouw eigen project. Wel zul je de blogventure
backend moeten clonen om er gebruik van te kunnen maken. Dit betekent dat je twee projecten tegelijkertijd aan het
runnen bent:
jouw Blogventure frontend en jouw Blogventure backend.
Clone [deze backend](https://github.com/hogeschoolnovi/frontend-fake-blog-database) naar jouw eigen computer en start
deze op
volgens de instructies in de `README.md`. Lees de documentatie goed door, zodat je weet welke endpoints
er beschikbaar zijn. Op basis van de volgende opdrachten zul je namelijk zelf moeten bedenken waar het request naartoe
moet.

## Opdracht 1 - Oefenrequests (in de console)

_Tip:_ begin een nieuw, schoon frontend projectje zodat je onbezorgd kunt oefenen met de requests, voordat je dit
implementeert in je bestaande blogventure applicatie. Scheelt een hoop verwarring en zoekwerk!

1. **Blogposts ophalen:** maak een tijdelijke button, zodat je daar jouw asynchrone functie aan kunt koppelen. Maak een
   request naar de backend om _alle_ posts op te halen en log deze in de console;
2. **Post 6 ophalen:** maak nog een button en gebruik deze om de informatie over de post met `id` 6 op te halen uit de
   backend. Log deze gegevens in de console;
3. **Nieuwe post toevoegen:** maak nóg een button en zorg ervoor dat er een nieuwe blogpost wordt toegevoegd aan de
   database,
   wanneer de gebruiker hierop klikt. Dit mag je voor nu doen met deze hardcoded-data:

```json
{
  "title": "Wat gebruiker heeft ingevuld",
  "subtitle": "Wat gebruiker heeft ingevuld",
  "content": "Wat gebruiker heeft ingevuld, in dit geval minder dan 100 woorden",
  "author": "Voornaam achternaam",
  "created": "2023-09-21T09:30:00Z",
  "readTime": 1,
  "comments": 0,
  "shares": 0
}
```

Zorg ervoor dat er succesmelding in de console wordt gelogd bij succes en een foutmelding in de console bij een mislukte
poging.

4. Check, check, dubbelcheck: als je nu opnieuw alle posts ophaalt door op de haal posts op-knop te klikken, staat jouw
   toegevoegde to-do daar nu bij? 😍
5. **Post verwijderen:** maak een button en gebruik de `id` van de laatste blogpost uit de lijst om deze uit de backend
   te
   verwijderen (bijvoorbeeld `16`, `17` of `18`). Deze `id` mag je voor nu gewoon even handmatig overtypen (hardcoded).
   Zorg ervoor dat er bij success een
   melding in de console wordt gelogd en een foutmelding bij een mislukte poging (wanneer de post al verwijderd is,
   bijvoorbeeld!);
6. **Post wijzigen:** maak nog een button en gebruik de `id` van de eerst blogpost uit de lijst om daarvan de subtitel
   te wijzgen. Let erop dat je **alle** informatie van deze post meestuurt - ook de velden die niet
   worden aangepast! - anders verlies je gegevens. Ook hier wil je een succes- en foutmelding bij maken. Controleer of
   de wijziging gelukt is door daarna weer op de knop te klikken die alle posts ophaalt.

## Opdracht 2 - Alle posts ophalen en weergeven

Wanneer de gebruiker op de overzichtspagina komt, willen we natuurlijk direct beginnen met het ophalen en weergeven van
alle posts. Inmiddels weet je dat je daar een mounting-effect voor nodig hebt.

1. Zorg ervoor dat alle posts worden opgehaald wanneer de overzichtspagina geladen wordt. Deze log je eerst in de
   console.
2. Om de posts straks te kunnen weergeven op de pagina maak je een stukje State aan, waarin je de opgehaalde posts kunt
   opslaan.
3. Nu is het tijd om de State ook te gaan gebruiken. Zorg ervoor dat de data die gebruikt wordt om de posts op de pagina
   weer te geven niet
   meer uit het JSON-bestand komt, maar uit jouw State-variabele. Om er nu voor te zorgen dat de app niet crasht als er
   nog geen
   data is, of als er geen data opgehaald kan worden, implementeer je een extra check op de plek waar je over de posts
   heen mapt.
4. Zorg ervoor dat er een passende foutmelding weergegeven wordt op de pagina wanneer het ophalen van de data mislukt.
   Zo weet de gebruiker altijd waar 'ie aan toe is!

## Opdracht 3 - Specifieke post ophalen en weergeven

We gaan hetzelfde doen op de pagina waar je de details over één post laat zien. Hiervoor halen we natuurlijk niet weer
alle posts op, maar alleen de informatie over die éne post die we willen weergeven. Doorloop hier weer dezelfde stappen:

1. Zorg ervoor dat de juiste post wordt opgehaald (op basis van de `id`) wanneer de detailpagina geladen wordt. Dit log
   je eerst in de console.
2. Om de post te kunnen weergeven op de pagina maak je een stukje State aan, waarin je de opgehaalde data kunt
   opslaan.
3. Zorg ervoor dat de data die gebruikt wordt om de post op de pagina weer te geven niet
   meer uit het JSON-bestand komt, maar uit jouw State-variabele. Ook hier implementeer je weer een extra check bij het
   weergeven van de data, mocht er onverhoopt een leeg object terugkomen.
4. Zorg ervoor dat er een passende foutmelding weergegeven wordt op de pagina wanneer het ophalen van de data mislukt.

## Opdracht 3 - Formulier werkend maken

We hebben ons formulier natuurlijk al zo opgebouwd dat alle juiste informatie in een object verzameld wordt wanener de
gebruiker het formulier submit. Er wordt echter niets verzonden... Dus ook daar gaan we verandering in brengen! Omdat
dit request getriggerd wordt op basis van een submit-event, hoef je hier geen effect-hook te gebruiken.

1. Breidt de huidige `handleSubmit` functie uit, door er een _asynchrone functie_ van te maken en voeg een `try/catch`
   -blok toe.
2. Verstuur de verzamelde data op de voorgeschreven manier naar de backend.
3. Kijk goed naar de informatie die je terugkrijgt wanneer het request succesvol is uitgevoerd. Is alles goed gegaan?
   Zorg ervoor dat het formulier verdwijnt. In plaats daarvan moet de volgende boodschap op de pagina worden weergegeven:

> De blogpost is succesvol toegevoegd. Je kunt deze hier `<link-naar-post>` bekijken.

4. Ging er iets mis? Dan blijft het formulier staan en geef je een rode foutmelding weer.

## Bonusopdracht
* Zorg ervoor dat de gebruiker posts kan verwijderen doormiddel van een 'delete'-knop op de detailpagina.
