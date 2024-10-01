---
layout: page
title: Backend Arkitektur
permalink: /backend_arkitektur/
---
# Backend Udvikling

## Intro


## Læringsmål / Delmål
<ul>
    <li>Research arkitektur muligheder</li>
    <li>Valg af arkitektur</li>
</ul>

## Valg af Arkitektur
Udefra research er valget endt på VIPER.

## Clean architecture

### Delmål
<ul>
    <li>Overordnet forståelse</li>
    <li>Overordnet mappe struktur</li>
</ul>

Clean architecture er et princip, der går ud på at seperare applikationen i flere lag (seperations of concerns).<br/>
Fordelen her er at vi kan seperare eks. UI fra vores logik, model og database.<br/>
Dette gør det nemmere at vedligholde og teste.<br/>

I forhold til App udvklingen vil en simpel mappe strukturer kunne se således ud:
<ul>
    <li>Root</li>
    <ul>
        <li><a href="#entities">Entities</a></li>
    </ul>
    <ul>
        <li><a href="#views">Views</a></li>
        <ul>
            <li><a href="#layouts">Layouts</a></li>
            <li><a href="#pages">Pages</a></li>
            <li><a href="#resources">Resources</a></li>
        </ul>
    </ul>
</ul>

### Entities (Core business Models)
{: #entities}
High level, kerne modeller såsom product.<br/>
De står for data structures og validering.

### Views
{: #views}
Frontend. 

### Layouts
{: #layouts}
De overordnet layout. Eks. Sider der har en sidebar (source list for macOS).

### Pages
{: #pages}
Siders indhold. De nedarver fra layouts.

### Resources
{: #resources}
Alle resourcer som farver, fonts etc.

### Use cases (Application logic)
Her samles uses cases. En use case kunne f.eks være Create product.
Her vil alt logikken være for de aktioner en bruger kan fortage (Gem p/sletteroduktet, eks.).
En klasse vil blive oprettet: ProductUseCase.
Og den vil så have diverese metoder, såsom createProduct, getAllProducts osv.

### Interfaces
Vil stå for interaktionen mellem vores logik og eksterne kilder.
Det vil betyde at når vi eks. skal tilknytte en API, DB vil det gå igennem en database.
Ligeledes vil UI også gå igennem denne i form af en ViewModel.

#### Ressourcer
https://books.google.dk/books/about/Clean_Architecture.html?id=uGE1DwAAQBAJ&source=kp_book_description&redir_esc=y

## VIPER

### Delmål
<ul>
    <li>Overordnet forståelse</li>
    <li>Forstå hvert lag</li>
</ul>

<i>View, Interactor, Presenter, Enity, Router</i>
VIPER kaldes Clean Architecture for IOS apps, og er derfor kraftigt inspireret af Clean Architecture<br/>
Fordele ved VIPER<br/>
<ul>
    <li>Seperations of Concerns.</li>
    <li>Testing</li>
    <li>Loose Coupling</li>    
</ul>

### View
Håndterer UI elementer (Layouts, widgets etc)<br/>
Fungerer som frontend - Dette er hvad bruger ser og inteagerer med.<br/>
Reference til Presenter<br/>

### Interactor
Indkapsler (encapsulates) Business Logic Layer.<br/>
Her er Business Logic og use cases<br/>
Intagerer med repos, databaser, API og får dataen<br/>
Reference til Presenter. Presenter bestemmer hvad der skal gøres med dataen.<br/>
Den fortæller presenter, hvornår den er klar

### Presenter
Mellemleddet mellem View og Interactor<br/>
Håndterer brugernes interaktioner. <br/>
Formaterer eller manipulerer dataen, så den passer til views, samt opdaterer views<br/>
Reference til Presenter, Router og View

### Entity
Datamodeller.<br/>
Classes, Structures eller protocols.

### Router
Håndterer navigationen mellem screens.
Entry point.

##### Ressourcer
<b>Architecture</b>https://www.linkedin.com/learning/ios-app-development-design-patterns-for-mobile-architecture<br/>
<b>VIPER:</b> https://www.objc.io/issues/13-architecture/viper/<br/>
<b>VIPER:</b>https://medium.com/@sandeepkella23/i-have-explained-what-is-viper-architecture-in-below-everything-briefly-81a6105da6ed<br/>
<b>VIPER:</b>https://www.youtube.com/watch?v=hFLdbWEE3_Y&t=411s<br/>
<b>Folder Structure</b>https://medium.com/mop-developers/build-your-first-swiftui-app-part-2-project-architecture-c6e3e62c6457<br/>