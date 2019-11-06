---
title: 'C++Přehledy sestavení: referenční informace o zobrazeních analyzátoru výkonu systému Windows'
description: Referenční informace C++ o zobrazeních přehledů sestavení dostupných v analyzátoru výkonu Windows
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: e574e7ef4c1b4c5832785d69dbc90ba043cf996a
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73633089"
---
# <a name="c-build-insights-windows-performance-analyzer-views-reference"></a>C++Přehledy sestavení: referenční informace o zobrazeních analyzátoru výkonu systému Windows

::: moniker range="<=vs-2017"

Nástroje C++ pro tvorbu sestav jsou k dispozici v aplikaci Visual Studio 2019. Chcete-li zobrazit dokumentaci k této verzi, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2019.

::: moniker-end
::: moniker range="vs-2019"

Tento článek poskytuje podrobné informace o všech zobrazeních přehledů C++ sestavení dostupných v nástroji Windows Performance Analyzer (WPA). Pomocí této stránky můžete najít:

- Popis sloupce dat; ani
- dostupná přednastavení pro každé zobrazení, včetně zamýšleného použití a preferovaného režimu zobrazení.

Pokud s protokolem WPA začínáte, doporučujeme si nejprve seznámit se [základy WPA pro C++ Build Insights](wpa-basics.md).

## <a name="build-explorer"></a>Průzkumník sestavení

Zobrazení Průzkumníka sestavení se používá pro:

- Diagnostikujte problémy paralelismus,
- Určete, zda je čas sestavení ovládán analýzou, generováním kódu nebo propojením a
- Identifikujte kritické body a neobvykle dlouhé aktivity sestavení.

### <a name="build-explorer-view-data-columns"></a>Sloupce dat zobrazení Průzkumníka sestavení

| Název sloupce | Popis |
|-|-|
| BuildTimelineDescription | Textový popis časové osy, na které se aktuální aktivita nebo vlastnost vyskytuje. |
| BuildTimelineId          | Identifikátor založený na nule pro časovou osu, na které se aktuální aktivita nebo vlastnost vyskytuje. |
| Součást                | Komponenta, která je zkompilována nebo propojena po vygenerování aktuální události. Hodnota tohoto sloupce je *\<\>informace o volání* , pokud k této události není přidružena žádná komponenta. X je jedinečný číselný identifikátor pro vyvolání prováděný v době, kdy byla událost vygenerována. Tento identifikátor je stejný jako ten, který je ve sloupci InvocationId pro tuto událost. |
| Výpočtu                    | Počet aktivit nebo vlastností reprezentovaných tímto řádkem dat. Tato hodnota je vždy 1 a je užitečná pouze při agregačních scénářích, pokud je seskupeno více řádků. |
| ExclusiveCPUTime         | Množství času procesoru v milisekundách, které používá tato aktivita. Doba strávená podřízenými aktivitami není v této množství zahrnutá. |
| ExclusiveDuration        | Doba trvání aktivity milisekundy. Doba trvání podřízených aktivit není v této množství zahrnutá. |
| InclusiveCPUTime         | Množství času procesoru v milisekundách používaných touto aktivitou a všemi podřízenými aktivitami. |
| InclusiveDuration        | Doba trvání milisekundy této aktivity, včetně všech podřízených aktivit. |
| InvocationDescription    | Textový popis vyvolání, ve kterém došlo k této události Popis zahrnuje, zda se jednalo o *CL. exe* nebo *Link. exe*, a jedinečný číselný identifikátor vyvolání. Pokud je to možné, zahrnuje úplnou cestu k komponentě zkompilované nebo propojené během vyvolání. Pro vyvolání, které nevytvářejí žádnou komponentu, nebo pro ty, které sestavují více komponent, je cesta prázdná. Identifikátor vyvolání je stejný jako ten ve sloupci InvocationId. |
| InvocationId             | Jedinečný číselný identifikátor vyvolání, ve kterém došlo k této události. |
| Name                     | Název aktivity nebo vlastnosti reprezentované touto událostí. |
| Interval                     | Časové razítko, které určuje, kdy došlo k události. |
| Nástroj                     | Nástroj, který se provádí v případě výskytu této události. Hodnota tohoto sloupce je buď CL, nebo odkaz. |
| Typ                     | Typ aktuální události Tato hodnota je buď aktivita, nebo vlastnost. |
| Hodnota                    | Pokud je aktuální událost vlastnost, tento sloupec obsahuje hodnotu. Pokud aktuální událost je aktivita, zůstane tento sloupec prázdný. |

### <a name="build-explorer-view-presets"></a>Předvolby zobrazení Průzkumníka sestavení

