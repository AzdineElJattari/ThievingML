<p align="center"><img alt="header-image" src="https://user-images.githubusercontent.com/56048370/100483716-28d5f580-30fa-11eb-887e-fc7a82af392c.png" width="100"/></p>
<h2 align="center">Thieving ML</h2>
<p align="center">:robot: Dit is een eenvoudige tutorial die je laat kennismaken met de wereld van Machine Learning :robot:</p>
<br>
  
<table align="center"><tr><td align="center" width="9999">

**<img alt="header-image" align="center" src="https://user-images.githubusercontent.com/56048370/100488272-83c51800-310d-11eb-9353-332a22e894a3.png"/> [Youtube](https://www.youtube.com/channel/UCGW01S5Ri2RMa-qqXtO9Tzw?view_as=subscriber) 
• <img alt="header-image" align="center" src="https://user-images.githubusercontent.com/56048370/100491240-533ba900-3122-11eb-815b-3beabde80e62.png"/> [Rapporteer bug](https://github.com/AzdineElJattari/ThievingML/issues) 
• <img alt="header-image" align="center" src="https://user-images.githubusercontent.com/56048370/100491250-66e70f80-3122-11eb-9f76-c2cdd32ddfdc.png"/> [Vraag feature aan](https://github.com/AzdineElJattari/ThievingML/issues) 
• <img alt="header-image" align="center" src="https://user-images.githubusercontent.com/56048370/100488703-22527880-3110-11eb-8da1-1dda2acc4600.png"/> [Contacteer ons](thievingml@gmail.com)**

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
<img alt="header-image" width="60%" height="60%" align="center" src="https://user-images.githubusercontent.com/56048370/100528009-4083ab80-31d8-11eb-9f33-925c4db06548.png"/>
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
<img alt="header-image" width="60%" height="60%" align="center" src="https://user-images.githubusercontent.com/56048370/100528224-9d806100-31da-11eb-845e-6992cf4125a6.png"/>

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
<img alt="header-image" width="25%" height="15%" align="center" src=""/>


### ![image info](https://user-images.githubusercontent.com/56048370/100489562-14532680-3115-11eb-9621-04bcf5aca2a7.png) Reiziger object <a name="reizigerobject"></a>
This is a sub paragraph

### ![image info](https://user-images.githubusercontent.com/56048370/100489562-14532680-3115-11eb-9621-04bcf5aca2a7.png) Scorebord object <a name="scorebordobject"></a>
This is a sub paragraph

## :point_right: Het gedrag van de Agent en de andere spelobjecten <a name="gedrag"></a>
The second paragraph text

## :point_right: Spelobjecten scripts (C#) <a name="allescripts"></a>
The second paragraph text

### ![image info](https://user-images.githubusercontent.com/56048370/100490290-a4479f00-311a-11eb-839d-3ef719df2eb7.png) Environment.cs <a name="scripts"></a>
The second paragraph text

![image info](https://user-images.githubusercontent.com/56048370/100489836-2b931380-3117-11eb-98ea-59fd67012cb0.png) Overzicht methodes van de omgeving <a name="environment"></a>
<br>
<br>
This is a sub paragraph

![image info](https://user-images.githubusercontent.com/56048370/100489836-2b931380-3117-11eb-98ea-59fd67012cb0.png) Object-variabelen van de omgeving <a name="environment2"></a>
<br>
<br>
This is a sub paragraph

![image info](https://user-images.githubusercontent.com/56048370/100489836-2b931380-3117-11eb-98ea-59fd67012cb0.png) Initialisatie van de omgeving instantie <a name="environment3"></a>
<br>
<br>
This is a sub paragraph

![image info](https://user-images.githubusercontent.com/56048370/100489836-2b931380-3117-11eb-98ea-59fd67012cb0.png) Opkuisen van het speelveld <a name="environment4"></a>
<br>
<br>
This is a sub paragraph

![image info](https://user-images.githubusercontent.com/56048370/100489836-2b931380-3117-11eb-98ea-59fd67012cb0.png) Scorebord <a name="environment5"></a>
<br>
<br>
This is a sub paragraph

![image info](https://user-images.githubusercontent.com/56048370/100489836-2b931380-3117-11eb-98ea-59fd67012cb0.png) Genereren van een traveller <a name="environment6"></a>
<br>
<br>
This is a sub paragraph

### ![image info](https://user-images.githubusercontent.com/56048370/100490290-a4479f00-311a-11eb-839d-3ef719df2eb7.png) Traveller.cs <a name="scripts2"></a>
The second paragraph text

### ![image info](https://user-images.githubusercontent.com/56048370/100490290-a4479f00-311a-11eb-839d-3ef719df2eb7.png) Thief.cs <a name="scripts3"></a>
The second paragraph text

![image info](https://user-images.githubusercontent.com/56048370/100490645-1c16c900-311d-11eb-9ebb-79a9f7bfa543.png) Overzicht van methodes <a name="thief"></a>
<br>
<br>
The second paragraph text


![image info](https://user-images.githubusercontent.com/56048370/100490645-1c16c900-311d-11eb-9ebb-79a9f7bfa543.png) Object variabelen <a name="thief2"></a>
<br>
<br>
The second paragraph text

![image info](https://user-images.githubusercontent.com/56048370/100490645-1c16c900-311d-11eb-9ebb-79a9f7bfa543.png) Initialiseer de dief <a name="thief3"></a>
<br>
<br>
The second paragraph text

![image info](https://user-images.githubusercontent.com/56048370/100490645-1c16c900-311d-11eb-9ebb-79a9f7bfa543.png) OnEpisodeBegin <a name="thief4"></a>
<br>
<br>
The second paragraph text

![image info](https://user-images.githubusercontent.com/56048370/100490645-1c16c900-311d-11eb-9ebb-79a9f7bfa543.png) Heuristic <a name="thief5"></a>
<br>
<br>
The second paragraph text

![image info](https://user-images.githubusercontent.com/56048370/100490645-1c16c900-311d-11eb-9ebb-79a9f7bfa543.png) OnActionReceived <a name="thief6"></a>
<br>
<br>
The second paragraph text

![image info](https://user-images.githubusercontent.com/56048370/100490645-1c16c900-311d-11eb-9ebb-79a9f7bfa543.png) OnCollisionEnter <a name="thief7"></a>
<br>
<br>
The second paragraph text

![image info](https://user-images.githubusercontent.com/56048370/100490645-1c16c900-311d-11eb-9ebb-79a9f7bfa543.png) DestroyObjects (Optimizations) <a name="thief8"></a>
<br>
<br>
The second paragraph text

## :point_right: Resultaat in Tensorflow na één uur testen  <a name="tensorflow"></a>
The second paragraph text
