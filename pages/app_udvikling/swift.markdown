---
layout: page
title: Swift
permalink: /swift/
---
# Swift

## Delmål
<p>Delmål i forhold til hvad jeg på nuværende tidspunkt tænker jeg skal vide, for at komme i mål med projektet.
Disse delmål har syntax, så vi kan skrive kode<br/>
Frontend så bruger kan interagere med applikationen<br/>
En database til at hente og indsætte data<br/>
En API til at kommunikere med eksterne services.<br/>
</p>
<ul>
    <li><a href="#syntax">Blive komfortabel med syntax</a></li>    
    <li><a href="#classes_structs_protocols">Klasser, Structs og Protocols</a></li>
    <li><a href="#ui">SwiftUI vs UIKit (Programmatic UI)</a></li>            
    <li><a href="#navigation_state">Navigation, States og User</a></li>
    <li><a href="#database">Database</a></li>            
    <li><a href="#api">Connect til API (GET, POST, PUT, DELETE)</a></li>
    <li><a href="#testing">Testing</a></li>
    <li><a href="#best_practices">Best practices</a></li>
</ul>

## Syntax
{: #syntax}
Swift syntaksen er lært mest igennem ved bare at prøve sig af<br/>
Når vi allerede har en grundlæggende programmeringsviden, er det ikke svært at sætte sig ind i et nyt sprog.<br/>
Derudover har Xcode en ret god auto-complete, samt en indbygget dokumentation, der er gjort meget brug af.<br/>
Hertil har jeg også brugt Swift dokumentation til at slå op i<br/>
Jeg er mest af alt blevet komfortabel med syntax og Xcode igennem at bygge projektet.

### Klasser, Structs og Protocols
{: #classes_structs_protocols}
Et par ting hvor jeg så at Swift har adskilt sig fra andre sprog er classes, structs og protocols samt guards:<br/>
Det skal dog nævnes at f.eks protocols er samme som interface i C# - Apple har bare valgt at kalde det noget andet.

<b>Classes</b><br/>
Classes er reference types<br/>
Det betyder at hvis vi instantiere et objekt, og referer en anden variabel til samme objekt:
var myCar = Car(color: "Grey")<br/>
var mySecondCar = myCar<br/>
Ændrer vi så værdien for color på mySecondCar: mySecondCar.color = "Blue"<br/>
Så vil det også ændre farven på myCar, fordi de referer til det samme i hukommelsen.<br/>
Det kunne også være Google Sheet, der deles med andre - Når en laver en ændring, er det ændret for alle.<br/>
<br/>
Classes kan nedarves (Subclasses)

<b>Struct</b><br/>
Structs er value type.<br/>
Igen hvis vi instantiere et objekt, og referer en anden variabel til samme objekt:
var myCar = Car(color: "Grey")<br/>
var mySecondCar = myCar<br/>
mySecondCar.color = "Blue"<br/>
Er der her lavet en kopi. Når vi ændrer farven, bliver kun mySecondCar påvirket.
<br/>
Structs kan ikke nedarves. Vi kan bruges protocols, så vi kan dele behaviour.
Det har fordelen at vi ikke nedarver en masse funktioner, vi ikke skal bruge (Bloat)<br/>
Det gør at de er mere lightweight og har bedre performance.<br/>

<b>Protocols</b><br/>
Protocoller er et blueprint, om hvilke metoder og properties en klasse eller struct skal implementere.<br/>
Der kan derfor ikke oprettes en instans af en protocol.<br/>
Lig med interfaces i C#.<br/>

<b>Guard</b><br/>
Guards Er statements ligesom IF statements.<br/>
Guards er en tand kortere og lettere at læse. Vi kan sætte en variabel, hvis statements er True, hvis det er False eksvikerer koden inde i kroppen.<br/>

I projektet har jeg gjort brug af guards, når jeg henter fra databasen.<br/>
<code>
guard let data = document.data() else {
    print("No data found in document.")    
}
</code>
Her er der sagt: Giv mig data i variablen data, er den False, så print beskeden, ellers forstær og gem variblen.

#### Swift Ressourcer
<ul>
    <li><a href="https://docs.swift.org/swift-book/documentation/the-swift-programming-language/" target="_blank"><b>Swift:</b> https://docs.swift.org/swift-book/documentation/the-swift-programming-language/</a></li>
    <li><a href="https://developer.apple.com/design/human-interface-guidelines/designing-for-macos" target="_blank"><b>Swift:</b> https://developer.apple.com/design/human-interface-guidelines/designing-for-macos</a></li>
    <li><a href="https://developer.apple.com/videos/play/wwdc2022/110353/" target="_blank"><b>Swift Protocols:</b> https://developer.apple.com/videos/play/wwdc2022/110353/</a></li>
    <li><a href="https://www.programiz.com/swift-programming/guard-statement" target="_blank"><b>Guard: </b> https://www.programiz.com/swift-programming/guard-statement</a></li>
</ul>
## UI
{: #ui }
Frontend delen til IOS App<br/>
Jeg har undersøgt hvilke muligheder der er for at bygge UI - SwiftUI, Storyboards, UIKit<br/>
Der er lavet et par hurtige projekter (eksperimenter), hvor jeg har prøvet de forskellige af.<br/>
Jeg fandt flere fordele og ulemper ved alle tre.<br/>
Jeg er dog endt med at fokuserer på SwiftUI - Apple er kommet med mange updates til dette sprog, og det virker til at de vil have det som deres primære sprog i fremtiden<br/>
Dertil synes jeg også at ens kode var langt mere overskuelig at kigge på med SwiftUI.<br/>

#### UI Ressourcer
<ul>
    <li><a href="https://developer.apple.com/tutorials/swiftui" target="_blank"><b>SwiftUI:</b> https://developer.apple.com/tutorials/swiftui</a></li>
    <li><a href="https://developer.apple.com/documentation/appkit/"><b>AppKit</b> https://developer.apple.com/documentation/appkit/</a></li>
    <li><a href="https://www.youtube.com/watch?v=_U6_l58Cv4E"><b>UIKit</b> https://www.youtube.com/watch?v=_U6_l58Cv4E</a></li>
</ul>

## Navigation og State
{: #navigation_state }
Navigation i IOS skulle jeg lige vende mig til at vride min hjerne omkring.<br/>
Da jeg har været mest vant til at kode Web (PHP), skulle jeg ind i et nyt koncept - State.<br/>
<b>State</b> hvilket "stadie" din app er i, i modsætning til webudvikling, så vil appen ikke refreshe, når bruger inteagerer med programmet - Vi har ingen browser til at refreshe siden.<br/>
<b>Navigationen</b> bruger jeg b.la i menuen:
<code>
NavigationSplitView {
    List{        
        Section("Products", isExpanded: $isProductsExpanded){
            NavigationLink("Products", destination: ProductRouter.createModule())
        }
    }
}
</code>
Her har vi en struct: <code>NavigationSplitView</code>, der indeholder en list med et <code>NavigationLink</code> - En struct der giver os muligheden for et link, destination er hvor linket skal gå hen. I dette tilfælde er det klassen <code>ProductRouter</code> til metoden <code>createModule</code>
<br/>
<b>State</b><br/>
I et view har vi:<br/>
<code>
struct CreateIntegrationView: View {
    @ObservedObject var presenter: CreateIntegrationPresenter    
    @State private var selectedPlatform: Platform? = nil
    ...
    Picker("Choose platform", selection: $selectedPlatform) {        
        Text("Select platform").tag(nil as Platform?)        
        ForEach(presenter.platforms) { platform in
            Text(platform.name).tag(platform as Platform?)
        }
    }
    ...
    Button(action: {    
    presenter.createIntegration(
        ...
    platform: selectedPlatform)
    ...
    .onAppear {
        Task{
            do {
                await presenter.loadPlatforms()
            } 
        }
    }
</code>
Her holder vi øje med Presenter (se backend arkitektur / VIPER) igennnem property wrapper @ObservedObject - Vi observerer denne klasse<br/>
<code>@State private var selectedPlatform: Platform? = nil</code> fortæller koden hvilket stadie vi er i. Default er propertien <code>nil</code><br/>
<code>Button action...</code> hvad skal der ske, når bruger klikker på en knap - Her sender vi til en metode i presenter.<br>
<code>.onAppear</code> når siden indlæses - Her vil vi have en async task i en metode i presenter.
Hopper vi i presenter:<br/>
<code>
class CreateIntegrationPresenter : CreateIntegrationPresenterProtocol, ObservableObject {
    ...    
    @Published var platforms : [Platform] = []
    ...

</code>
Vi nedarver først og fremmest fra ObservableObject, der gør at vi kan observere ændringer i vores view.<br/>
De ændringer der så skal ske sker igennem property @Published, ObservedObject lytter efter hvornår der er indlæst (published).<br/>
Det er altså koden, der bliver kørt 
<code>
await presenter.loadPlatforms()
</code>
og 
<code>
ForEach(presenter.platforms) { platform in
</code>
Nu kan bruger vælge en platform, hvad de har valgt holder vi øje med ved <code>@State private var selectedPlatform: Platform? = nil</code>
og vi kan sende det valg videre med knappen.

#### Navigation ressourcer
<ul>
<li>
    <b>SwiftUI : NavigationStack</b><a href="https://youtu.be/oxp8Qqwr4AY?si=YAQFnf2fFt-oDhLg<" target="_blank">https://youtu.be/oxp8Qqwr4AY?si=YAQFnf2fFt-oDhLg</a>
</li>

<li>
    <b>Swift Navigation</b><a href="https://developer.apple.com/documentation/swiftui/migrating-to-new-navigation-types<" target="_blank">https://developer.apple.com/documentation/swiftui/migrating-to-new-navigation-types
    </a>
</li>
</ul>

## Database
{: #database}

## API
{: #api}

## Testing
{: #testing}