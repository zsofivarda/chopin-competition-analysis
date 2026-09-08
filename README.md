# Chopin Nemzetközi Zongoraverseny – Adatelemzés

## Áttekintés

Ez a projekt a Nemzetközi Chopin Zongoraverseny (Varsó) eredményeit elemzi 1927-től 2025-ig, 19 versenykiírás adatai alapján. A cél az volt, hogy megvizsgáljam, mely országokból kerülnek ki a legsikeresebb versenyzők, hogyan változott a mezőny nemzetközi összetétele az idők során, és mely országok vannak jelen a legkonzisztensebben a verseny történetében.

## Motiváció

Közel két évtizedes klasszikus zenei (kürtművész-kürttanári) szakmai háttérrel rendelkezem, jelenleg pedig gazdaságinformatikus végzettséggel adatelemzői pályára készülök. Ez a projekt lehetőséget adott arra, hogy a zenei szakmai tudásomat és az újonnan megszerzett adatelemzői készségeimet (SQL, Power BI) egyetlen, számomra személyesen is releváns témában kapcsoljam össze.

## Használt eszközök

* **Excel / Power Query** – adatgyűjtés és -tisztítás
* **Microsoft SQL Server + SSMS** – adattárolás és elemző lekérdezések
* **Power BI Desktop** – vizualizáció és dashboard-készítés

## Adatforrás

Az adatok a Wikipédia egyes Chopin-verseny kiírásainak oldalairól, valamint a Nemzetközi Chopin Zongoraverseny hivatalos honlapjáról származnak (1927–2025, 19 versenyév), kézi gyűjtéssel és Power Query-s importálással összeállítva.

## Módszertan

1. **Adatgyűjtés**: az egyes versenyévek Wikipédia-táblázatainak importálása Excelbe (Power Query "Webről" funkció)
2. **Tisztítás**: whitespace-hibák, országnév-inkonzisztenciák, kategorizálási pontatlanságok javítása
3. **Kategorizálás**: minden versenyző besorolása három kategória egyikébe:

   * *Döntő + helyezés* – számozott helyezést elért döntősök
   * *Döntő + díjazott* – helyezés nélkül, de pénzdíjjal jutalmazott döntősök
   * *Egyéb díjazott* – különdíjasok, akik nem jutottak döntőbe
4. **SQL elemzés**: csoportosító és összesítő lekérdezések (országonkénti eloszlás, időbeli trendek, részvételi konzisztencia)
5. **Power BI vizualizáció**: kétoldalas interaktív dashboard

## Főbb megállapítások

* A helyezettek (Döntő + helyezés kategória) alapján a **Szovjetunió/Oroszország (33)** és **Lengyelország (31)** dominálja a versenyt, messze megelőzve a többi országot.
* A verseny **már a 2. kiírástól (1932) kezdve nemzetközivé vált** (6 különböző ország), nem egy fokozatos, lassú folyamat eredményeként.
* **1949-ben jelentősen visszaesett** a résztvevő országok száma (2 ország, szemben az 1937-es 6-tal) – ez valószínűleg a II. világháborút követő időszak korlátozottabb nemzetközi kapcsolataival függhet össze, bár ennek pontos okát nem vizsgáltam részletesen.
* A **részvételi konzisztencia** (hány különböző évben szerepelt egy ország) más sorrendet mutat, mint az összesített döntős-szám: **Japán** a versenyek 12-ből, **Lengyelország** 16-ból volt jelen, ami arra utal, hogy egyes országok nem csak mennyiségileg, hanem időben elhúzódóan is jelen vannak a mezőnyben.

## Dashboard felépítése

**1. oldal – Országok és trendek**

* Helyezettek száma országonként (oszlopdiagram)
* Országok száma évenként (vonaldiagram)
* Rövid kontextus az 1949-es visszaesésről

**2. oldal – Részvétel és kategóriák**

* Versenyeken való részvétel gyakorisága országonként (oszlopdiagram)
* Döntősök megoszlása kategóriák szerint (donut chart)

## Fájlstruktúra

```
├── README.md
├── data/
│   └── chopin\_versenyek.csv       # Végleges, tisztított adat
├── powerbi/
│   └── Chopin\_verseny\_elemzes.pbix
└── screenshots/
    ├── page1\_orszagok\_trendek.png
    └── page2\_reszvetel\_kategoriak.png
```

## Screenshotok



!\[1. oldal – Országok és trendek](screenshots/page1\_orszagok\_trendek.png)

!\[2. oldal – Részvétel és kategóriák](screenshots/page2\_reszvetel\_kategoriak.png)

