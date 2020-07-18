# [emZero](https://github.com/vadno/emzero) kiértékelés

## A kiértékelés alapanyaga
A kiértékeléshez a [KorKor](https://github.com/vadno/korkor_pilot) korpusz egy részét használtam.

* __kiértékelendő__ anyag: az emZero kimenete (elemzés időpontja: 2019.10.10.)
* __gold standard__: az emZero kézzel javított kimenete, a KorKor pilotkorpusz [fájljai](https://github.com/vadno/korkor_pilot/tree/master/korkor/koreferencia)

#### Méretek
* 95 fájl
* 1436 mondat
* 31492 token írásjelekkel együtt (a gold adaton számolva)

#### Összevetés
Az összevetéshez az [emDiff](https://github.com/vadno/emdiff) kiértékelő modulját használtam.
Bemeneti formátumként xtsv-t fogad.

Az emZero szabályalapú szkript a testetlen finit ige alanyát, a határozott ragozású ige testetlen tárgyát és a birtok testetlen birtokosát illeszti be a mondatok függőségi fájába.
A korpusz építésekor ezeket a beillesztett testetlen elemeket ellenőriztük és javítottuk.
A kiértékeléskor az ellenőrzött korpusszal vetjük össze az eredeti kimenetet.

#### Mérőszámok
Az emDiff a címkék kiértékeléséhez a __pontosság__ (precision), __fedés__ (recall) és ezek harmonikus közepe, az __F-mérték__ (F-measure) mérőszámokat használta.

#### Eredmények
|                   | átlag   | összesített |
| ----------------- |--------:| -----------:|
| pontosság         | 93,08%  | 92,26%      |
| fedés             | 85,30%  | 85,25%      |
| F-mérték          | 88,16%  | 88,61%      |

#### Hibaanalízis
