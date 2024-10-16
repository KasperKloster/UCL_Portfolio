---
layout: page
title: Log
permalink: /Log/
---
# Log

## September
<ul>
    <li>Forståelse projektet</li>
    <li>Opsæt delmål</li>
    <li>Research af Swift (Tutorials)</li>
    <li>Swift vs UIKit (Programmatic UI)</li>
    <li>Research af Arkitektur (Clean architecture og VIPER)</li>
    <li>Opsæt Projektplan i GitHub</li>
    <li>Oprettet Wireframes og Mockup</li>
    <li>Valg af Arkitektur (VIPER)</li>
    <li>Valg af UI Framework</li>
    <li>Opsæt af projekt i Xcode</li>
</ul>

### Notes
At skrive projektet op og indsætte læringsmål.
<br/>

#### Backend
September har stået på research: Hvilken backend arkitektur skal der bruges? <br/>
Valget er endt på VIPER - Det ser ud til at være det mest avanceret, men også mest brugbart i forlhold til skalering.<br/>
Derudover så er det kraftigt inspireret af Clean Architecture, som bruges i .NET projektet.<br/>
Ulemple ved VIPER er dog at der bruges længere tid på kode. Fordelen er at vi har en god struktur<br/>
Derudover er Viper også til større projekter og har en stejlere læringskurve.<br/> 
Min tankegang er; Forstår jeg en mere "avanceret" arkitektur, vil det være nemmere at forstå en "simpel" arkitektur (MVC)<br/> 
<br/>
Hertil er der også undersøgt om der skal brugers UIKit, AppKit eller SwiftUI<br/>
Det gode ved AppKit (Imperative programming) er at vi har mere kontrol. Men der er mere at kode og har en stejlere læringskurve<br/>
<br/>
SwiftUI (Declarative programming) er hurtigere at komme igang med og virker på tværs af Apples enheder (cross development)<br/>
Derudover virker det også til at Apple fokuserer på dette, samt at det er nemmere at finde læringsmateriale.
<br/><br/>
Derudover er der også undersøgt hvilke mappestruktur: Layer-based eller Feature-based.<br/>
Feature-based synes jeg ser mest organiseret ud.
<br/>
Hertil er der også lavet wireframes til et overordnet layout, så jeg har noget at gå efter.

#### Swift
Der er brugt tid på at lære syntax, og blive mere bekvemt med Xcode<br/>
Derudover er der undersøgt forskellen på SwiftUI, AppKit og storyboards for at finde den udviklingstil, der passer mig bedst.<br/>
Derudover har jeg så læst på protocols - i Viper snakker lagende sammen via protocols, derfor er forståelse af disse vigtigt.

## Oktober
Fra teori til hands-on. <br/>
Der er oprettet et projekt i Xcode, og sat en helt simpel applikation op<br/>
I første omgang er der kun fokuseret på forståelsen af Viper og data-binding i Swift.<br/>

### Database
Ingen app uden Database<br/>
Jeg har undersøgt hvilken database, vil være bedst for projektet.<br/>
Jeg har valgt Firestore, grundet at jeg kan se det smarte i at man kan have én database på tværs af platforme.<br/>
Derudover tilbyder den gratis version mere end rigeligt til mit behov - Apples eget kan hurtigt koste.
<br/><br/>
Jeg har brugt timer, og med timer mener jeg dage, på at få hul igennem.
Opsætningen var ret enkelt, men forbindelsen fra App til Firestore gad den bare ikke...
Jeg fik en fejl at det var min internet forbindelse eller at firewall blokerede firestore.googleapis.com<br/>
Efter at havde prøvet forskellige forbindelser, kunne jeg udelukke den grund.
Jeg debuggede, omskrev koden, research... Alt. Intet virkede.
<br/>
Jeg opsatte en hurtig side i Javascript, og der fungerede forbindelsen. - Documents blev vist.<br/>
I Xcode rodede jeg rundt i diverse indstillinger og der fandt jeg to manglende flueben ved Incomming og Outgoing connections
"Tjek, Tjek" og der var hul igennem!


TDD, testing via Swift Tests<br/>
