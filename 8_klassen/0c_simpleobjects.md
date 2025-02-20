# Een eenvoudige klasse

We zullen nu enkele basisconcepten van klassen en objecten toelichten aan de hand van praktische voorbeelden.

## Object methoden

Stel dat we een klasse willen maken die ons toelaat om objecten te maken die verschillende mensen voorstellen. We willen aan iedere mens kunnen vragen waar deze woont en die zal dat dan op het scherm tonen.

We maken een nieuwe klasse ``Mens`` en maken een methode ``Praat`` die iets op het scherm zet:

```csharp
class Mens
{
    public void Praat()
    {
        Console.WriteLine("Ik ben een mens!");
    }
}
```

We zien twee nieuwe aspecten:

* Het keyword **``static``** komt bij een klasse niet aan te pas (of toch minder zoals we [later zullen zien](/10_advancedklassen/5_static.md))
* Voor de methode plaatsen we ``public`` : dit leggen we zo meteen uit

Je kan nu elders objecten aanmaken en ieder object z'n methode ``Praat`` aanroepen:

```csharp
Mens joske = new Mens();
Mens alfons = new Mens();

joske.Praat();
alfons.Praat();
```

Er zal 2x ``Ik ben een mens!`` op het scherm verschijnen. Waarbij telkens ieder object (``joske`` en ``alfons``) zelf verantwoordelijk ervoor waren dat dit gebeurde.

## Public en private access modifiers

De **access modifier** geeft aan hoe zichtbaar een bepaalde deel van de klasse is. Wanneer je niet wilt dat "van buitenuit" (bv objecten vna je klasse in de Main) een bepaalde methode kan aangeroepen worden, dan dien je deze als ``private`` in te stellen. Wil je dit net wel dat moet je er expliciet ``public`` voor zetten.

Test in de voorgaande klasse eens wat gebeurt wanneer je ``public`` verwijderd voor de methode. Inderdaad, je zal de methode ``Praat`` niet meer op de objecten kunnen aanroepen.

De reden: **wanneer je voor een methode (of klasse) niet expliciet ``public`` zet dan wordt deze methode als ``private`` beschouwd.**

Test volgende klasse eens, kan je de methode ``VertelGeheim`` vanuit de Main op ``joske`` aanroepen?

```csharp
class Mens
{
    public void Praat()
    {
        Console.WriteLine("Ik ben een mens!");
    }

    void VertelGeheim()
    {
        Console.WriteLine("Mijn geheim is dat ik leef!");
    }
}
```

Zoals aangehaald hoef je ``private`` niet expliciet te schrijven, maar het is wel een goede gewoonte. Volgende twee manieren zijn dus identiek:

```csharp
 VertelGeheim() {....}  //private impliciet
 private  VertelGeheim() {....} //private expliciet
```

### Reden van private

Waarom zou je bepaalde zaken ``private`` maken? 

Stel dat we in de klasse extra (hulp)methoden willen gebruiken die enkel intern nodig zijn, dan doen we dit. Volgende voorbeeld toont hoe we in de methode ``Praat`` de private methode ``VertelGeheim`` gebruiken:


```csharp
class Mens
{
    public void Praat()
    {
        Console.WriteLine("Ik ben een mens!");
        VertelGeheim();
    }

    void VertelGeheim()
    {
        Console.WriteLine("Mijn geheim is dat ik leef!");
    }
}
```

Als we nu elders een object laten praten als volgt:

```csharp
Mens rachid = new Mens();
rachid.Praat();
```

Dan zal de uitvoer worden:

```text
Ik ben een mens!
Mijn geheim is dat ik leef!
```

# Interne variabelen

We maken onze klasse wat groter, we willen dat een object een leeftijd heeft die we kunnen verhogen via een methode ``VerjaardagVieren`` (we hebben de methode ``VertelGeheim`` even weggelaten):

```csharp
class Mens
{
    private int leeftijd = 1;

    public void VerjaardagVieren()
    {
        Console.WriteLine("Hiphip hoera voor mezelf!");
        leeftijd++;
        Praat();
    }

    public void Praat()
    {
        Console.WriteLine("Ik ben een mens! ");
        Console.WriteLine($"Ik ben {leeftijd} jaar oud");

    }

}
```

Hier zien we een pak details de onze aandacht vereisen:

* Ook variabelen zoals ``int leeftijd`` mogen een access modifier krijgen in een klasse. Ook hier, als je niet expliciet ``public`` zet wordt deze als ``private`` beschouwd
* Ook al is ``leeftijd`` ``private`` alle methoden in de klasse kunnen hier aan. Het is enkel langs buiten dat bijvoorbeeld volgende code niet zal werken ``rachid.leeftijd = 34`;``
* We kunnen iedere variabele een beginwaarde geven.
* **Ieder object zal z'n eigen leeftijd hebben**

Die laatste opmerking is een kernconcept van OOP: ieder object heeft z'n eigen interne staat die kan aangepast worden individueel van de andere objecten van hetzelfde type.

We zullen dit testen in volgende voorbeeld waarin we 2 objecten maken en enkel 1 ervan laten verjaren. Kijk wat er gebeurt:

```csharp
Mens Elvis = new Mens();
Mens Bono = new Mens();

Elvis.VerjaardagVieren();
Elvis.VerjaardagVieren();
Evlis.VerjaardagVieren();
Bono.VerjaardagVieren();
```

Als je deze code zou uitvoeren zal je zien dat de leeftijd van Elvis verhoogt en niet die van Bono wanneer we ``VerjaardagVieren`` aanroepen. Zoals het hoort!