| Název předvolby           | Upřednostňovaný režim zobrazení | Jak používat |
|-----------------------|---------------------|------------|
| Statistika aktivity   | Graf nebo tabulka       | Pomocí této předvolby můžete zobrazit agregované statistiky pro všechny aktivity Průzkumníka sestavení. V režimu tabulky sdělte na první pohled, zda je sestavení ovládáno analýzou, generováním kódu nebo linkerem. Agregované doby trvání každé aktivity jsou seřazeny v sestupném pořadí. Rozjděte si hlavní uzel, abyste mohli snadno najít, která volání pro tyto hlavní aktivity vybírají nejvíce času. Pokud chcete, můžete upravit nastavení WPA tak, aby zobrazovalo průměry nebo jiné typy agregací. V režimu grafu si přečtěte, kdy je každá aktivita aktivní během sestavení. |
| Vyvolání           | Zapisovací               | Posuňte se dolů na seznam vyvolání v zobrazení grafu seřazené podle času spuštění. Můžete ji použít společně s využitím procesoru (vzorkování) k vyhledání vyvolání, která se zarovnají s nízkými zónami využití procesoru. Detekuje problémy paralelismu. |
| Vlastnosti vyvolání | Tabulka               | Rychle Najděte klíčové informace o daném kompilátoru nebo vyvolání linkeru. Určete jeho verzi, pracovní adresář nebo úplný příkazový řádek, který se používá k vyvolání. |
| Časové osy             | Zapisovací               | Podívejte se na pruhový graf, jak se vaše sestavení paralelně vytvořilo. Identifikujte problémy paralelismu a kritická místa na první pohled. Nakonfigurujte WPA pro přiřazení různých významů k pruhům podle vašich potřeb. Vyberte popisy volání jako poslední seskupený sloupec pro zobrazení barevně kódovaného pruhového grafu pro všechna vaše volání. Pomůže vám rychle identifikovat časově náročné culprits. Pak přiblížíte a zvolte název aktivity jako poslední seskupený sloupec, abyste viděli nejdelší části. |

## <a name="files"></a>Soubory

Zobrazení soubory se používá pro:

- Určete, která záhlaví se budou často zobrazovat a
- pomůžete se rozhodnout, co zahrnout do předkompilované hlavičky (PCH).

### <a name="files-view-data-columns"></a>Sloupce dat zobrazení souborů

| Název sloupce              | Popis |
|--------------------------|-------------|
| Název aktivity ActivityName             | Aktivita probíhají v době, kdy byla tato událost souboru vyvolána. V současné době se tato hodnota vždy *analyzuje*. |
| BuildTimelineDescription | * |
| BuildTimelineId          | * |
| Součást                | * |
| Výpočtu                    | * |
| Úrovní                    | Pozice s nulovým základem ve stromu zahrnutí, ve kterém je tento soubor nalezen. Počítání začíná v kořenu include stromu. Hodnota 0 obvykle odpovídá souboru. c/. cpp. |
| ExclusiveDuration        | * |
| IncludedBy               | Úplná cesta k souboru, který zahrnoval aktuální soubor. |
| IncludedPath             | Úplná cesta k aktuálnímu souboru. |
| InclusiveDuration        | * |
| InvocationId             | * |
| Spuštění                | Časové razítko, které představuje čas, kdy byla vyvolána událost aktuálního souboru. |
| Nástroj                     | * |

\* hodnota tohoto sloupce je stejná jako v zobrazení [Průzkumník sestavení](#build-explorer-view-data-columns) .

### <a name="files-view-presets"></a>Předvolby zobrazení souborů

| Název předvolby | Upřednostňovaný režim zobrazení | Jak používat |
|-------------|---------------------|------------|
| týkají  | Tabulka               | Podívejte se na seznam v sestupném pořadí, abyste viděli, které soubory mají nejvyšší agregovanou dobu analýzy. Tyto informace slouží k tomu, abyste pomohli restrukturovat hlavičky nebo rozhodnout, co se má do souboru PCH zahrnout. |

## <a name="functions"></a>Funkce

Zobrazení Functions (funkce) se používá k identifikaci funkcí s nadměrným dlouhým časem generování kódu.

### <a name="functions-view-data-columns"></a>Sloupce dat zobrazení funkcí

| Název sloupce              | Popis |
|--------------------------|-------------|
| Název aktivity ActivityName             | Aktivita probíhající v době, kdy byla tato událost funkce vyvolána. V současné době je tato hodnota vždy *strategii*. |
| BuildTimelineDescription | * |
| BuildTimelineId          | * |
| Součást                | * |
| Výpočtu                    | * |
| úkolu                 | Doba trvání aktivity generování kódu pro tuto funkci. |
| functionName             | Název funkce, která projde generování kódu. |
| InvocationId             | * |
| Spuštění                | Časové razítko, které představuje, kdy byla vyvolána událost aktuální funkce. |
| Nástroj                     | * |

\* hodnota tohoto sloupce je stejná jako v zobrazení [Průzkumník sestavení](#build-explorer-view-data-columns) .

### <a name="functions-view-presets"></a>Předvolby zobrazení funkcí

| Název předvolby | Upřednostňovaný režim zobrazení | Jak používat |
|-------------|---------------------|------------|
| týkají  | Tabulka               | Podívejte se na seznam v sestupném pořadí, abyste viděli, které funkce měly nejvyšší agregovaný čas generování kódu. Můžou to být doporučení, kde váš kód přebírá klíčové slovo **__forceinline** , nebo že některé funkce můžou být moc velké. |
| Časové osy   | Zapisovací               | Podívejte se na tento pruhový graf, kde zjistíte umístění a dobu trvání funkcí, které se vygenerují nejvíce času. Podívejte se, jestli jsou v zobrazení Průzkumníka sestavení zarovnané na kritická místa. Pokud to uděláte, proveďte příslušnou akci, abyste snížili čas generování kódu a využili své časy sestavení. |

## <a name="see-also"></a>Viz také:

[Začínáme se C++ sestavami Build Insights](get-started-with-cpp-build-insights.md)\
[referenční\ vcperf. exe](vcperf-reference.md)
[Základy Windows Performance Analyzer](wpa-basics.md)\
[Analyzátor výkonu systému Windows](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end
