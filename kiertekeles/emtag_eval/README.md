# [emTag](https://github.com/ppke-nlpg/purepos) kiértékelés

## A kiértékelés alapanyaga
A kiértékeléshez a [KorKor](https://github.com/vadno/korkor_pilot) korpusz egy részét használtam.

* __kiértékelendő__ anyag: az emTag kimenete (az [emtsv](https://github.com/dlt-rilmta/emtsv) eszközben használva (elemzés időpontja: 2019.02.))
* __gold standard__: az emTag kézzel javított kimenete

#### Méretek
* 121 fájl
* 1720 mondat
* 36492 token írásjelekkel együtt (a gold adaton számolva)

#### Összevetés
Az összevetéshez az [emDiff](https://github.com/vadno/emdiff) kiértékelő modulját használtam.
Bemeneti formátumként xtsv-t fogad.

#### Mérőszámok
Az emDiff a címkék kiértékeléséhez a __pontosság__ (accuracy) mérőszámát használta.

#### Eredmények
|                   | átlag   | összesített |
| ----------------- |--------:| -----------:|
| tő                | 98,23%  | 98,15%      |
| morfológiai címke | 95,48%  | 95,40%      |


#### Hibaanalízis
