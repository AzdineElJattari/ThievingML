<p align="center"><img alt="header-image" src="https://user-images.githubusercontent.com/56048370/100483716-28d5f580-30fa-11eb-887e-fc7a82af392c.png" width="100"/></p>
<h1 align="center">ThievingML</h1>
<p align="center">:robot: Dit is een eenvoudig tutorial die u zal doen kennismaken met de wereld van Machine Learning :robot:</p>
<br>
  
<table align="center"><tr><td align="center" width="9999">

**<img alt="header-image" align="center" width="2.5%" height="2.5%" src="https://user-images.githubusercontent.com/56048370/100546885-05c75500-3264-11eb-8440-c62c613ce2b1.jpg"/> [Panopto](https://www.youtube.com/channel/UCGW01S5Ri2RMa-qqXtO9Tzw?view_as=subscriber) 
• <img alt="header-image" align="center" src="https://user-images.githubusercontent.com/56048370/100491240-533ba900-3122-11eb-815b-3beabde80e62.png"/> [Rapporteer bug](https://github.com/AzdineElJattari/ThievingML/issues) 
• <img alt="header-image" align="center" src="https://user-images.githubusercontent.com/56048370/100491250-66e70f80-3122-11eb-9f76-c2cdd32ddfdc.png"/> [Vraag feature aan](https://github.com/AzdineElJattari/ThievingML/issues)** 

</td></tr></table>

# Inhoud
1. [Introductie ThievingML](#introductie)
2. [Nodige software](#benodigdheden)
3. [Spelverloop](#spelverloop)
4. [Observaties, acties & beloning systeem](#beloning)
5. [Het speelveld](#speelveld)
6. [De spelomgeving](#spelomgeving)
    - [Speelveld object](#speelveldobject)
    - [Dief object](#diefobject)
    - [Reiziger object](#reizigerobject)
    - [Scorebord object](#scorebordobject)
7. [Spelobjecten scripts (C#)](#allescripts)
    - [Environment.cs (omgeving) *code-snippets*](#scripts)
        * [Overzicht methodes van de omgeving](#environment)
        * [Object-variabelen van de omgeving](#environment2)
        * [Initialisatie van de omgeving instantie](#environment3)
        * [Opkuisen van het speelveld](#environment4)
        * [Scorebord](#environment5)
        * [Genereren van een traveller (reiziger)](#environment6)
    - [Traveller.cs (reiziger) *code-snippets*](#scripts2)        
    - [Thief.cs (dief) *code-snippets*](#scripts3)
        * [Overzicht van methodes](#thief)
        * [Object variabelen](#thief2)
        * [Initialiseer de dief](#thief3)
        * [OnEpisodeBegin](#thief4)
        * [Heuristic](#thief5)
        * [OnActionReceived](#thief6)
        * [OnCollisionEnter](#thief7)
        * [DestroyObjects (Optimizations)](#thief8)
8. [Resultaat in Tensorflow na één uur testen](#tensorflow)
    
## :point_right: Introductie ThievingML <a name="introductie"></a>
In deze tutorial zullen we u als opkomende Machine Learning developer stap voor stap begeleiden hoe u doormiddel van *Machine Learning* - *ML Agents* en het gebruik van *Unity3D* en *C#* code een basic project tot stand kan brengen. Ook voor mensen **zonder** programmeer ervaring is het mogelijk om deze tutorial te volgen en succesvol de ThievingML project tot stand te brengen.
<br>
<br>
Let's roll! :wink: 
<br>
<br>
<img alt="header-image" width="60%" height="60%" align="center" src="https://user-images.githubusercontent.com/56048370/100522847-351a8b00-31ac-11eb-8180-03f4f6650e76.png"/>

## :point_right: Nodige software <a name="benodigdheden"></a>
   [C# Visual Studio](https://visualstudio.microsoft.com/downloads/) <img alt="header-image" width="20" height="20" align="center" src="https://user-images.githubusercontent.com/56048370/100491797-deb73900-3126-11eb-8461-f6925356a65c.png"/>
    • [Unity 3D](https://unity3d.com/get-unity/download) <img alt="header-image" width="20" height="20" align="center" src="https://user-images.githubusercontent.com/56048370/100491779-afa0c780-3126-11eb-82ef-5db5ece28fbd.png"/>
    • [Python 3](https://www.python.org/downloads/) <img alt="header-image" width="20" height="20" align="center" src="https://user-images.githubusercontent.com/56048370/100491828-0d351400-3127-11eb-8a45-fb6fe13e9a9d.png"/>
    • [Tensorflow](https://www.tensorflow.org/install/pip) <img alt="header-image" width="20" height="20" align="center" src="https://user-images.githubusercontent.com/56048370/100491704-11acfd00-3126-11eb-89af-1b9d01264ffb.png"/>
    <br><br> *Optioneel:* [Anaconda](https://docs.anaconda.com/anaconda/user-guide/tasks/tensorflow/) <img alt="header-image" width="20" height="20" align="center" src="https://user-images.githubusercontent.com/56048370/100491847-305fc380-3127-11eb-855a-35a78e5a9d91.png"/>

## :point_right: Spelverloop <a name="spelverloop"></a>
Het spelverloop zal in deze hoofdstuk kort schematisch worden voorgesteld. In het spel dat u zal gaan ontwikkelen zullen er 2 objecten zijn met een hoofdrol.
Enerzijds hebben we de **Thief (Dief)** anderzijds hebben we de **Traveller (Reiziger)**. De dief is diegene die doormiddel van *Machine Learning* zal gaan leren om zo snel mogelijk onder knie te krijgen wanneer er een reiziger passeert op zijn pad om vervolgens te gaan springen zodat hij de reiziger dan succesvol kan gaan 'bestelen' en vervolgens zal de Agent **beloont** worden.
<br>
<br>
**Detecteer fase** :point_down:
<br>
<br>
<img alt="header-image" width="60%" height="60%" align="center" src="https://user-images.githubusercontent.com/56048370/100524234-b840de80-31b6-11eb-8689-c0c04e5be2d5.png"/>
<br>
<br>
**Spring fase** :point_down:
<br>
<br>
Wanneer er dus een reiziger zal passeren zal de dief doormiddel van *sensoren* die zitten verwerkt in de ogen gaan omhoog gaan springen om zo succesvol langs achter in de zakken te zitten van de reiziger. Nu vraagt u zich nu af maar wat als de Agent er niet in slaagt om over de reiziger te springen? <br> Dan zal er een **bestraffing** plaats vinden. Ook zal er in het spel een scorebord zichtbaar zijn die u als developer duidelijk zal aantonen wanneer de Agent wordt *beloont | gestraft*. Heel dit process zal zich blijven herhalen. Na verloop van tijd zal u bij het trainen van de Agent ook door hebben dat er niet meer gestraft zal worden en dus de Agent succesvol over de reiziger zal blijven springen.
<br>
<br>
<img alt="header-image" width="60%" height="60%" align="center" src="https://user-images.githubusercontent.com/56048370/100524479-c55ecd00-31b8-11eb-8c17-10c0b4aa21e9.png"/>

## :point_right: Observaties, acties & beloning systeem <a name="beloning"></a>
In onderstaand tabel krijgt u netjes een overzicht te zien hoe de beloningsysteem van ThievingML in elkaar zit. 
<br>
| Observaties      | Acties | Beloning     |
| :---        |    :----:   |          ---: |
| Inkomende traveller      | Springen       | +0.1f   |
| Inkomende traveller   | Geen        | -1f, einde episode      |
| Geen   | Springen        | -0.2f      |

## :point_right: Het speelveld <a name="speelveld"></a>
Laten we beginnen met alle componenten op te bouwen om de simulatie mogelijk te maken. Men kan hiervoor **3D objecten** vanuit **Unity** maken zoals een kubus/cilinder voor de actoren of men kan sites gebruiken zoals [Mixamo](https://www.mixamo.com/#/) Unity assets of [Sketchfab](https://sketchfab.com) om zo characters te downloaden en te importeren in je Unity environment.
<br>
Voor deze tutorial gaan we gebruik maken van **Mixamo**. Kies een character die zal spelen als de Thief en eentje die de traveller moet voorstellen
<br>
<br>
<img alt="header-image" width="60%" height="60%" align="center" src="https://user-images.githubusercontent.com/56048370/100527881-21384e80-31d7-11eb-8776-22a8d130ca62.png"/>
<br>
<br>
Nu moeten we een character gaan importeren. Om dit te doen druk je simpelweg op **download**, vervolgens kies je voor de optie **FBX** uit de dropdown met als titel *Format*.
<br>
<br>
<img alt="header-image" width="60%" height="60%" align="center" src="https://user-images.githubusercontent.com/56048370/100527946-99067900-31d7-11eb-815e-65319c8a84db.png"/>
<br>
<br>
Na het downloaden sleept u de bestanden rechtstreeks in uw *models* folder van uw Unity project.
<br>
<br>
<img alt="header-image" width="40%" height="40%" align="center" src="https://user-images.githubusercontent.com/56048370/100528009-4083ab80-31d8-11eb-9f33-925c4db06548.png"/>
<br>
<br>
Aan het einde van dit tutorial zal u ook te zien krijgen hoe u animations kunt toevoegen voor uw character.

## :point_right: De spelomgeving <a name="spelomgeving"></a>
In dit hoofdstuk zullen we kort elke object overlopen die zal worden gecreëerd in het project.

### ![image info](https://user-images.githubusercontent.com/56048370/100489562-14532680-3115-11eb-9621-04bcf5aca2a7.png) Speelveld object <a name="speelveldobject"></a>
Het speelveld krijgt de naam *Street* en is eenvoudig vlak met de **schaal X = 14 | Y = 0.5 | Z = 1.5** en de **posities** en de **rotatie** op **X = Y = Z = 0** en dit geldt ook voor de **Mesh Collider**. Dit en alle andere objecten zitten vervat in een container object genaamd *Environment*. Dit zal ervoor zorgen dat het geheel later eenvoudig gedupliceerd kan worden.
<br>
<br>
Onderstaande afbeelding toont u de volledige hiërarchie binnen de spelobjecten met hun benaming zoals ze in deze handleiding gebruikt zullen worden. :point_down:
<br>
<br>
<img alt="header-image" width="40%" height="40%" align="center" src="https://user-images.githubusercontent.com/56048370/100528224-9d806100-31da-11eb-845e-6992cf4125a6.png"/>

### ![image info](https://user-images.githubusercontent.com/56048370/100489562-14532680-3115-11eb-9621-04bcf5aca2a7.png) Dief object <a name="diefobject"></a>
In dit hoofdstuk zullen we de asset die u hebt gedownload van **Maximo** en die de rol van 'dief' op zich zal nemen gaan gebruiken en de instellingen geven die nodig zullen zijn zodat de *Dief object* zal kunnen springen & detecteren wanneer er een traveller op zijn pad is.
<br>
<br>
<img alt="header-image" width="25%" height="15%" align="center" src="https://user-images.githubusercontent.com/56048370/100528351-2ba91700-31dc-11eb-82da-b70eaac37118.png"/>
<br>
<br>
Selecteer de Dief object in Unity en voeg volgende componenten eraan toe :point_down:

**Rigidbody**
<br>
<img alt="header-image" width="40%" height="40%" align="center" src="https://user-images.githubusercontent.com/56048370/100528484-a888c080-31dd-11eb-84d2-64276f5f388a.png"/>
<br>
>Zorg ervoor dat de instellingen van de component *Rigibody* helemaal hetzelfde zijn als de afbeelding hierboven.
<br>
<br>

**Box Collider**
<br>
<img alt="header-image" width="40%" height="40%" align="center" src="https://user-images.githubusercontent.com/56048370/100528545-85124580-31de-11eb-8798-ff8249bffbe6.png"/>
<br>

>Zorg ervoor dat de instellingen van de component *Box Collider* helemaal hetzelfde zijn als de afbeelding hierboven.
<br>

> :bell: Nadat u bovenstaande instellingen hebt ingevoerd op beide componenten zal u een groen rechthoek te zien krijgen zoals op de afbeelding hieronder rond de dief object. Deze kunt u vervolgens vergroten of verkleinen door op het vierhoekje te drukken en te slepen. Zorg er wel voor dat de dief object qua formaat ongeveer volledig past in het groene rechthoek.

<br>
<img alt="header-image" width="25%" height="15%" align="center" src="https://user-images.githubusercontent.com/56048370/100528932-80e82700-31e2-11eb-85d6-724951c98007.png"/>
<br> 
De acties die de dief object zal gaan uitvoeren zijn gebaseerd op observaties. Om ervoor te gaan zorgen dat de dief kan gaan observeren maken we gebruiken van **Ray Perception Sensor 3D** component. Voeg het toe met de instellingen vanuit onderstaande afbeelding. :point_down:
<br>
<br>
<img alt="header-image" width="40%" height="40%" align="center" src="https://user-images.githubusercontent.com/56048370/100529081-e557b600-31e3-11eb-83bc-cb860244bae9.png"/>
<br>

Zorg ervoor dat zoals op onderstaande foto de **Ray Perception** ter hoogste staat van waar de ogen van de dief object staan. Voeg ook bij de *Detectable tags* de gedownloade **Reiziger object** toe. Dit zal ervoor zorgen dat de sensor de reiziger kan detecteren.
<br>
<br>
<img alt="header-image" width="60%" height="60%" align="center" src="https://user-images.githubusercontent.com/56048370/100529232-8c891d00-31e5-11eb-8a4c-5308bc8eda53.png"/>
<br>
<br>
Voeg een *Behavior parameters* toe met de naam **Thief** :point_down:
<br>
<br>
<img alt="header-image" width="60%" height="60%" align="center" src="https://user-images.githubusercontent.com/56048370/100529260-f30e3b00-31e5-11eb-8135-85ea9b9567f2.png"/>
<br>
<br>
Voeg een *Decision requester* toe (dit is een automatische trigger om de agent te dwingen iets te gaan doen) :point_down:
<br>
<br>
<img alt="header-image" width="60%" height="60%" align="center" src="https://user-images.githubusercontent.com/56048370/100529321-952e2300-31e6-11eb-8599-c602966b058e.png"/>

### ![image info](https://user-images.githubusercontent.com/56048370/100489562-14532680-3115-11eb-9621-04bcf5aca2a7.png) Reiziger object <a name="reizigerobject"></a>
We gaan ervan uit dat u ook een **Traveller (reiziger) 3D object** hebt gedownload van [Mixamo](https://www.mixamo.com/#/). Eens u het correct hebt gedownload en hebt geïmporteerd in Unity gaan we meteen ook voor dit 3D object een *Rigidbody* & *Box Collider* creëren.
<br>
<br>
<img alt="header-image" width="60%" height="60%" align="center" src="https://user-images.githubusercontent.com/56048370/100529463-5731fe80-31e8-11eb-9a6b-d26cf8d50d37.png"/>
<br>
<br>
Selecteer de Reiziger object in Unity en voeg volgende componenten eraan toe :point_down:

**Rigidbody**
<br>
<img alt="header-image" width="40%" height="40%" align="center" src="https://user-images.githubusercontent.com/56048370/100529596-56e63300-31e9-11eb-9234-415f6da029e4.png"/>
<br>
>Zorg ervoor dat de instellingen van de component *Rigibody* helemaal hetzelfde zijn als de afbeelding hierboven.
<br>

**Box Collider**
<br>
<img alt="header-image" width="40%" height="40%" align="center" src="https://user-images.githubusercontent.com/56048370/100529609-8a28c200-31e9-11eb-888e-c2ef0df6682a.png"/>
<br>
<br>
<img alt="header-image" width="40%" height="40%" align="center" src="https://user-images.githubusercontent.com/56048370/100529671-2c48aa00-31ea-11eb-8c0e-2e029a180e60.png"/>
> Een Box Collider zal ervoor zorgen wanneer er een collision is, u binnen uw script gebruik er gebruik van kan maken.

Ten slotte zullen we voor dit 3D object ook nog een tag geven genaamd **Traveller** via de Unity GUI zoals op onderstaande afbeelding :point_down:
<br>
<img alt="header-image" width="40%" height="40%" align="center" src="https://user-images.githubusercontent.com/56048370/100529738-cf99bf00-31ea-11eb-9eb0-aa4e6bba5767.png"/>

### ![image info](https://user-images.githubusercontent.com/56048370/100489562-14532680-3115-11eb-9621-04bcf5aca2a7.png) Scorebord object <a name="scorebordobject"></a>
Dit 3D object met naam **ScoreBord** is een instantie van de **TextMeshPro** klasse. Dit 3D object zal de *Cumulative reward* (Gecumuleerde beloning) bevatten en weergeven.
<br>
<br>
<img alt="header-image" width="40%" height="40%" align="center" src="https://user-images.githubusercontent.com/56048370/100529815-61093100-31eb-11eb-909b-29b675c3fdfb.png"/>

## :point_right: Het gedrag van de Agent en de andere spelobjecten <a name="gedrag"></a>
In dit hoofdstuk zullen we overlopen wat het gedrag zal zijn en wat de uitgevoerde handelingen zullen zijn van *alle* 3D objecten in dit project. Dit zal bestaan uit code snippets vanuit **C#** met wat uitleg erbij. 

## :point_right: Spelobjecten scripts (C#) <a name="allescripts"></a>
Hieronder zullen we stapsgewijs per 3D object bekijken wat er moet staan in de script bestanden om ze een bepaald *gedrag* te geven en bepaalde *handelingen* te kunnen laten uitvoeren bij bepaalde *omstandigheden*.

### ![image info](https://user-images.githubusercontent.com/56048370/100490290-a4479f00-311a-11eb-839d-3ef719df2eb7.png) Environment.cs <a name="scripts"></a>
In het *Environment.cs* script bestand staat er code in om de **Traveller (Reiziger) / Thief (Dief)** te doen spawnen op het platform. Al deze handelingen zullen bij het runnen van het project automatisch worden uitgevoerd door Unity.

![image info](https://user-images.githubusercontent.com/56048370/100489836-2b931380-3117-11eb-98ea-59fd67012cb0.png) **Overzicht methodes van de omgeving** <a name="environment"></a>
<br>
Maak een nieuw folder aan in de project folder genaamd *Scripts*. Hierin zullen alle script bestanden staan die we gaan creëren en zullen gebruiken op het juiste 3D object. De eerste script bestandje die we zullen maken krijgt de naam *Environment*. In de ``Environment Class`` zullen we volgende methodes gaan aanmaken.

- ``InvokeRepeating`` -> Is een functie die ervoor zal zorgen dat de ``SpawnTravellers()`` methode op een bepaald tijdstip terug zal worden aangeroepen.

- ``ClearEnvironment`` -> Deze methode zal dienen voor het opkuisen van eventuele 3D objecten van een vorig episode.

- ``SpawnTravellers`` -> Deze methode zal ervoor zorgen dat de Traveller zal worden gespawnt op het platform.

![image info](https://user-images.githubusercontent.com/56048370/100489836-2b931380-3117-11eb-98ea-59fd67012cb0.png) **Object-variabelen van de omgeving** <a name="environment2"></a>
<br>
We zullen een aantal *Public* object-variabelen gaan creëren.

```csharp
public Traveller travellerPrefab;

private Thief thief;

private TextMeshPro scoreBoard;

private GameObject travellers;

public float spawnTime;

public float delayInBetween;
```
De variabel ``travellerPrefab`` zal **manueel** door de ontwikkelaar (developer) moeten gekoppeld worden via de Unity GUI. 
De twee variabele ``spawnTime`` en ``delayInBetween`` worden in de methode ``InvokeRepeating()`` gezet om zo te kunnen bepalen om de hoeveel keer een traveller gespawnd zal doen worden.

De rest van de variabelen zijn ``private`` en zullen ervoor zorgen dat de simulatie-omgeving een referentie heeft naar de agent, de variabelen ``scoreBoard`` en ``travellers`` zullen ook een referentie krijgen naar de simulatie-omgeving.

![image info](https://user-images.githubusercontent.com/56048370/100489836-2b931380-3117-11eb-98ea-59fd67012cb0.png) **Initialisatie van de omgeving instantie** <a name="environment3"></a>
<br>
Tijdens de initialisatie zullen bovenstaande referenties worden ingevuld door de volgende methode. :point_down:

```csharp
  public void OnEnable()
  {
      travellers = transform.Find("Travellers").gameObject;
      scoreBoard = transform.GetComponentInChildren<TextMeshPro>();
      thief = transform.GetComponentInChildren<Thief>();        
  }
```
Merk hierbij wel op dat de ``Find()`` methode en ``GetComponentInChildren()`` methode op de ``transform`` van ``Environment`` ervoor moeten zorgen dat uitsluitend child-objecten worden teruggegeven. Dit is belangrijk omdat we later de hele simulatie-omgeving gaan dupliceren binnen dezelfde scene in Unity. Andere methoden zoas ``GameObject.FindGameObjectWithTag`` zouden dus mogelijk de verkeerde referenties doorgeven, i.e. referenties naar objecten van een ander simulatie-omgeving, zonder hiervoor een foutmelding te geven.

![image info](https://user-images.githubusercontent.com/56048370/100489836-2b931380-3117-11eb-98ea-59fd67012cb0.png) **Opkuisen van het veld** <a name="environment4"></a>
<br>
Bij het begin van elke episode zal het veld opnieuw in zijn beginsituatie terecht komen alvorens er nieuwe travellers worden gegenereerd.

```csharp
public void ClearEnvironment()
{
    travellers = transform.Find("Travellers").gameObject;
    foreach (Transform traveller in travellers.transform)
    {
       GameObject.Destroy(traveller.gameObject);
       travellers = transform.Find("Travellers").gameObject;
       foreach (Transform traveller in travellers.transform)
       {
          GameObject.Destroy(traveller.gameObject);
       }
    }
}
```

![image info](https://user-images.githubusercontent.com/56048370/100489836-2b931380-3117-11eb-98ea-59fd67012cb0.png) **Scorebord** <a name="environment5"></a>
<br>
Het scorebord moet continu de **belonging** (=score) gaan weergeven. Dit zal gebeuren door eenvoudigweg gebruik te gaan maken van de *getter* van de methode ``GetCumulativeReward()`` vanuit de ``Agent class``.

```csharp
private void FixedUpdate()
{
        scoreBoard.text = thief.GetCumulativeReward().ToString("f2");
}
```

![image info](https://user-images.githubusercontent.com/56048370/100489836-2b931380-3117-11eb-98ea-59fd67012cb0.png) **Genereren van een traveller** <a name="environment6"></a>
<br>
Voor dit gedeelte zal u een 3D object moeten aanmaken zoals op onderstaande afbeelding en deze dan moeten plaatsen op het plek waar u wil dat de traveller opnieuw zal moeten spawnen op het **platform (scene)**. Als is hierin bent geslaagd dan zal onderstaand stukje code ervoor zorgen om de traveller te doen spawnen op het plek van de 3D object die u zojuist hebt aangemaakt.

```csharp
GameObject newTraveller = Instantiate(travellerPrefab.gameObject);
```
<br>
<img alt="header-image" width="70%" height="70%" align="center" src="https://user-images.githubusercontent.com/56048370/100548917-1ed60300-3270-11eb-9c61-fa4ad02ce79c.png"/>
<br>

Onderstaande lijn code zal een traveller aanmaken en vervolgens zal deze dan door ``setParent()`` methode een traveller binnen de lege ``Travellers`` worden gezet.

```csharp
newTraveller.transform.SetParent(travellers.transform);
```
<br>
<img alt="header-image" width="40%" height="40%" align="center" src="https://user-images.githubusercontent.com/56048370/100549008-b3406580-3270-11eb-8827-5668fb55b1c3.png"/>
<br>

Vervolgens zullen de rotatie en de positie ook hetzelfde zijn als die van de travellers.

```csharp
newTraveller.transform.localPosition = travellers.transform.localPosition;
newTraveller.transform.localRotation = travellers.transform.localRotation;
```
<br>
<img alt="header-image" width="25%" height="15%" align="center" src="https://user-images.githubusercontent.com/56048370/100549166-922c4480-3271-11eb-80ac-689038196906.png"/>
:arrow_up_small:
:arrow_down_small:
<br>
<img alt="header-image" width="50%" height="50%" align="center" src="https://user-images.githubusercontent.com/56048370/100549168-93f60800-3271-11eb-8fe7-2cd2cbb0af6a.png"/>

Onderstaande methode genaamd ``SpawnTravellers()`` zal ervoor gaan zorgen dat binnen een bepaalde gekozen duratie een traveller wordt gespawnt.

```csharp
public void SpawnTravellers()
{
    GameObject newTraveller = Instantiate(travellerPrefab.gameObject);
    newTraveller.transform.SetParent(travellers.transform);
    newTraveller.transform.localPosition = travellers.transform.localPosition;
    newTraveller.transform.localRotation = travellers.transform.localRotation;
}
```

Binnen de ``Start()`` methode gaan we nu de volgende lijn code schrijven.

```csharp
void Start()
{
    InvokeRepeating("SpawnTravellers", SpawnTime, delayInBetween);
}
```
En nu kunnen we het ``Environment`` script gaan koppelen met de *Traveller* zoals op onderstaande afbeelding.
<br>
<br>
<img alt="header-image" width="50%" height="50%" align="center" src="https://user-images.githubusercontent.com/56048370/100549525-a8d39b00-3273-11eb-8ce7-6251eaf618ef.png"/>
<br>
### ![image info](https://user-images.githubusercontent.com/56048370/100490290-a4479f00-311a-11eb-839d-3ef719df2eb7.png) Traveller.cs <a name="scripts2"></a>
In dit script zal de snelheid worden bepaald van een *traveller*. Doormiddel van onderstaande velden kan men het **minimum** en **maximum** snelheid bepalen van de traveller.

```csharp
[SerializeField] private float minSpeed;
[SerializeField] private float maxSpeed;
```

Vervolgens hebben we de **Rigidbody** variabele nodig van de traveller om zo een bepaalde snelheid erop te zetten. Het is ook belangrijk om een random te zetten tussen de **minimum** en **maximum** zodat we het niet te simpel maken voor de traveller.

```csharp
private Rigidbody Rigidbody;
```
```csharp
private void Awake()
{
    Rigidbody = GetComponent<Rigidbody>();
}
```
```csharp
private void FixedUpdate()
{
    Rigidbody.velocity = Vector3.back * Random.Range(minSpeed,maxSpeed);
}
```

### ![image info](https://user-images.githubusercontent.com/56048370/100490290-a4479f00-311a-11eb-839d-3ef719df2eb7.png) Thief.cs <a name="scripts3"></a>
In het Thief.cs script bestand zal alle actie plaatsvinden. Want in dit script bestand zullen we van ons Thief (Dief) 3D object een **Agent** maken door de ``Thief class`` te laten overerven van de ``Agent class`` binnenin C#.

```csharp
public class Thief : Agent
{
}
```

![image info](https://user-images.githubusercontent.com/56048370/100490645-1c16c900-311d-11eb-9ebb-79a9f7bfa543.png) **Overzicht van methodes** <a name="thief"></a>
<br>
Deze class zal in totaal 6 methoden gaan bevatten.

- ``Initialize`` -> Zal zorgen voor een eenmalige initialisatie van de Agent.

- ``OnEpisodeBegin`` -> De initialisatie bij de aanvang van een episode.

- ``Heuristic`` -> Indien er geen NN gekoppeld is, dan zorgt deze methode voor een alternatieve manier voor het bepalen van de acties die de agent zal moeten uitvoeren. Dit kan bijvoorbeeld gebeuren via toetsaanslagen (KEYUP/KEYDOWN).

- ``OnActionReceived`` -> De wijzigingen die het spelobject van de eagent moet ondergaan wanneer de speler via ``Heuristic`` of het ``NN`` voorstelt om een bepaalde actie uit te voeren.

- ``OnTriggerEnter`` -> Deze functie word uitgevoerd wanneer er wordt gedetecteerd dat 2 3D objecten met elkaar **botsen** (in aanraking komen).

- ``Jump`` -> Deze methode zal ervoor zorgen dat de **Thief (Dief) 3D object** zal springen over de **traveller** die op zijn pad terecht komt.


![image info](https://user-images.githubusercontent.com/56048370/100490645-1c16c900-311d-11eb-9ebb-79a9f7bfa543.png) **Object variabelen** <a name="thief2"></a>

```csharp
[SerializeField] private float jumpForce;
[SerializeField] private KeyCode jumpKey;
private Vector3 startingPosition;
private bool jumpIsReady = true;
private bool stoleMoney = false;
private bool firstCollision = true;
private Rigidbody body;
private Environment environment;
```
De ``jumpForce`` variabele zal bepalen hoe hoog of hoe krachtig de jump van de thief (dief) 3D object zal zijn. De ``jumpKey`` geeft de speler de keuze om een bepaalde key toe te voegen voor te jumpen bv. doormiddel van de *spatiebalk*.
De ``startingPosition`` zal ervoor gaan zorgen dat de startpositie van de thief (dief) 3D object wordt weergegeven. 

De ``jumpIsReady`` variabele is een boolean die **True** zal teruggeven als resultaat als de thief (dief) 3D object niet in de lucht is en **False** teruggeven als de thief (dief) object wel in de lucht is. De ``stoleMoney`` variabele is nodig om te zien of de thief (dief) 3D object succesvol over de traveller (reiziger) is gesprongen *"reiziger succesvol bestolen"*. En ten slotte hebben we de ``rigidBody`` en ``environment`` variabelen aangemaakt om bepaalde methodes aan te roepen.

![image info](https://user-images.githubusercontent.com/56048370/100490645-1c16c900-311d-11eb-9ebb-79a9f7bfa543.png) **Initialiseer de dief** <a name="thief3"></a>
<br>
De eenmalige initialisatie van de **Thief (Dief) Agent** moet eruit zien als onderstaande code snippet.

```csharp
public override void Initialize()
{
   body = GetComponent<Rigidbody>();
   environment = GetComponentInParent<Environment>();
   startingPosition = transform.position;
}
```

![image info](https://user-images.githubusercontent.com/56048370/100490645-1c16c900-311d-11eb-9ebb-79a9f7bfa543.png) **OnEpisodeBegin** <a name="thief4"></a>
<br>
Bij aanvang van elke episode, zal de **Thief (Dief) Agent** opnieuw gepositioneerd moeten worden. Alle travellers die ervoor nog overgebleven zijn zullen dan verwijderd worden.

```csharp
public override void OnEpisodeBegin()
{
   jumpIsReady = true;
   transform.position = startingPosition;
   body.velocity = Vector3.zero;
 
   environment.ClearEnvironment();
}
```

![image info](https://user-images.githubusercontent.com/56048370/100490645-1c16c900-311d-11eb-9ebb-79a9f7bfa543.png) **Heuristic** <a name="thief5"></a>
<br>
Deze methode zal helpen om de correcte werking en beloning van de Thief (Dief) Agent te testen zodat, terwijl het in de simulatie zit andere acties kan uitvoeren.

```csharp
public override void Heuristic(float[] actionsOut)
{
    actionsOut[0] = 0;
    if (Input.GetKey(jumpKey))
    {
       actionsOut[0] = 1;
    }
}
```
In dit geval kan je de Thief (Dief) Agent manueel besturen met de zelf ingestelde ``jumpKey`` toets.
<br>
<br>
<img alt="header-image" width="40%" height="40%" align="center" src="https://user-images.githubusercontent.com/56048370/100550687-e4726300-327b-11eb-8fdf-c8cacf703273.png"/>
<br>

![image info](https://user-images.githubusercontent.com/56048370/100490645-1c16c900-311d-11eb-9ebb-79a9f7bfa543.png) **OnActionReceived** <a name="thief6"></a>
<br>
Deze methode zal zodanig functioneren dat het zal zorgen voor de vertaling van een voorgestelde actie naar bewegingen of andere wijzigingen van het 3D object van de Agent. Acties worden als een getallenreeks gecodeerd en dusdanig doorgegeven vanuit het ``NN`` of via de *Heuristic-methode*. Voor de Thief (Dief) Agent is er gekozen om discrete acties te ontvangen (t.o.v. continue waardes).

```csharp
private void Jump()
{
     if (jumpIsReady)
     {
         body.AddForce(new Vector3(0, jumpForce, 0), ForceMode.VelocityChange);
         jumpIsReady = false;
     }
}
```

```csharp
public override void OnActionReceived(float[] vectorAction)
{
    if (Mathf.FloorToInt(vectorAction[0]) == 1) // 0 = Stilstand / 1 = Springen
    {
       Jump();
    }      
}
```
Deze code snippet zal ervoor zorgen dat de Thief (Dief) Agent zal gaan springen als ``jumpIsReady`` *True* is, dit dient om ervoor te zorgen dat de Thief (Dief) Agent alleen kan gaan springen als hij op *Street* -> *Op de grond* is. 

Omdat 0 de standaardwaarde is van vectorAction[], is het beter om deze te behouden voor 'het niets doen' van de Agent. Het definiëren van de structuur van ``vectorAction`` gebeurt in de ``Behavior Parameters`` component zoals in onderstaande afbeelding.
<br>
<br>
<img alt="header-image" width="40%" height="40%" align="center" src="https://user-images.githubusercontent.com/56048370/100550957-fd7c1380-327d-11eb-8dea-e1a7d3d80d9c.png"/>
<br>

![image info](https://user-images.githubusercontent.com/56048370/100490645-1c16c900-311d-11eb-9ebb-79a9f7bfa543.png) **OnCollisionEnter** <a name="thief7"></a>
<br>
Deze code snippet zal ervoor zorgen dat er eerst wordt gekeken of er collision is met de ``Street`` object en of dit zijn eerste is van de episode. Dit zal dienen om ervoor te gaan zorgen dat hij geen punten verliest bij de initiële landing "Er zal nog toont worden dat de Thief (Dief) Agent zal afgestraft worden als hij zinloos springt". De ``CompareTag()`` methode wordt gebruikt om de identiteit van het object te achterhalen waarmee de Thief (Dief) Agent in botsing treedt.

```csharp
 private void OnCollisionEnter(Collision collision)
{
    if(collision.gameObject.CompareTag("Street") && firstCollision)
    {
        jumpIsReady = true;
        firstCollision = false;
    }
}
```

Botst de Thief (Dief) Agent op de ``Street`` en heeft hij geen geld gestolen van een Traveller (Reiziger), dan moeten we hem afstraffen om zo de Thief (Dief) Agent aan te leren om alleen te gaan springen als het nodig is.

```csharp
else if (collision.gameObject.CompareTag("Street") && !stoleMoney) 
{ 
     AddReward(-0.2f);
     jumpIsReady = true;
}
```

Botst de Thief (Dief) Agent op de ``Street`` en heeft hij wel succesvol geld gestolen van de Traveller (Reiziger), dan zet je ``jumpIsReady`` op **True** zodat hij terug kan springen en ``stoleMoney`` variabel zal op **False** worden gezet.

```csharp
else if (collision.gameObject.CompareTag("Street") && stoleMoney)
{
      jumpIsReady = true;
      stoleMoney = false;
}
```

Hierna gaan we kijken of er collision heeft plaatsgevonden met de Traveller (Reiziger). Want uiteindelijk is dit iets wat de Thief (Dief) Agent zeker niet mag doen en wordt de Agent hier hard voor afgestraft door **-1** punt af te gaan trekken. Vervolgens wordt de ``EndEpisode()`` methode opgeroepen om de episode te beëindigen.


```csharp
else if (collision.gameObject.CompareTag("Traveller"))
{
      AddReward(-1.0f);
      EndEpisode();
}
```

Tenslotte moeten we ook de Thief (Dief) Agent nog  belonen als hij succesvol over de Traveller (Reiziger) object is gesprongen om de reiziger vervolgens te "bestelen". Dit zal gebeuren door de ``OnTriggerEnter()`` methode.

```csharp
private void OnTriggerEnter(Collider collision)
{
    if (collision.gameObject.CompareTag("Point"))
    {
         AddReward(0.1f);
         stoleMoney = true;
    }
}
```

Als er een collision is met de tag ``"Point"`` dan zal de Thief (Dief) Agent **+0.1** punt erbij krijgen en moet ``stoleMoney`` op **True** gezet worden. Meer uitleg over de ``Point`` object zal hieronder in de volgende topic meegegeven worden.

![image info](https://user-images.githubusercontent.com/56048370/100490645-1c16c900-311d-11eb-9ebb-79a9f7bfa543.png) **DestroyObjects (Optimizations)** <a name="thief8"></a>
<br>
Om de performantie tijdens de trainingsfase zo soepel mogelijk te laten verlopen moeten we een manier voorzien om de gespawnde **Travellers (Reizigers)** zo snel mogelijk te verwijderen nadat ze buiten het zicht zijn van de van de **Thief (Dief) Agent**. Om dit voor elkaar te krijgen gaan we een muur creëren en dit achter de Thief (Dief) Agent zetten zodat elke Traveller (Reiziger) dat botst met deze muur zal verwijderd worden van de scene.

Maak een kubus 3D object aan en laat het er ongeveer uitzien als onderstaande afbeelding. Confirmeer zeker dat deze "muur" net achter de Thief (Dief) Agent staat in de scene.
<br>
<br>
<img alt="header-image" width="40%" height="40%" align="center" src="https://user-images.githubusercontent.com/56048370/100551616-1ab2e100-3282-11eb-9be3-2d799fbcc628.png"/>
<br>
<br>
Verander hierna de *material* design naar *default terrain standard* zoals op onderstaande afbeelding. Dit zal er voor gaan zorgen dat het onzichtbaar wordt.
<br>
<br>
<img alt="header-image" width="40%" height="40%" align="center" src="https://user-images.githubusercontent.com/56048370/100551621-20102b80-3282-11eb-8f1b-d3e45f066fc7.png"/>
<br>
<br>
En tenslotte is er nog deze script bestand genaamd ``DestroyObjects`` die het object dat in collision gaat met de muur verwijderd.

```csharp
public class DestroyObjects : MonoBehaviour
{
    private void OnCollisionEnter(Collision other)
    {
        Destroy(other.gameObject);
    }
}
```
Binnen uw **Traveller** voegt u een empty object toe zoals op onderstaande afbeelding en geeft u het een random naam. In dit voorbeeld gebruiken we als naam *Coins*.
<br>
<br>
<img alt="header-image" width="40%" height="40%" align="center" src="https://user-images.githubusercontent.com/56048370/100551625-27373980-3282-11eb-9470-d874b2615595.png"/>
<br>
<br>
Vervolgens voegt u een tag toe genaamd *Point*. Vervolgens gaan we nu nog de layer op *Ignore Raycast* zetten zoals op onderstaande afbeelding. En dan voegen we een *Box Collider* toe en moet de collider boven de **Traveller (Reiziger) 3D object** zijn in de **area** waarin de **Thief (Dief) Agent** zal springen. Elke keer als de Thief (Dief) hierboven springt zal hij een beloning krijgen door de ``OnTriggerEnter()`` methode.
<br>
<br>
<img alt="header-image" width="40%" height="40%" align="center" src="https://user-images.githubusercontent.com/56048370/100551630-2dc5b100-3282-11eb-8987-c9ff351c9df3.png"/>
<br>
<br>
<img alt="header-image" width="40%" height="40%" align="center" src="https://user-images.githubusercontent.com/56048370/100551638-3ddd9080-3282-11eb-88b0-f6b91e87d0ef.png"/>
<br>
<br>

## :point_right: Resultaat in Tensorflow na één uur testen  <a name="tensorflow"></a>
The second paragraph text
