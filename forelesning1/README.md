
# _PG5600_ iOS programmering
## Forelesning 1

---

### Hans Magnus Inderberg
#### _@hinderberg_

### Mads Mobæk
#### _@madsmobaek_

---

# Agenda

* Praktisk informasjon
* Kort intro til til OSX
* iOS økosystem
* XCode
* Swift

---

# Praktisk informasjon

* Ikke lenger Objective-C, men Swift
* Utgår: Objective-C Programming: The Big Nerd Ranch Guide
* Inngår: The Swift Programming Language (fra iBooks)
* Deleksamen og innlevering

---

# Kort intro til til OSX

Todo

---

# iOS økosystem

Todo

---

# XCode

Todo

---

---

# Swift

![](wwdc.png)

^ Under utviklerkonferansen WWDC i starten av Juni, lanserte Apple ganske så uventet et nytt programmeringsspråk kalt Swift.

---

![](swift-logo-hero.jpg)

^ kalt Swift.

^Et nytt programmeringsspråk for iOS og OS X

---

## Som førte til reaksjoner som dette

![fit inline](tweet-trash.png)

---

## og dette

![100% inline](tweet-mattt.png)

---

#### _Som igjen førte til_

## Introduksjon til Swift

---

# Hva er Swift?
* _Et programmeringsspråk for iOS og OSX laget av Apple_
* _De har fjernet C avhengigheten og Swift tar over for Objective-C_
* _Fokus på Enkelhet og sikkerhet_
* _Moderne og kraftig_
* _Fungerer side-om-side med C og Objetice-C_
* _Paradigmer som imperativ, OOP og funksjonelt_  

^ Swift er laget av Apple og tar i bruk mange kjente paradigmer og  som vi kjenner fra andre språk.
De sier at språket har fokus på sikkerhet og det merkes ved at kompileren er
flink til å finne utvikler feil og at de tvinger utviklere til å bruke visse patterns når de utvikler.
Enkelheten kommer frem i den lette syntaxen, de har for eksempel fjernet semi-kolon.
Mye inspirasjon kan man si at har blitt hentet fra språk som .NET familien, spesielt
F#, Java, Lisp, JavaScript, Diverse funksjonelle språk.

---

# Hvordan ser det ut?

---

```swift
			   println("Hei hei BEKK")
```

---

# Konstanter og Variabler

```swift
let shortName: String = "BEKK"


var numberOfemployees: Int = 320
numberOfemployees = 500
```

^ Konstanter deklareres med LET og variabler med VAR
En konstant kan bare bli satt en gang, men det må ikke skje ved kompilering.
I Swift er det foretrukket å bruke konstanter og imutable verdier, med mindre noe skal endre seg
Dette vil blant annet gjøre det enklere i multi-treding og enklere for kompileren.

---

# Type inference
```swift
var numberOfemployees = 350
numberOfemployees = 500


let shortName = "BEKK"
```

^Type interence er et stort fokus punkt i Swift.
Det betyr med andre ord at du skjelden trenger å spesifisere typen. Men typen vil fortsatt vœre der.

^De analyserer både oppover og nedover i type-treet.
Det vil si at om du ikke spesifiserer typen, så vil det analysere output av det du setter variabelen din til for å finne typen.

^Men om du setter typen, så vi den typen overskrive den faktiske typen.
For eksempel hvis du setter en Double til å vœre Float.

^Verdier vil aldri automatisk skifte type, så om du skal legge sammen er string og int, så må du eksplisitt konvertere en av dem.

---

# Strenger

```swift
let subject = "iOS programmering"
println("\(countElements(subject)) tegn")
```

* TODO: compare

---

# Unicode støtte

```swift



                   let 🌍 = "😩😛😵😘"
```

^Jada, du kan bruke emoticons

---

# String interpolation

```swift
let n1 = 10, n2 = 8
let mathString = "\(n1) ganger \(n2) er \(n1 * n2)"
//10 ganger 8 er 80
```

^Strenger kan kombineres ved hjelp av streng interpolation. Der man også kan skrive matematiske utrykk.
^Det er også laget broer mellom Objective-C sine NSString klasse og Swift String, noe som gjør at man kan benytte disse om hverandre.

---

# Numbers

* TODO

---

# Tuples

* TODO: skriv om til å være uten funksjoner

```swift


func refreshWebPage() -> (Int, String) {
  return (200, "success")
}

let (statusCode, message) = refreshWebPage()
println("Fikk status \(statusCode): \(message)")
```

---

```swift

// Navngi felter i tuple returverdi

func refreshWebPage() -> (code: Int, message: String) {
  return (200, "success")
}

let status = refreshWebPage()
println("Fikk status \(status.code): \(status.message)")
```

---

# Optionals

---

