# Klassen en objecten aanmaken in CS

In C# kunnen we geen objecten aanmaken voor we een klasse hebben gedefinieerd dat de algemene eigenschappen (properties) en werking (methoden) beschrijft.

## Klasse maken

Een klasse heeft de volgende vorm:

```csharp
[optionele access modifier] class className
{

}
```

Volgende code de klasse auto in C#

```csharp
class Auto
{

}
```

Binnen het codeblock dat bij deze klasse hoort zullen we verderop dan de werking via properties en methoden beschrijven.

De optionele access modifier komen we later op terug.

### Klassen in Visual Studio

Je kan "eender waar" een klasse aanmaken, maar het is een goede gewoonte om per klasse een apart bestand te gebruiken:

* In de solution explorer, rechterklik op je project
* Kies Add
* Kies Class..
* Geef een goede naam voor je klasse

**De naam van je klasse moet voldoen aan de identifier regels die ook gelden voor het aanmaken van variabelen!**

![Klasse toevoegen in VS](../assets/6_klassen/klassadd.png)

## Objecten aanmaken

Je kan nu objecten aanmaken van de klasse die je hebt gedefinieerd.
Je doet dit door eerst een variabele te definiëren en vervolgens een object te **instantiëren** met behulp van het ``new`` keyword:

```csharp
Auto mijnEerste = new Auto();
Auto mijnAndereAuto = new Auto();
```

We hebben nu **twee objecten aangemaakt van het type Auto**.

Let goed op dat je dus op de juiste plekken dit alles doen (bekijk de onderstaande screenshot):

* Klassen maak je aan als aparte files in je project
* Objecten creëer je in je code op de plekken dat je deze nodig hebt, bijvoorbeeld in je ``Main`` methode bij een Console-applicatie

![basics oop same in vv](../assets/6_klassen/allessamen.png)

> Je hebt dus in het verleden ook al objecten aangemaakt. Telkens je met Random werkt deed je dit al. Dit wil zeggen dat er dus in .NET ergens reeds een voorgeprogrammeerde klasse ``Random`` bestaat met de interne werking.