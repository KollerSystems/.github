# Funkcionális Specifikáció

## Bevezetés
- A Koller egy fejlett, automatizált digitális rendszer, melyben minden olyan funkció megtalálható, ami egy kollégium összhangos működéséhez szükséges. A rendszer célja, hogy megkönnyítse a tanárok és a tanulók élétét, nyomon kövesse a diákok mozgását, kezelje a kimenőket, jelenléteket, szobaértékeléseket és menza adatokat, valamint statisztikai elemzéseket biztosítson. A rendszer elérhető weben, valamint Android és iOS platformokon.
- Rendszer célcsoportjai: Kollégiumi dolgozók, tanulók

## Funkciók

### Felhasználók

#### Tanulók
- Személyes adatok
- Kollégiumi adatok
   - Szobaszám
   - Csoport
   - Osztály
   - Fokozat
 
#### Tanárok
- Kollégiumi adatok
   - Irodaszám
   - Csoportszám (ha csoportvezető)
 
### Helyiségek

- telephely?
- épület
- szárny
- emelet
- szoba
- megnevezés (113, lány kondi, igazgatói)

Ezek lehetnek akár specifikusak:
- iroda
- tanulói szoba
- terem
- konyha
- étkező

### (Kollégiumi) osztályok

Különböző iskolák azonos évfolyamaiból állnak (pl.: 9A és 9B néhány tanulója -> 9B kollégiumi osztály. Nem lehet 9.-esből 10.-es)

### Csoportok

Bármely diákoknak egy összeállított csoportja egy csoportvezető nevelőtanárral az élén. Egy szobában csak ugyanolyan csoportban lévő emberek lakhatnak.

### Portai ki- és belépések

Akár teljesen automatikus közlekedést könyvelő rendszer.

#### Késés

Akkor jön létre, és arra az időre csak, amikor a diáknak bent kellett volna lennie védett időszakban.

```
o: szabadidő
v: védett
[: kimenetele
]: bejövetele

o[oo]ovvvooovvvoooo -> nincs késés
oo[oov]vvooovvvoooo -> 1db v késés
oo[oovvvo]oovvvoooo -> 3db v késés (hiszen szabadideje is volt közben, csak védettről késett)
ooo[ovvvooovvvo]ooo -> 6db v késés (csak védett időket számolja)
```

Természetesen a kimenő feljogosítja a védett időszakban nem bent lenni, így ez kivonódik, azonban ha letelik a megengedett ideje, a rendszer késést onnantól kezd számolni.

Késést nevelőtanár igazolhat, azonban nincs joga magától beírni. Az igazolás az adott késésre egyelőre bináris, tehát két fajtája van: aktív és igazolt.

#### Sietés

Tájékoztató jellegű a portásnak és a diáknak, hogy mennyivel korábban ment el a megengedettnél. Következménye nincs, a késésbe lesz majd beleszámítva. Természetesen ha pl 25 percet siet, de 5 perc múlva már vissza is jön, akkor csak 5 percet késett.

#### Kimenő

A kimenő feljogosít védett időszakon belül közlekedni, bizonyos időintervallumban.

### Kulcsfelvétel

Lehetőség van:
- Megnézni, kik vannak épp hozzárendelve egy helyiséghez
- Kiknél vannak éppen kulcsok
- Jogosultságot adni a tanulóknak adott kulcsokhoz adott kritériumokkal.

### Alapprogram és kötelezően választható (min 1) szakkör

#### Alapprogram
Több téma van, az adott témát/témákat egy tanár tart minden kollégiumi osztálynak más időpontokban.

#### Szakkör
Ezekre mindenki igénye szerint jelentkezik (egyre legalább kötelező). Ez egy adott témakörrel foglalkozó, ismétlődő program, amit egy adott tanár tart. Olyasmi mint egy sima tantárgy.

Tanárok a rendszerben jelölik a jelenlétet.

### Szobaértékelés
Tanárok értékelhetik a lakószobákat.

### Létszámozás
Tanárok létszámozhatják a lakószobákat.

### Dícséret és figyelmeztető

Tulajdonság bármelyikre:
- jellege, azaz aki feladja annak titulusa (szaktanári, nevelőtanári, igazgatói stb.)
- ki adta
- kinek adta
- miért
- mikor

### Ügyelet

Ha a munkrandben ügyeletes lesz egy tanár és készen is áll az átvételre a kollégájától, rendszerben is átveszi.

