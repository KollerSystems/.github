# Funkcionális Specifikáció

## Jelentkezés folyamata

Két féle jelentkezés van:
- Új tanuló => Mindent meg kell adni
- Régi => Adategyeztetés

1. Diák jelentkezik az adott kollégiumba
2. Tanár látja a jelentkezett diákokat (személyes adatok stb.)
3. Felveszi/elutasítja => lesz hozzáférése/nem
4. Kollégium-specifikus adatait beviszik a rendszerbe (osztály, szoba)
5. Személyes megjelenésekor kap bilétát (belépéshez) + kép készülhet róla
6. Tanév végén "kirúgja a rendszer" -> véget ér a jelentkezés (adatkezelés miatt)

## Leszerelés folyamata

Okai lehetnek:
- Jogviszonyát szeretné megszüntetni a diák
- Tanár szünteti meg a jogviszonyát
- Lejár a jogviszonya (1 tanév)

1. Tanár beadja a leszerelési igényt (KELL egyeztetni tanárral, appból nem lehet)
  - könyvtári tartozás
  - sportszertári
  - szobai kártérítési
  - raktári, értkezési
  - kártérítési
2. Tanuló jóváhagyja
3. Leadja bilétáját
4. Portás kiengedi
5. Hozzáférése a rendszerhez korlátozódik, státusza leszerté válik, de adatai megmaradnak (szobájából helye felszabadul azért)
  - TODO!

## Portai közlekedés

Kapu feltételezése

1. biléta használata
2. kapun való átlépés
3. portás látja a mozgását a rendszerben
  - név
  - profilkép
  - csoport
  - kimenési jogosultsága
  - kilépés időpontja
  - irány
  - mozgás szabályossága
    - korán megy el
    - kesőn jön be

## Kimenők rendszere

A kimenő feljogosít védett időszakon belül közlekedni, bizonyos időintervallumban.

Ennek két kezdete is lehet:
- Diák kérvényezi, majd tanár jóváhagyja
- Tanár létrehozza magától

Tulajdonságai:
- frekvenciája (ismétlődés: soha, bizonyos napokon egyszer, hetente, kéthetente vagy négyhetente)
- időbeli kezdete
- időbeli vége
- ismétlődés lejárta (ha alkalmazható)
- oka/célja
- kinek/kiknek szól

## Késések

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

Késést nevelőtanár igazolhat, azonban nincs joga magától beírni. Az igazolás egyelőre bináris, tehát két fajtája van: aktív és igazolt.

## Kulcsfelvétel folyamata

Két fajta kulcs:
- jogosult személy (portás) engedélyezi, elutasítja a kérelmet (fontosabb kulcsok)
- önmagát jogosítja a tanuló (becsületkasszás) => értesíti a felelős illetőt

Tulajdonságai:
- Helyiség neve
- időintervallum (kezdet egyből, lezárta miután visszavitte); ezt automatikusan beírja fel- és leadáskor (azonban ezt a diáknak az alkalmazásban jelezni kell)
- kulcsfelvevő azonosítója

Hasonlóan a kimenőkhöz, a kulcsfelvevőknek is lehet engedélyük bizonyos "védett" kulcsokat felvenni (110 például). Ezek engedélye is lehet bizonyos időkre szűkítve (stúdió csak szakkörös napokon például)
Tárolandó:
- engedélyezett azonosítója
- engedélyezett kulcs
- engedély kezdete időben
- vége időben
- frekvenciája (periodikusan ismétlődhet)

## Alapprogram és kötelezően választható (min 1) szakkör

Alapprogram: Egy kollégiumi osztály jár rá, mindig más témakör. Ez a témakör időnként változik, független az osztálytól, évfolyamtól.
Kollégiumi osztály: különböző iskolák azonos évfolyamaiból ollózzák össze (9A -> 9B, de nem lehet 9.-esből 10.-es)

Szakkör: Egyet legalább fel kell venni, ez egy ismétlődő témájú program. Olyasmi mint egy sima tantárgy.

TODO!

## Dícséretek és figyelmeztetők rendszere

Tulajdonság bármelyikre:
- jellege, azaz aki feladja annak titulusa (szaktanári, nevelőtanári, igazgatói stb.)
- ki adta
- kinek adta
- miért
- mikor

## Helyiségek tulajdonsága

- telephely?
- épület
- szárny
- emelet
- szoba

Ezek lehetnek specifikusak:
- iroda
- tanulói szoba
- semmilyen
