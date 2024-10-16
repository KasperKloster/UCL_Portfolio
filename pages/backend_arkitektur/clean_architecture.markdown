---
layout: page
title: Clean Architecture
permalink: /clean_architecture/
---
# Clean Architecture

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