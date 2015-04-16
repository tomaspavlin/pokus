# Song Maker - specifikace
## Úvod
Tento dokument popisuje vlastnosti a cíle aplikace Song Maker.

### Idea software
Song Maker je aplikace na **komponování hudby** pomocí uživatelem zadaných **pravidel**. Aplikace bude skládat **klavírní** skladby různých žánrů, bude připravená k tomu žánry vytvářet a upravovat a bude umět skladbu zahrát a exportova do souboru **MIDI**.

### Cíl software
Cílem aplikace je skládat takovou hudbu, která se bude **líbit**. Skladby, které bude aplikace vytvářet, se budou navzájem **lišit**. Tyto skladby se budou vytvářet pomocí zapsaných **pravidel**, kdy bude umožněno uživateli jednoduše a přehledně tato pravidla měnit a vytvořit si tak jakoukoli hudbu. Pomocí správně zapsaných pravidel bude aplikace schopná na určitý nástroj **zahrát jakoukoli skladbu**.

## Podrobná specifikace
### Komponování hudby
Po spuštění aplikace Song Maker se zobrazí **okno**, které bude sloužit k ovládání aplikace uživatelem. V první části si uživatel **vybere hudební žánr**, který bude aplikace skládat a bude mít možnost si ho **pomocí formulářů nastavit**. Protože se žánry budou lišit, bude mít každý jiné nastavení. Nastavením myslím například nastavení **délky skladby** nebo **složitosti akordů**. Po kliknutí na tlačítko se **skladba zkomponuje**.

### Pravidla pro skládání
Každý hudební žánr se bude skládat pomocí nějakých pravidel. Množině pravidel tvořící jeden žánr budu říkat **template**. Tato pravidla budou zapsána v textových souborech pomocí mnou vytvořeného jazyka. Budou říkat, co kdy se má hrát, jak se vymyslí rytmus a melodie a jak dlouhá skladba bude.

#### Interpret pravidel
Po kliknutí na tlačítko, které bude komponovat skladbu, se vlastně spustí interpret pravidel, který skladbu vytvoří.

#### Nastavení pravidel
Jak jsem popsal výše, uživateli bude umožněno si zvolený žánr nastavit. Bude to znamenat to, že do pravidel budou moci vstoupit uživatelem zvolené hodnoty a pravidla se jim budou moci přizpůsobit.

### Modifikace skladeb
Již zkomponovanou skladbu bude možné **transponovat** do jiných tónin a měnit její **rychlost**.

### Export
Skladbu bude možné exportovat do **MIDI** souboru a nechat si ji **přehrát**.

#### Dávkový export
Bude možné zautomatizovat komponování a exportování skladeb. Uživatel si bude moci nechat zkomponovat velké množství skladeb a pak z nich vybrat tu nejlepší.

### Vytváření nových pravidel (templates)
Aby psaní pravidel bylo více user-friendly, bude existovat další část programu, ve které uživatel bude moci **graficky nová pravidla vytvářet** a stará upravovat. Jednotlivá pravidla budou reprezentuvána graficky pomocí **barevných panelů** a pomocí barev, znázorněných **čar** a **najetím myši** na panel bude jasné, které s jakým souvisí. Tyto panely bude možné upravovat, odebírat a přidávat.
Cílem této části bude vytvořit takové rozhraní na vytváření nových templates, které dokáže ovládat uživatel, který nemá zkušenosti s programováním, a přitom bude možné vytvářet složité a obsáhlé templates.

#### Jazyk pravidel
Jak jsem zmínil, pravidla budou v textových souborech zapsána pomocí určitého jazyka, který se pak bude interpretovat. Kromě jiného bude tento jazyk obsahovat metody pro vytvoření konsonantních druhů melodií, náhodného či dobře znějícího rytmu, bude umět *zmáčknout* či *pustit* pedál a další.

#### Vytvořená pravidla
Aplikace se dostane k uživateli s již předvytvořenými hudebními žánry (pravidly), kde bude zastoupen **waltz**, **ragtime**, **blues**, **polka** a další žánry, které autor dokáže pochopit a popsat.

### Experimentální část programu
Pravidla ke skládání skladeb nemusí být omezená jen na hudební žánry, nýbrž mohou popisovat jakýkoliv způsob vymýšlení skladeb. Proto se pokusím vytvořit pravidla, která budou co nejvěruhodněji napodobovat způsob skládání skladeb rýznými hudebními skladateli počínaje popovými či rockovými hvězdami, přes skladatele jako *Scott Joplin* a *Jelly Roll Morton* a končeje *Chopenem*.
Tato část je experimentální a rozhodně připoštím, že se nemusí podařit ji naplnit.

## Programátorská specifikace
### MIDI
K vytváření midi souborů využiji volnou knihovnu **Sanford.Multimedia.Midi**.

### Multithreading
Při interpretaci pravidel a při vytváření skladeb UI nezamrzne, nýbrž se interpreter spustí v novém vlákně. Vytváření skladby bude možné přerušit.