### Menza

Lehetőség van a rendszerbe feltöltött menza menü böngészésére.

### Statisztika

Mindenféle adatoból kiállítható statisztikák egy adott időintervallumon belül.

## Folyamatok

### Jelentkezés

Két féle jelentkezés van:
- Új tanuló => Minden adatot meg kell adni
- Régi => Adategyeztetés

1. Diák jelentkezik az adott kollégiumba
2. Tanár látja a jelentkezett diákokat (személyes adatok stb.)
3. Felveszi/elutasítja => lesz hozzáférése/nem
4. Kollégium-specifikus adatait beviszik a rendszerbe (osztály, szoba)
5. beléptető bilétájába ráírják a felhasználó beléptető kulcsát
6. Személyes megjelenésekor megkapja a bilétát + kép készülhet róla

### Leszerelés

Okai lehetnek:
- Jogviszonyát szeretné megszüntetni a diák
- Tanár szünteti meg a jogviszonyát
- Lejár a jogviszonya (1 tanév)

1. Tanár beadja a leszerelési igényt (KELL egyeztetni tanárral, rendszerből nem lehet)
  - könyvtári tartozás
  - sportszertári
  - szobai kártérítési
  - raktári, értkezési
  - kártérítési
2. Tanuló jóváhagyja
3. Leadja bilétáját
4. Portás kiengedi
5. Hozzáférése a rendszerhez korlátozódik
   - adattörténelme megmarad
   - státusza leszerté válik
     - nem lesznek felé elvárások
     - rejtve lesz a rendszerben

### Portai közlekedés

Ki/beléptetőkapu feltételezése

1. biléta használata
2. kapun való átlépés
3. Mozgás rögzítése
4. portás látja a legfrissebb mozgásokat a rendszerben
   - név
   - profilkép
   - csoport
   - fokozat
   - kilépés időpontja
   - irány
   - mozgás szabályossága
     - korán megy el
     - kesőn jön be
     - kimenővel közlekedett-e
   
A portás be- és kiengedhet könyvelésen kívűl is embereket.

### Kimenők

Ennek két kezdete is lehet:
- Diák kérvényezi, majd tanár jóváhagyja
- Tanár létrehozza magától

Tárolandó:
- frekvenciája (ismétlődés: soha, a hét napjain egyszer, hetente, kéthetente vagy négyhetente)
- időbeli kezdete
- időbeli vége
- ismétlődés lejárta (ha alkalmazható)
- oka/célja
- kinek/kiknek szól

### Kulcsfelvétel

Két fajta kulcs létezik:
- jogosult személy (portás) engedélyezi, elutasítja a kérelmet (fontosabb kulcsok)
- önmagát jogosítja a tanuló => értesíti a felelős illetőt

Tárolandó:
- Helyiség neve
- időintervallum (kezdet egyből, lezárta miután visszavitte); ezt automatikusan beírja fel- és leadáskor (azonban ezt a diáknak az alkalmazásban jelezni kell)
- kulcsfelvevő azonosítója

Hasonlóan a kimenőkhöz, a kulcsfelvevőknek is lehet engedélyük bizonyos "védett" kulcsokat felvenni (stúdió). Ezek engedélye is lehet bizonyos időkre szűkítve (csak szakkörös napokon például)
Tárolandó:
- engedélyezett felhasználó
- engedélyezett kulcs
- engedély kezdete időben
- vége időben
- frekvenciája (periodikusan ismétlődhet)

### Szobaértékelés és létszámozás

Két féle képpen indítható:
- az adott emelet adott szárnyaiban lévő szobákra
- egy adott szobára

#### Szobarend
1. Szempontok értékelése
2. Végső értékelés
   - Automatikus a szempotok alapján
   - Manuális
3. Következő szobák
5. Értékelések közzé tétele

#### Szobalétszám
1. adott szobában tartózkodó diákok megjelölése jelenlévőnek, vagy nem.
   - Ha valaki a beléptető rendszer szerint kint van, automatikusan el lesz könyvelve nem jelenlévőnek
2. Következő szobák
3. Értékelések közzé tétele

### Menza rendszerbe való feltöltésének

0. PDF formátumú dokumentum Jsonné alakaítása
1. Json fájl feltöltése a rendszerbe, esetleges szerkesztések
2. Közzététel

# Repository
![Metrics](/github-metrics.svg)