```swift
var possibleWelcomeMessage: String? = "Halloo"

if possibleWelcomeMessage == nil {
    println("Det er ingen streng her!")
} else {
    // unwrapping med !
    let welcomeMessage = possibleWelcomeMessage!
    println(welcomeMessage)
}
```

^Greit å vite at typer som ikke er optinal kan ikke vœre nil.
Da får man kompile error

---

```swift
if let welcomeMessage = possibleWelcomeMessage {
        println(welcomeMessage)
}
```

^Automatisk unwrapping og sette verdien i en if

---

# Collection types

_Det finnes to typer collections i Swift_

<br />

* _Arrays_
* _Dictionaries_


^ De vanlige typene finnes også i Swift

---

# Array

```swift
// Deklaring
let jobs = [String]()

// merk ingen spesifisering av type
var jobs = ["Systemutvikler", "Prosjektleder", "Frontend-Utvikler"]

// Uthenting
jobs[0]
```

^ Et array deklareres på veldig standard måte, med to klammer. Uthenting er som vanlig.
Forskjellig fra objective-c er at type inference gjør at disse er typed arrays

---

```swift
// Modifisering

jobs.append("Rådgiver")
jobs += ["Rådgiver", "Backend-Utvikler"]
jobs[0] = "Backend-Utvikler"
jobs[2..<5] = ["Rådgiver", "Backend-Utvikler", "Prosjektleder"]
```

---

# Dictionary

```swift
// Deklaring
let emptyDictionary = [String: Float]()
var jobs = ["Rådgiver" : 35, "Systemutvikler" : 21, "Prosjektleder" : 32]

// Uthenting
jobs["Systemutvikler"]

// Modifisering
people["Rådgiver"] = 45
people["Prosjektleder"] = 81
```

^ I dicionary så holdes ting på normalt nivå og mange av dere kjenner nok igjen dette fra andre språk.

---

# Løkker

_Det finnes fire typer løkker_

* _while_
* _do-while_
* _for_
* _for-in_

^ Ikke noe nytt her altså, og de gjøres på vanlig måte

---

# Ranges

```swift


for nr in 1...10 {
	println("\(nr) ganger 2 er \(nr*2)")
}

for nr in 1..<10 {
	println("\(nr) ganger 2 er \(nr*2)")
}

```

^_1…10 – Går fra 1 til 10. Og er kjent som en closed range._
 _1..<10 – Går fra 1 til 9. Og er kjent som en half-closed range_

---

# Control flow
<br />

* _if_
* _switch_

---

# if

* _Ikke noe nytt, paranteser er valgfritt_

```swift
if age <= 10 {
    println("Barn")
} else if age >= 80 {
    println("Gammel")
} else {
    println("I mellom en plass?;)")
}
```

---

# switch

_Her har de gått banans_ ;-)

* _Du trenger ikke bruke break etter hver case_
* _Bruk hvilke som helst object i en switch_
* _Hvis du utelater default case må switch'ene matche alle case, hvis ikke blir det_ compile error

---

```swift
switch age {
case 1,2,3,4,5,6,7,8,9,10:
    println("Du er et barn!")
case 80...100:
    println("Du er gammal!")
default:
    println("I mellom en plass?;)")
}
```

---

# Du kan switche på instanser

``` swift
switch sender {
  case childButton:
    println("Du er et barn!")
  case oldisButton:
    println("Du er gammal!")
  default:
    println("I mellom en plass?;)")
}
```

^ Man kan også switche på instanser av forskjellige typer.

---

# Enums

```swift
enum Level {
	case Consultant
	case Senior
	case Manager
}

// eller
enum Level {
	case Consultant, Senior, Manager
}

```

---

# Enums Raw og Associated verdier

```swift
// Enumeration Raw Values
enum ASCIIControlCharacter: Character {
    case Tab = "\t"
    case LineFeed = "\n"
    case CarriageReturn = "\r"
}

// Enumeration Associated Values
enum Barcode {
    case UPCA(Int, Int, Int, Int)
    case QRCode(String)
}
var productBarcode = Barcode.UPCA(8, 85909, 51226, 3)
productBarcode = .QRCode("ABCDEFGHIJKLMNOP")
```

^Kan ha konstruktører, funksjoner, variabler

---

# Playground

* _Ligner på Scala Workspaces or F# interactive mode_
* _Kjører kode forløpende_
* _Test ut nye algoritme, tester, utforsk apier, rett en bestemt bug_

---

# Playground Demo

---

# REPL

###### _read–eval–print loop støtte_
###### _Startes med ```xcrun swift```_

---

# For å kjøre Swift i terminalen
## må man sette nyeste xcode med
## _`xcode-select`_

_xcode-select -s /Applications/Xcode6-Beta6.app/Contents/Developerents/Developer_

---

# Oppgaver

Se [Øvingsoppgavene](oppgaver1.md)
