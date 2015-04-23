# Song Maker - specifikace
## Úvod
Tento dokument popisuje vlastnosti a cíle aplikace Song Maker.

### Hlavní myšlenka projektu
Song Maker je aplikace pro Windows na **komponování hudby** pomocí uživatelem zadaných **pravidel**. Aplikace bude skládat **klavírní** skladby různých žánrů, bude připravená k tomu žánry vytvářet a upravovat a bude umět skladbu zahrát a exportova do souboru **MIDI**.

### Cíl projektu
Cílem aplikace je skládat takovou hudbu, která se bude **líbit**. Skladby, které bude aplikace vytvářet, se budou navzájem **lišit**. Tyto skladby se budou vytvářet pomocí zapsaných **pravidel**, kdy bude umožněno uživateli jednoduše a přehledně tato pravidla měnit a vytvořit si tak jakoukoli hudbu. Pomocí správně zapsaných pravidel bude aplikace schopná na určitý nástroj **zahrát jakoukoli skladbu**.

## Uživatelská specifikace
### Komponování hudby
Po spuštění aplikace Song Maker se zobrazí **okno**, které bude sloužit k ovládání aplikace uživatelem. V první části si uživatel **vybere hudební žánr**, který bude aplikace skládat a bude mít možnost si ho **pomocí formulářů nastavit**. Protože se žánry budou lišit, bude mít každý jiné nastavení. Nastavením je myšleno například nastavení **délky skladby** nebo **složitosti akordů**. Po kliknutí na tlačítko se **skladba zkomponuje**.

### Pravidla pro komponování hudby
Každý hudební žánr se bude skládat pomocí nějakých pravidel. Množině pravidel tvořící jeden žánr budu říkat **template**. Tato pravidla budou zapsána v textových souborech pomocí námi vytvořeného jazyka. Budou popisovat, co se ve kterou chvíli má hrát, jaký způsobem se určí rytmus a melodie a jak dlouhá skladba bude.

#### Interpret pravidel
Po kliknutí na tlačítko, které bude komponovat skladbu, se vlastně spustí interpret pravidel, který skladbu vytvoří.

#### Nastavení pravidel
Jak bylo uvedeno výše, uživateli bude umožněno si zvolený žánr nastavit. Bude to znamenat to, že do pravidel budou moci vstoupit uživatelem zvolené hodnoty a pravidla se jim budou moci přizpůsobit.

### Modifikace skladeb
Již zkomponovanou skladbu bude možné **transponovat** do jiných tónin a měnit její **rychlost**.

### Export
Skladbu bude možné exportovat do **MIDI** souboru a nechat si ji **přehrát**.

#### Dávkový export
Bude možné zautomatizovat komponování a exportování skladeb. Uživatel si bude moci nechat zkomponovat velké množství skladeb a pak z nich vybrat tu nejlepší.

### Vytváření nových pravidel (templates)
Aby psaní pravidel bylo více user-friendly, bude existovat další část programu, ve které uživatel bude moci **graficky nová pravidla vytvářet** a stará upravovat. Jednotlivá pravidla budou reprezentuvána graficky pomocí **barevných panelů** a pomocí barev, znázorněných **čar** a **najetím myši** na panel bude zřejmé, které s jakým souvisí. Tyto panely bude možné upravovat, odebírat a přidávat.
Cílem této části bude vytvořit takové rozhraní na vytváření nových templates, které dokáže ovládat uživatel, který nemá zkušenosti s programováním, a přitom bude možné vytvářet složité a obsáhlé templates.

#### Jazyk pravidel
Jak bylo uvedeno, pravidla budou v textových souborech zapsána pomocí určitého jazyka, který se posléze bude interpretovat. Kromě jiného bude tento jazyk obsahovat příkazy pro vytvoření konsonantních melodií, náhodného či dobře znějícího rytmu, bude umět *zmáčknout* či *pustit* pedál a další.

#### Vytvořená pravidla
Aplikace se dostane k uživateli s již předvytvořenými hudebními žánry (pravidly), kde bude zastoupen **waltz**, **ragtime**, **blues** a **polka**.

## Programátorská specifikace
Aplikace bude napsána v *C# .NET Framework 4.5*. Bude optimalizována pro platformu Windows.

### MIDI
K vytváření midi souborů využiji volnou knihovnu **Sanford.Multimedia.Midi**.

### Multithreading
Při interpretaci pravidel a při vytváření skladeb UI nezamrzne, nýbrž se interpreter spustí v novém vlákně. Vytváření skladby bude možné přerušit.
