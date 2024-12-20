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
    <li>Læs CSV</li>
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
En applikation kan hurtigt blive kedelig, hvis vi intet data kan håndtere. Derfor ville jeg have en database.<br/>
Jeg undersøgte først hvilke muligheder vi har, når vi snakker om IOS.<br/>
Kunne vi bruge MySQL, MongoDB, SQLlite eller andet?<br/>
Jeg kiggede først ind på Apples egne anbefaling: SwiftData<br/>
SwiftData har en masse fede features, især i ens models.<br/>
Den har bare det store problem, at det kun virker til IOS og er derfor ikke særligt velegnet til cross platform og skalerbarhed<br/>
Medmindre jeg vil risikere at håndtere to databaser, derfor kiggede jeg på alternativer og har samtidig længe tænkt på at lære Firestore<br/>
Derfor endte valget på Firestore.<br/>
Firestore er NoSQL database som Google har lavet.<br/>
Den er især god til at håndtere store mængde af dataer og har en god dokumentation med gode eksempler.<br/>
NoSQL betyder at vi ikke laver relationship på samme måde, som det gøres med SQL, i stedet kan vi refere til andre dokumenter.<br/>
Firestore er bygget op med:
<ul>
    <li><b>Collections:</b> Det samme som en tabel i SQL</li>
    <li><b>Documents:</b> En enitity i en collections</li>
    <li><b>Fields:</b> Hvilke felter et document har</li>
</ul>

I Appen er der brugt Firestore flere steder, her er et eksempel:<br/>
I Interactor (Se Viper / Backend Arkitektur), håndterer vi database kald:<br/>
<code>
    func fetchPlatformName(platformRef : String) async throws -> String {
        try await platformManager.getPlatformName(platformRef: platformRef);
    }
</code>
Her sender vi et Async call til platformManager og vil have platform name. Vi har sendt en reference med, som egenligt bare er document navnet, samet ID'et på platform document<br/>
platformManager ligger i mappen Network/Services/Platform<br/>
<code>
    // Fetch the platform name from the Firestore reference
    func getPlatformName(platformRef : String) async throws -> String
    {
        var name : String = ""
        do {
            let platformDocument = try await Firestore.firestore().document(platformRef).getDocument()
            // Check if the document exists and extract the "name" field
            if let documentData = platformDocument.data() {
                name = documentData["name"] as? String ?? "Unknown Name"
            }            
        } catch{
            print("Could not get platform name \(error.localizedDescription)")
        }
        return name
    }
</code>
Her har vi metoden, der henter navnet, den vigtigste linje er:<br/>
<code>
let platformDocument = try await Firestore.firestore().document(platformRef).getDocument()
</code>
Her går vi såmændt bare ind og henter det dokument fra referencen. Har vi fået det, kører vi:
<code>
if let documentData = platformDocument.data() {
    name = documentData["name"] as? String ?? "Unknown Name"
}   
</code>
Hvor vi sætter det navn vi returnerer udefra feltet i documentData, og vi sætter en else statement, hvis ikke det eksisterer<br/><br/>
I starten kæmpede jeg meget med at få Firstore til at virke. Jeg kunne slet ikke få kontakt, kun en heftigt fejlkode.<br/>
Jeg googlede rundt, men kunne ikke finde særligt mange med samme problem, og dem der havde løst det,for år siden havde ikke skrevet svaret<br/>
Jeg har brugt timer, og med timer mener jeg dage, på at få hul igennem.
Opsætningen var ret enkelt, men forbindelsen fra App til Firestore gad den bare ikke...
Jeg fik en fejl at det var min internet forbindelse eller at firewall blokerede firestore.googleapis.com<br/>
Efter at havde prøvet forskellige forbindelser, kunne jeg udelukke den grund.
Jeg debuggede, omskrev koden, research... Alt. Intet virkede.
<br/>
Jeg opsatte en hurtig side i Javascript, og der fungerede forbindelsen. - Documents blev vist.<br/>
I Xcode rodede jeg rundt i diverse indstillinger og der fandt jeg to manglende flueben ved Incomming og Outgoing connections
"Tjek, Tjek" og der var hul igennem!<br/>
Derfra har det kørt ganske fejlfrit og lynhurtigt.

<ul>
    <li><b>SwiftData; </b><a href="https://developer.apple.com/xcode/swiftdata/" target="_blank">https://developer.apple.com/xcode/swiftdata/</a></li>
    <li><b>Add Data: </b><a href="https://firebase.google.com/docs/firestore/manage-data/add-data" target="_blank">https://firebase.google.com/docs/firestore/manage-data/add-data</a></li>
</ul>

