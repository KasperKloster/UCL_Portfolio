---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: page
---

# Intro
<b><a href="#f_app">App udvikling</a></b> er valgt grundet at kunne udvikle til alle (Apple) enheder, og prøve noget andet end webudvikling, konsol og .NET <br>
Der vil dog primært være fokus på macOS, i det at projektet mest er beregnet til Desktop<br>
Derudover giver det også muligheden for at lære et nyt sprog (Swift) og en ny IDE (Xcode)<br>
<b><a href="#f_back">Backend arkitektur</a></b> er valgt grundet tidligere projekter, der har vokset og jeg ikke engang selv kan finde rundt i det længere<br>
Derfor har jeg set vigtigheden i at have en klar arkitektur, der følger faste principper, og gør at jeg ikke skal opfinde en selv og dokumentere den.<br>
<b><a href="#f_goal">Læringsmål</a></b> Længere ned af siden her, vises mine læringsmål for de to fag.<br>
Der er to sider for App udvikling og Backend udvikling, hvor at læringsmålene er delt ind til mindre bidder og hertil også reflektioner og læringsressourcer<br>
Alle mål der har været igennem semesteret, er hvad jeg mener, hvilken viden jeg mangler på nuværende tidspunkt, for at kunne udvikle flere apps i fremtiden<br>
<br><br>
<b>Projekter</b> Der har været to projekter. Et med mit team og et for mig selv. Dette er grundet at IOS udvikling ikke passede til teamets projekt<br>
Solo projektet viser App udvikling (IOS) og backend arkitektur (VIPER).<br>
Projekt med team viser forståelsen af backend arkitektur (Clean architecure), samt samarbejde med GitHub.<br>
De to projekter har været med henblik på samme virksomhed og deres udfordringer.
<br><br>
<b><a href="{{ site.baseurl }}/proces">Læringsprocessen</b></a> for dette semester og projekterne er vist her.

## Kobling mellem App udvikling og Backend arkitektur
Om vi udvikler en app, website eller console, har arkitekturen en vigtigthed i forhold til:
<ul>
    <li>Dokumentation</li>
    <li>Skalerbarhed</li>
    <li>Vedligholdelse</li>
    <li>Test</li>
</ul>

## Overordnet mål
For de to valgfag er det overordnet mål.
En macOS fuld CRUD app, der fungerer lokalt (Ikke deployed til Apple Store), der connectes til en ekstern API, database, tests og skalerbar.<br/>
Hertil få en viden og praktisk via god arkitektur.
<br/>
Projektet er delt op igennem delmål (For Swift og Backend arkitektur), jeg skal lære for at kunne udvikle en applikation.<br/>
De resourcer som jeg har brugt vil være listet op nederest på siderne.<br/>
Jeg har løbende skrevet længere logbog omkring, hvad jeg har gennemgået og hvilke udfordringer der har været.

## Læringsmål
{: #f_goal}

### <a href="{{ site.baseurl }}/app_udvikling">Fag: App Udvikling</a>
{: #f_app}
#### Viden - Den studerende har viden om
<ul>
    <li>De grundlæggende elementer i Swift: Datatyper, variabler, funktioner, klasser mm.</li>
    <li>Grundlæggende navigation i Xcode (Apples IDE).</li>
    <li>Forskellen på SwifiUI, UIKit og Storyboards</li>
    <li>Forskellige database muligheder (Core data og Firestore)</li>
    <li>Brug og integration af API’er i Swift</li>
    <li>Principperne bag backend arkitektur: Med fokus på VIPER</li>
    <li>Betydning af tests i app udvikling</li>
    <li>Fordele og ulemper ved Cross platform development muligheder vi har i skrivende stund. (React native, Flutter, Maui)</li>
</ul>

#### Færdigheder - Den studerende kan
<ul>
    <li>Udvikle en multiplatform IOS app (Swift)</li>
    <li>Oprette og designe vha. SwiftUI eller UIKit</li>
    <li>Forbinde og bruge eksterne services via API</li>
    <li>Persistens vha. Database med CRUD.</li>
    <li>Brug af tests i workflow for kodekvalitet</li>
    <li>Udvikle en app med en klar arkitektur med henblik på skalering.</li>
</ul>

#### Kompetencer - Den studerende kan:
<ul>
    <li>Planlægge og udvikle en IOS app fra ide til færdig produkt</li>
    <li>Anvende arkitektur såsom VIPER, for at sikre en klar struktur.</li>
    <li>Implementere eksterne API’er og manipulere dens data og indsætte data.</li>
    <li>Brug af database (CRUD)</li>
    <li>Test og debug applikation</li>
    <li>Brug af udviklingsværktøjer til samarbejde med et team (Git)</li>
</ul>

### <a href="{{ site.baseurl }}/backend_arkitektur">Fag: Backend arkitektur</a>
{: #f_backend}

#### Viden - Den studerende har viden om
<ul>
    <li>Grundlæggende principper og lag i Clean Architecture (Core, Application, Interfaces etc.)</li>
    <li>Grundlæggende principper i VIPER (View, interactor, presenter, entity, router)</li>
    <li>Konceptet loose coupling, high dependency</li>
    <li>Testing i Clean architecture og VIPER</li>
</ul>

#### Færdigheder - Den studerende kan
<ul>
    <li>Implementere og anvende arkitektur i et projekt (Clean architecture i .NET, VIPER i Swift)</li>
    <li>Have en god og klar mappestruktur, der afspejler arkitekturen.</li>
    <li>Udvikle et projekt med henblik på skalering, der følger arkitekturen.</li>
    <li>Opsætte og vedligeholde UML diagrammer,  der viser arkitekturen</li>
</ul>

#### Kompetencer - Den studerende kan:
<ul>
    <li>Designe (UML) og implementere backend arkitektur</li>
    <li>Teste arkitektur</li>
    <li>Udvikle og vedligeholde et projekt, der passer til team og skalering.</li>
</ul>