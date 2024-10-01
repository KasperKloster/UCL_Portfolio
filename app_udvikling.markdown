---
layout: page
title: App Udvikling
permalink: /app_udvikling/
---
# App Udvikling

## Læringsmål

### Xcode
<ul>
    <li>Basic navigation</li>
</ul>

### SwiftUI
#### Delmål
<ul>
    <li>Views</li>
    <li>Layout</li>
    <li>Style</li>
</ul>

### UIKit
#### Delmål
<ul>
    <li>Views</li>
    <li>Layout</li>
    <li>Style</li>    
</ul>


## Swift
#### Delmål
<p>Delmål i forhold til hvad jeg på nuværende tidspunkt tænker jeg skal vide, for at komme i mål med projektet</p>
<ul>
    <li>Blive komfortabel med syntax</li>    
    <li><a href="#classes_structs_protocols">Klasser, Structs og Protocols</a></li>
    <li>SwiftUI vs UIKit (Programmatic UI)</li>    
    <li>Functions</li>
    <li>Navigation</li>
    <li>User input</li>
    <li>Encapsulation</li>
    <li>Upload .csv</li>
    <li>Connect til API</li>
    <li>Core Data</li>
    <li><a href="#best_practices">Best practices</a></li>
</ul>

## Klasser, Structs og Protocols
{: #classes_structs_protocols}

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
Meget lig interfaces i C#.<br/>

## Best Practices
{: #best_practices}

<b>Folder names:</b> Skrevet i CamelCase<br/>
<b>Structures:</b> CamelCase. Ental. Har samme "funktion" som klasser. Men mere simple<br/>
<b>Variables:</b> lowercase</br>

### API
#### Delmål
<ul>
    <li>Opret forbindelse</li>
    <li>Create</li>
    <li>Read</li>
    <li>Update</li>
    <li>Delete</li>
</ul>

### UnitTest
#### Delmål
<ul>
    <li>Lær hvordan testing sker via. Swift</li>
    <li>Opsæt test</li>
</ul>

#### Ressourcer
<b>Swift:</b>https://docs.swift.org/swift-book/documentation/the-swift-programming-language/<br/>
<b>Swift Protocols:</b>https://developer.apple.com/videos/play/wwdc2022/110353/<br/>
<b>SwiftUI:</b>https://developer.apple.com/tutorials/swiftui<br/>
<b>AppKit</b>https://developer.apple.com/documentation/appkit/<br/>
<b>UIKit</b>https://www.youtube.com/watch?v=_U6_l58Cv4E<br/>
<b>Swift:</b>https://developer.apple.com/design/human-interface-guidelines/designing-for-macos<br/>

#### Notes
Class: NSWindowController. Administrer loading og display af window. Luk det, størrelse og andet til Vinduet som vi ikke vi bekymre os om.