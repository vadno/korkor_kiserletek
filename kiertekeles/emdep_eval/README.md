# [emDep](https://github.com/antaljanosbenjamin/magyarlanc/tree/b558823b2d1f9cdc0b5c0ad93b628e96fe251cc1) kiértékelés

## A kiértékelés alapanyaga
A kiértékeléshez a [KorKor](https://github.com/vadno/korkor_pilot) korpusz egy részét használtam.
Azért csak egy részét, mert a korpusz építése során ezeken a fájlokon nem történt tokenszám-módosító javítás, így ugyanolyan tokenszámú fájlokat és mondatokat lehetett összehasonlítani.
A fájlok nem a végleges KorKor korpuszból vannak, hanem az annak építésekor keletkező köztes állapotú fájlok.
Ennek az az oka, hogy a KorKor korpusz tartalmaz zéró elemeket (zéró létigéket és névmásokat), ezzel szemben a függőségi elemző nem produkál ilyeneket.

* __kiértékelendő__ anyag: az emDep kimenete (az [emtsv](https://github.com/dlt-rilmta/emtsv) eszközben használva (elemzés időpontja: 2019.08.03.))
* __gold standard__: az emDep kézzel javított kimenete (a [WebAnno](https://webanno.github.io/webanno/) eszköz segítségével)

#### Méretek
* 96 fájl
* 1530 mondat
* 29823 token írásjelekkel együtt

#### Összevetés
Az összevetéshez az [emDiff](https://github.com/vadno/emdiff) kiértékelő modulját használtam, ami képes függőségi elemzés kiértékelésére is.
Bemeneti formátumként xtsv-t fogad.

#### Formátumok
A WebAnno [CoNLL-U formátumú](https://universaldependencies.org/format.html) fájlt fogad és bocsát ki.
Az összevetéshez használt fájlok formátuma ezért eredetileg CoNLL-U.
Az emDiff használatához szükséges konvertálni a fájlokat xtsv-re, ezt a [conllu2xtsv](https://github.com/vadno/conllu2xtsv) konverter segítségével végeztem.

#### Mérőszámok
Az emDiff a függőségi elemzés kiértékelésében szokásos mérőszámokat biztosít a kiértékeléskor.
A függőségi elemzés kiértékelésekor vizsgálhatjuk a címke (a függőségi típusa), valamint a kapcsolat (a csomópont, amelytől a token az adott kapcsolattípussal függ) értékét.
Az __UAS__ (unlabeled attachment score) tekintet nélkül a kapcsolat fajtájára pusztán a fa felépítését tekinti, tehát azt, hogy az egyes csomópontok ugyanahhoz az anyacsomópontokhoz kapcsolódnak-e, mint a gold standard anyagban.
A __LAS__ (labeled attachment score) a fa felépítése mellett az élcímkéket is számításba veszi.

Az UAS és LAS mérőszámok kiszámíthatók az egyes mondatokra, az egyes fájlokra és a vizsgálandó anyag egészére is.
A kiértékelés során a teljes anyagra és fájlonként is kiszámítottam az UAS és LAS értékeket, az utóbbi esetben átlagszámítással következtettem a teljes anyag minőségére.

#### Eredmények
|         | átlag   | összesített  |
| ------- |--------:| ------------:|
| LAS     | 0,83    | 0,83         |
| UAS     | 0,87    | 0,87         |

#### Kivételként kezelt esetek
A KorKor korpusz néhány esetben eltér az emDep által használt címkekészlettől.
Ezeket az eltéréseket kivételként kellett kezelni a kiértékelés során.
Az emDep __ATT__ címkét ad a birtokos és birtoka közötti függőségi élre, míg a KorKor korpuszban ez a kapcsolat meg van különböztetve a többi __ATT__ címkével jelölt kapcsolattól és __POSS__ címkével jelöli.
Ezt a különbséget nem tekintem hibának és a kezelése is egyszerű.
A kiértékeléskor egyszerűen minden __POSS__ címkét __ATT__ címkeként kell tekinteni.

#### Hibaanalízis

