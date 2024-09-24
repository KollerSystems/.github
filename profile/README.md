# Funkcionális specifikációk
## 1. Bevezetés
- Projekt leírása: A Koller egy fejlett, automatizált digitális rendszer, melyben minden olyan funkció megtalálható, ami egy kollégium összhangos működéséhez szükséges. A rendszer célja, hogy megkönnyítse a tanárok és a tanulók élétét, nyomon kövesse a diákok mozgását, kezelje a kimenőket, jelenléteket, szobaértékeléseket és menza adatokat, valamint statisztikai elemzéseket biztosítson. A rendszer elérhető weben, valamint Android és iOS platformokon.
- Rendszer célcsoportjai: Kollégiumi tanárok, tanulók
- Érintett rendszerek:
  - NFC beléptető rendszer (Mifare Classic NFC technológia)
  - Szerver
  - Felhasználói felületek
  - PDF-ből JSON-ba alakító menza menüparser

## 2. Funkciók
- Kimenők kezelése
  - Egy tanár képes egyszeri vagy többször használatos kimenőt rögzíteni egy adott időszakra, ezzel tovább szabályozva a kollégiumból való ki- és belépést.
  - A rendszer automatikusan nyomon követi a kimenőket, és késés esetén azt a kimenőhöz igazítja.
- Ki- és belépések követése
  - Az NFC biléta használatával a felhasználók ki- és beléphetnek a kollégiumból, amit a portás a saját asztali gépén is lát.
  - A rendszer minden ki- és belépést rögzít, valamint a késéseket automatikusan elkönyveli.
  - Portásnak és tanároknak jogosultsága van törölni áthaladást.
  - Portás beengedhet könyvelésen kívűl is felhasználókat.
- Szobaértékelések kezelése
  - A szobák tisztasági szintje értékelhető különböző kritériumok alapján, amely automatikusan vagy manuálisan egy 1-től 5-ig terjedő skálán véglegesíthető.
- Dícséretek és figyelmeztetések könyvelése
  - A rendszer lehetőséget biztosít különböző szintű dícséretek és figyelmeztetések rögzítésére, amelyek a diákok pontozási rendszerét is befolyásolják.
- Ügyeletes tanárok kezelése
  - A tanárok képesek saját magukat ügyeletesnek beállítani.
  - Több tanár is lehet egyszerre ügyeletes, és az ügyeleti rend nyomon követhető.
- Menza menedzsment
  - A tanárok képesek feltölteni étkezési adatokat (reggeli, ebéd, vacsora) és azok allergén tartalmait.
  - Egy menüparser segítségével a harmadik féltől száramazó PDF-ből automatikusan feltölthetőek ezek az adatok.
- Programok és szakkörök kezelése
  - A rendszer támogatja a kötelező alapprogramok és szakkörök létrehozását, könyvelését és jelenlétének nyomon követését.
- Pontozó rendszer
  - A diákok pontszámait különböző tényezők (dícséretek, figyelmeztetések, késések, szobaértékelések) alapján számítja ki a rendszer.
- Felhasználók kezelése
  - A tanárok kezelhetik a felhasználókat, valamint létrehozhat új felhasználókat.
- Helyiségek kezelése
  - A rendszer lehetőséget biztosít szobák, tantermek és egyéb helyiségek létrehozására és kezelésére.
- Osztályok és csoportok kezelése
  - A rendszer támogatja az osztályok és csoportok létrehozását, kezelését és böngészését.

## 3. Felhasználói interfész és platformok
- Webes felület.
- Mobilalkalmazás: Android és iOS alkalmazás, amely értesítéseket, összefoglalókat és NFC-alapú gyors keresést biztosít.

## 4. Külső interfészek és integrációk
- NFC integráció: Mifare Classic NFC biléta technológia a ki- és beléptetési rendszerhez, mobilos gyors kereséshez.
- PDF-ből JSON parser: Harmadik fél által biztosított PDF menük automatikus átalakítása JSON formátumba.

# Repository
![Metrics](/github-metrics.svg)
