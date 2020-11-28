<p align="center"><img alt="header-image" src="https://user-images.githubusercontent.com/56048370/100483716-28d5f580-30fa-11eb-887e-fc7a82af392c.png" width="100"/></p>
<h2 align="center">Thieving ML-Agents</h2>
<p align="center">:robot: A simple tutorial that will introduce you to the world of Machine Learning :robot:</p>
<br>
  
<table align="center"><tr><td align="center" width="9999">

**<img alt="header-image" align="center" src="https://user-images.githubusercontent.com/56048370/100488272-83c51800-310d-11eb-9353-332a22e894a3.png"/> [Youtube](https://www.youtube.com/channel/UCGW01S5Ri2RMa-qqXtO9Tzw?view_as=subscriber) 
• <img alt="header-image" align="center" src="https://user-images.githubusercontent.com/56048370/100491240-533ba900-3122-11eb-815b-3beabde80e62.png"/> [Report bug](https://github.com/AzdineElJattari/ThievingML/issues) 
• <img alt="header-image" align="center" src="https://user-images.githubusercontent.com/56048370/100491250-66e70f80-3122-11eb-9f76-c2cdd32ddfdc.png"/> [Request feature](https://github.com/AzdineElJattari/ThievingML/issues) 
• <img alt="header-image" align="center" src="https://user-images.githubusercontent.com/56048370/100488703-22527880-3110-11eb-8da1-1dda2acc4600.png"/> [Contact Us](https://www.youtube.com/channel/UCGW01S5Ri2RMa-qqXtO9Tzw?view_as=subscriber)**

</td></tr></table>

# Inhoud
1. [Introductie ThievingML](#introductie)
2. [Spelverloop](#spelverloop)
3. [Observaties, acties & beloning systeem](#beloning)
4. [Het speelveld](#speelveld)
5. [De spelomgeving](#spelomgeving)
    - [Speelveld object](#speelveldobject)
    - [Dief object](#diefobject)
    - [Reiziger object](#reizigerobject)
    - [Scorebord object](#scorebordobject)
6. [Spelobjecten scripts (C#)](#allescripts)
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
7. [Resultaat in Tensorflow na één uur testen](#tensforlow)
    
## :point_right: Introductie ThievingML <a name="introductie"></a>
Some introduction text, formatted in heading 2 style

## :point_right: Spelverloop <a name="spelverloop"></a>
The first paragraph text

## :point_right: Observaties, acties & beloning systeem <a name="beloning"></a>
The second paragraph text

## :point_right: Het speelveld <a name="speelveld"></a>
The second paragraph text

## :point_right: De spelomgeving <a name="spelomgeving"></a>
The second paragraph text

### ![image info](https://user-images.githubusercontent.com/56048370/100489562-14532680-3115-11eb-9621-04bcf5aca2a7.png) Speelveld object <a name="speelveldobject"></a>
This is a sub paragraph

### ![image info](https://user-images.githubusercontent.com/56048370/100489562-14532680-3115-11eb-9621-04bcf5aca2a7.png) Dief object <a name="diefobject"></a>
This is a sub paragraph

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
