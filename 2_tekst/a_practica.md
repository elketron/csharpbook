# Enkele opmerkingen vooraf

1. Bekijk volgende kennisclip waarin wordt uitgelegd hoe je meerdere projecten in 1 solution in VS kunt plaatsen:
![](../assets/infoclip.png)
[Meerdere projecten in 1 solution](https://ap.cloud.panopto.eu/Panopto/Pages/Viewer.aspx?id=f2c322cd-7607-4624-b0cd-a969006f8b2a)

**Probeer vanaf nu per hoofdstuk 1 solution aan te maken met daarin meerdere projecten (1 project per oefening)**
2. Sommige oefeningen zullen soms [PRO] in de titel hebben. Dit zijn pittigere oefeningen. Probeer ze zeker, maar laat je niet ontmoedigen als ze niet direct lukken. Het kan erg nuttig zijn om enkele weken later nog eens terug naar oudere hoofdstukken te gaan zien of er nog PRO-oefeningen zijn die je ondertussen wel mogelijks kan oplossen. [PRO²] oefeningen zijn nog iets pittiger (of bevatten zaken die niet bij de leerstof horen).

# ASCII Art

Genereer je naam in ASCII Art met een van de vele online generators. Plaats deze aan de start van een van je bestaande programma's zodat nu je naam wordt getoond wanneer het programma start, gevolgd door de rest.

# String interpolation

Kies 2 oefeningen uit het vorige hoofdstuk waarin je output op het scherm moest geven. Pas string interpolatie m.b.v. ``$`` (manier 2) toe in deze 2 oefeningen.

> Volgende 2 oefeningen zijn al iets stevigers. Iedere oefening eindigt met een [PRO] gedeelte dat je best enkel doet als je een uitdaging wenst.

# ASCII Art & Colors

Gebruik je kennis van het verschil tussen `Console.Write`  en `Console.WriteLine`, alsook de werking van kleuren in console-applicaties, om je ASCII-art naam van de eerdere oefening nu van kleur te voorzien. Zorg ervoor dat minstens 1 letter in een andere kleur is.

# Systeem informatie

## Deel 1

Maak een applicatie die de belangrijkste computer-informatie (geheugen, etc) aan de gebruiker toont.

Deze computer-informatie kan je verkrijgen mbv de Environment-klasse. Hier enkele voorbeelden (kijk zelf of er nog nuttige properties over je computer in staan):

```csharp
bool is64bit = Environment.Is64BitOperatingSystem;
string pcname = Environment.MachineName;
int proccount = Environment.ProcessorCount;
string username = Environment.UserName;
long memory = Environment.WorkingSet; //zal ongeveer 10 Mb teruggeven.
```

> **WorkingSet** geeft terug hoeveel geheugen het programma van windows toegewezen krijgt. Als je dus op 'run' klikt om je code te runnen dan zal dit programma geheugen krijgen en via WorkingSet kan het programma dus zelf zien hoeveel het krijgt. (Wat een vreemde lange zin.)

Zoals je ziet wordt het geheugen in bytes teruggegeven. Zorg ervoor dat het geheugen steeds in mega of gigabytes op het scherm wordt getoond.

**Formateer de informatie met behulp van de $-notatie  zodat deze  deftig getoond worden en de gebruiker snel de belangrijke informatie over z'n systeem te zien krijgt.**

## [PRO] Deel 2

Ook informatie over de harde schijven kan je verkrijgen (in bits). 
Dit vereist wel dat je bovenaan je programma volgende lijn bijschrijft: ``using System.IO``. 

Vervolgens kan je in je programma schrijven:

```csharp
long cdriveinbytes = DriveInfo.GetDrives()[0].AvailableFreeSpace;  
long totalsize = DriveInfo.GetDrives()[0].TotalSize;  
```

 De lijn met ``using`` is om aan te geven dat we iets uit de ``System.IO`` bibliotheek nodig hebben, namelijk ``DriveInfo``.
Schrijven we dat niet dan moeten we in onze code DriveInfo aanroepen met z'n volledige path: ``System.IO.DriveInfo....``

De 0 tussen rechte haakjes is de index van welke schijf je informatie wenst. 0 is de eerste harde schijf, 1 de tweede, enzovoort. (Ter info: dit zijn arrays, zie later)

Vraag aan de gebruiker het nummer van de harde schijf waar meer informatie over moet getoond worden. 

Opgelet: sta toe dat de gebruiker 1 voor de eerste harde schijf mag gebruiken, 2 voor de tweede, enzovoort. Je zal dus in code nog manueel 1 moeten aftrekken van de invoer van de gebruiken.
Bv:

```csharp
int invoer= Convert.ToInt32(Console.ReadLine()) - 1 ;
long totalsize = DriveInfo.GetDrives()[invoer].TotalSize;  
 ```

# Weerstandberekenaar

Stel dat je in het labo een weerstand vastneemt en je kent de kleurcodes van de streepjes wel, maar niet hoe je die kunt omzetten naar de effectieve weerstandswaarde. In dit programma kunnen we de gebruiker helpen.

![](../assets/1_csharpbasics/colors.jpg)

(Bron afbeelding: [https://www.esdsite.nl](https://www.esdsite.nl))

## Deel 1

Maak een programma dat de weerstandwaarde berekent gebaseerd op:

* Ring 1: die de tientallen voorstelt
* Ring 2: die de eenheden voorstel
* [ENKEL VOOR PRO] Ring 3: die de exponent (10 tot de macht) voorstelt. (tip:``Math.Pow(10,ring3``))

Gebruik twee variabelen van het type ``int`` waar je getal van 0 tot 9 telkens aan kan toewijzen. (we veronderstellen dus dat de gebruiker de kleurcode heeft omgezet naar een getal en dat toewijst aan de variabele)

Test dat je "formule/berekening" klopt om gebaseerd op 2 (of 3) ringen de weerstandswaarde te berekenen. 

## Deel 2

Plaats het geheel in een mooie UNICODE/Ascii-tabel

Hier enkele nuttige tekens:

```
╔═══════════════╦═══════════════╗
║ 
╟───────────────╫───────────────╢
║ 
╚═══════════════╩═══════════════╝
```

Gebruik $-string interpolatie om de informatie in de tabel te tonen zodat je volgende uitvoer kunt genereren:
![](../assets/1_csharpbasics/tabel.png)

of:

![](../assets/1_csharpbasics/tabel2.png)

## [PRO²] Deel 3

Kan je afhankelijk van de ringwaarde het getal in de tabel in de juiste kleur zetten conform de weerstandskleuren (tip: je zal ``Write`` en ``if`` moeten leren gebruiken)

# [PRO] Shell-starter
Je kan de output van een ``Process.Start()`` programma naar je console scherm sturen. Dit vereist wat meer code. Volgend voorbeeld zal de output van het commando ``ipconfig /all`` op het scherm tonen:

```csharp
System.Diagnostics.Process process = new System.Diagnostics.Process();
process.StartInfo.FileName = "ipconfig";
process.StartInfo.Arguments = "/all"; 
process.StartInfo.UseShellExecute = false;
process.StartInfo.RedirectStandardOutput = true;
process.StartInfo.RedirectStandardError = true;
process.Start(); //start process

// Read the output (or the error)
string output = process.StandardOutput.ReadToEnd(); //normal output
Console.WriteLine(output);
string err = process.StandardError.ReadToEnd(); //error output (if any)
Console.WriteLine(err);
process.WaitForExit();
//Continue
Console.WriteLine("Klaar");
```

> Let er op dat dit voorbeeld niet perfect werkt met een shell-commando dat even duurt. Denk bijvoorbeeld aan ``ping``. De output komt namelijk pas op het scherm als het commando is afgelopen. Test zelf maar eens!

Maak enkele kleine C# programma's die bepaalde shell-commando's zullen uitvoeren, eventueel na input van de gebruiker.
Enkele nuttige shell-commando's in de netwerk-sfeer zijn bijvoorbeeld:

```text
hostname

arp -a

getmac

nslookup google.com

netstat
```

Andere toffe commando's kunnen zijn:

```text
chrome.exe ap.be
notepad mytest.txt
```

Of de naam van een bestand dat je wilt openen, maar dan met het hele path:

```text
c:\Temp\mydocument.docx
```
