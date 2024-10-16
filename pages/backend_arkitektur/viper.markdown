---
layout: page
title: VIPER
permalink: /viper/
---

# VIPER

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
Er bindeleddet mellem forbindelsen af view, presenter og interactor<br/>
Dette gøres igennem createModule()<br/>
Vi kalder den funktion igennem vores navigation: NavigationLink("Products", destination: ProductRouter.createModule())<br/>
Der sikrer vi at alt er forbundet, inden vi viser view.
<br/><br/>
Håndterer derudover også navigationen mellem screens.<br/>

### En gennemgang af flowet

Navigation: Når bruger klikker på linken: NavigationLink("Products", destination: ProductRouter.createModule())<br/>
Bliver der navigeret til ProductRouter.createModule(), der returner et view.<br/>
<br/><br/>
Routeren har ansvaret for at samle alle lagende (view, interactor og presenter). <br/>
Presenter og interactor bliver instatieret. <br/>
presenter interactor property bliver sat (Så presenter kan hente data)<br/>
view bliver initaliseret med presenter property og bliver returneret<br/>
Til sidst returneres view:<br/>
`class ProductRouter {    
    static func createModule() -> some View {
        let presenter = ProductPresenter()
        let interactor = ProductInteractor()
        presenter.interactor = interactor
        let view = ProductView(presenter: presenter)
        return view
    }    
}`
<br/><br/>
Når viewet bliver vist:<br/>
Har vi en property af typen ProductPresenter. <br/>
Den har en property wrapper: @ObservedObject, der gør at den kan observere ændringer og automatisk opdatere viewet.<br/>
I view har vi functionen .onAppear (Hvad skal der ske, når skærmen er indlæst).<br/>
i .onAppear kalder vi presenter.loadProducts(), der henter data fra interaktoren<br/>
<br/><br/>
Kigger vi ind på presenter klassen nedarver vi ObservableObject - Det gør at vi kan udsende ændringer der bliver observeret af view (@ObservedObject)<br/>
Presenter har en property til interactor (Vi har referet den i router).<br/>
Vi har endnu en property wrapper @Published, der bliver opdateret, når vores data er indlæst.<br/>
Til sidst er der en function, der indlæser dataen fra interactoren. Den data bliver sendt tilbage til presenter, og til view, og vores data bliver vist.<br/>
Igennem @ObservedObject og @Published er der data-bindet. En forbindelse der gør at view automatisk bliver opdateret<br/>



##### Ressourcer
<b>Architecture</b>https://www.linkedin.com/learning/ios-app-development-design-patterns-for-mobile-architecture<br/>
<b>VIPER:</b> https://www.objc.io/issues/13-architecture/viper/<br/>
<b>VIPER:</b>https://medium.com/@sandeepkella23/i-have-explained-what-is-viper-architecture-in-below-everything-briefly-81a6105da6ed<br/>
<b>VIPER:</b>https://www.youtube.com/watch?v=hFLdbWEE3_Y&t=411s<br/>
<b>Folder Structure</b>https://medium.com/mop-developers/build-your-first-swiftui-app-part-2-project-architecture-c6e3e62c6457<br/>