## API
{: #api} 
Igennem begge projekter har der været behov for at blive tilkoblet en ekstern API.<br/>
Begge projekter har gjort brug af Shopify's GraphQL API.<br/> 
Da jeg har mindre erfaring med GraphQL, i forhold til REST, så jeg her muligheden for at få at fingrene i GraphQL to gange.
<br/><br/> 
I første omgang skulle jeg finde ud af hvordan Swift overhovedet tilknytter en API.<br/> 
Jeg oprettede et nyt Xcode projekt (eksperiment), så jeg kunne teste requests og responses igennem konsolen og ikke skulle compile et projekt, hver gang.
<br/>
Igennem en tutorial fandt jeg metoden på hvordan jeg kunne få hul igennem, blandet med min forvejen viden omkring at jeg vidste at der skulle en særlig Http Header sendt med ens request, endte min metode med at se således ud: <br/>
<code>    
    private func createRequest() -> URLRequest {
        var request = URLRequest(url: baseURL)
        request.httpMethod = "POST"
        request.addValue("\(accessToken)", forHTTPHeaderField: "X-Shopify-Access-Token")
        request.addValue("application/json", forHTTPHeaderField: "Content-Type")
        return request
    }
</code>
<br/>
Nu havde jeg en metode, og et setup der kan håndteres alle requests, hvis jeg bare kalder en særligt query, så GraphQL ved hvad der skal hentes tilbage.
Derefter hvordan dette response skal håndteres:
<br/><br/>
<code>
    func getProducts() async throws {
        var request = createRequest()
        
        // Define the GraphQL query
        let query = """
        {
            products(first: 10) {
                edges {
                    node {
                        id
                        title
                        description
                    }
                }
            }
        }
        """
</code>
Dernæst var jeg i tvivl om, hvad der skal sendes tilbage til Interactor i forhold til Viper<br/>
Skulle det være en JSON eller datatypen (I dette tilfælde Products)<br/>
Jeg har ikke kunne finde noget material på dette, men efter at have tænkt over det, synes jeg det giver mest mening at returnere en liste med Products<br/>
Dette er grundet et Interactor blot skal hente dataen.. Hvis jeg returenede JSON, skulle det være op til Presenter at konvertere JSON om til Products.<br/>
Dette synes jeg er et forvirrende ekstra step - Når jeg vil have Products i sidste ende, ser jeg ingen grund til at returene JSON.
<br/>
Hvis jeg på et senere tidspunkt skal ændre Products, vil det være op til Presenter at ændre disse.<br/>
Interactor skal returne så tæt på "rå" data som muligt.
<br/>
Herfra var det "blot" at Serialize JSON, og få det til en liste af Products.<br/>
<br/>
Det tog mig lang tid at fatte at hvert key, skulle ses som et objekt, hvis jeg skulle returne det som Product.<br/>
Jeg troede først jeg bare kunne skrive products.metafields.edges<br/>
Men efter kun at have set løsninger, hvor hvert key blev til en objekt og det samtidig ikke var muligt for mig at iterere igennem, tænker jeg at det er måden at gøre det på.<br/>
Der er derfor oprettet en særligt entity ShopifyProducts<br/>
Disse ShopifyProducts, kan jeg så loope igennem og instatiere dem som Products:
<br/><br/>

<code>
        do {
            var products : [Product] = []
            // Response to string / Debugging purposes
            // let jsonResponse = try JSONSerialization.jsonObject(with: data, options: []);
            // print(jsonResponse);
            
            // Decode the data into the structured response model
            let decodedResponse = try JSONDecoder().decode(ShopifyProductResponse.self, from: data)
            let productResponse = decodedResponse.data.products.edges.map { $0.node }
            
            for product in productResponse {
                // Get properties from base/main product
                let title : String = product.title
                let description : String = product.description
                // Initialize product from each variant (We can get the SKU for each product)
                for variant in product.variants.edges {
                    let sku : String = variant.node.sku
                    let product = Product(sku: sku, name: title, description: description)
                    // Append to all prodcuts
                    products.append(product);
                }
            }
            
            return products;
            
            
        } catch {
            print("Failed to decode Shopify Product JSON: \(error)");
            throw error;
        }
</code>

<ul>
    <li><b>Swift API Calls: </b><a href="https://www.youtube.com/watch?v=ERr0GXqILgc" target="_blank">https://www.youtube.com/watch?v=ERr0GXqILgc</a></li>
    <li><b>Coding keys: </b><a href="https://developer.apple.com/documentation/foundation/archives_and_serialization/encoding_and_decoding_custom_types" target="_blank">https://developer.apple.com/documentation/foundation/archives_and_serialization/encoding_and_decoding_custom_types</a></li>
</ul>


## Testing
{: #testing}
XCTest vs Swift Testing