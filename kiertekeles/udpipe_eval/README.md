# [UDPipe](http://ufal.mff.cuni.cz/udpipe) kiértékelés

## A kiértékelés alapanyaga
A kiértékeléshez a [KorKor](https://github.com/vadno/korkor_pilot) korpusz egy részét használtam.

* __kiértékelendő__ anyag: az UDPipe kimenete (az [emtsv](https://github.com/dlt-rilmta/emtsv) eszközben használva (elemzés időpontja: 2020.08.06.))
* __gold standard__: az emTag kézzel javított kimenete UD címkére konvertálva az [emmorph2ud](https://github.com/vadno/emmorph2ud ) konverterrel

Az UDPipe magyar modelljének 

#### Méretek
* 121 fájl
* 1899 mondat
* 36144 token írásjelekkel együtt (a gold adaton számolva)

#### Összevetés
Az összevetéshez az [emDiff](https://github.com/vadno/emdiff) kiértékelő modulját használtam.
Bemeneti formátumként xtsv-t fogad.

#### Mérőszámok
Az emDiff a címkék kiértékeléséhez a __pontosság__ (accuracy) mérőszámát használta.

#### Eredmények
|                   | átlag   | összesített |
| ----------------- |--------:| -----------:|
| Lemma             | 85,02%  | 85,08%      |
| UPOS              | 81,12%  | 81,24%      |

Összehasonlításképp az UDPipe által kimért teljesítmények a magyar modellhez [itt](http://ufal.mff.cuni.cz/udpipe/models) olvashatók.

#### Hibaanalízis
