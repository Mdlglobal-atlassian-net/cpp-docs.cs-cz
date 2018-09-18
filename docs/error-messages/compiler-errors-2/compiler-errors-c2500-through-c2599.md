---
title: Chyby kompilátoru C2500 až C2599 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/17/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2501
- C2508
- C2515
- C2519
- C2520
- C2522
- C2525
- C2527
- C2536
- C2538
- C2539
- C2546
- C2547
- C2559
- C2560
- C2564
- C2565
- C2576
- C2578
- C2580
- C2590
- C2591
- C2595
- C2596
helpviewer_keywords:
- C2501
- C2508
- C2515
- C2519
- C2520
- C2522
- C2525
- C2527
- C2536
- C2538
- C2539
- C2546
- C2547
- C2559
- C2560
- C2564
- C2565
- C2576
- C2578
- C2580
- C2590
- C2591
- C2595
- C2596
dev_langs:
- C++
ms.assetid: a869aaed-e9f6-49e3-b273-00ea7f45bed7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c54a35c50516b541ee6e76aea3c0b4b3147e5a1b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46017769"
---
# <a name="compiler-errors-c2500-through-c2599"></a>Chyby kompilátoru C2500 až C2599

Články v této části dokumentace vysvětlují podmnožinu chybové zprávy, které jsou generovány kompilátorem.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Chybové zprávy

|Chyba|Zpráva|
|-----------|-------------|
|[Chyba kompilátoru C2500](compiler-error-C2500.md)|"*identifier1*": "*identifier2*' je již přímé základní třídy.|
|C2501 chyby kompilátoru|"*identifikátor*": "__declspec (*specifikátor*) se může používat jedině pro struktury, sjednocení, třídy nebo členy bez znaménka bitových polí|
|[Chyba kompilátoru C2502](compiler-error-C2502.md)|"*identifikátor*': moc velký počet modifikátorů přístupu základní třídy|
|[Chyba kompilátoru C2503](compiler-error-C2503.md)|"*třídy*': základní třídy nemůžou obsahovat pole s nulovou velikostí|
|[Chyba kompilátoru C2504](compiler-error-C2504.md)|"*třídy*': základní třída undefined|
|[Chyba kompilátoru C2505](compiler-error-C2505.md)|"*symbol*": "__declspec (*specifikátor*) se dá používat jedině pro deklarace nebo definice globálních objektů nebo statických datových členů|
|[Chyba kompilátoru C2506](compiler-error-C2506.md)|"*člen*": "__declspec (*specifikátor*)' nelze použít pro tento symbol|
|[Chyba kompilátoru C2507](compiler-error-C2507.md)|"*identifikátor*': moc virtuálních modifikátorů základní třídy|
|C2508 chyby kompilátoru|"*identifikátor*": "__declspec (*specifier1*)" se nedá kombinovat s "__declspec (*specifier2*).|
|[Chyba kompilátoru C2509](compiler-error-C2509.md)|"*identifikátor*': členská funkce není deklarovaná"*třídy*.|
|[Chyba kompilátoru C2510](compiler-error-C2510.md)|"*identifikátor*': Levá strana '::' musí být třída/struktura/sjednocení|
|[Chyba kompilátoru C2511](compiler-error-C2511.md)|"*identifikátor*': členská funkce, nebyl nalezen v přetížení"*třídy*"|
|[Chyba kompilátoru C2512](compiler-error-C2512.md)|"*identifikátor*': žádný odpovídající konstruktor default k dispozici|
|[Chyba kompilátoru C2513](compiler-error-C2513.md)|' * typu ': deklarovaná žádná proměnná před '='|
|[Chyba kompilátoru C2514](compiler-error-C2514.md)|"*třídy*': Třída nemá žádné konstruktory|
|C2515 chyby kompilátoru|"*identifikátor*": "vtguard" může používat jedině pro definice nebo deklarace tříd|
|[Chyba kompilátoru C2516](compiler-error-C2516.md)|"*třídy*': není platný základní třídy|
|[Chyba kompilátoru C2517](compiler-error-C2517.md)|"*identifikátor*': napravo od '::' není definován|
|[Chyba kompilátoru C2518](compiler-error-C2518.md)|klíčové slovo '*– klíčové slovo*"ignoruje neplatné v seznamu základních tříd|
|C2519 chyby kompilátoru|"*identifikátor*': atributy WinRT můžou obsahovat jenom veřejné pole|
|C2520 chyby kompilátoru|"*třídy*': není k dispozici pro implicitní převod neexplicitní konstruktor|
|[Chyba kompilátoru C2521](compiler-error-C2521.md)|destruktor nebo finalizační metodu nepřijímá žádné argumenty|
|C2522 chyby kompilátoru|"*identifikátor*': identifikátor přetížení nejde v"*identifier1*"jak se už vyskytuje na"*identifier2*.|
|[Chyba kompilátoru C2523](compiler-error-C2523.md)|"*třídy*:: ~*identifikátor*': Neshoda značek destruktor nebo finalizační metodu|
|[Chyba kompilátoru C2524](compiler-error-C2524.md)|"*identifikátor*': destruktor nebo finalizační metody musí mít seznam parametrů void.|
|C2525 chyby kompilátoru|"*identifikátor*': parametr"*identifier1*"má název"*identifier2*"pro základní funkce a musí být shoda v publikované implementaci|
|[Chyba kompilátoru C2526](compiler-error-C2526.md)|"*identifier1*': funkce propojení C nemůže vracet třídu C++*identifier2*.|
|C2527 chyby kompilátoru|"*identifikátor*': DefaultOverload nejde zadat u obou"*function1*"a"*function2*". Odeberte jednu specifikaci nebo přejmenujte funkci při implementaci|
|[Chyba kompilátoru C2528](compiler-error-C2528.md)|"*identifikátor*': ukazatel na odkaz je neplatný|
|[Chyba kompilátoru C2529](compiler-error-C2529.md)|"*identifikátor*': odkaz na odkaz je neplatný|
|[Chyba kompilátoru C2530](compiler-error-C2530.md)|"*identifikátor*': odkazy musí být inicializován.|
|[Chyba kompilátoru C2531](compiler-error-C2531.md)|"*identifikátor*': odkaz na neplatné bitové pole|
|[Chyba kompilátoru C2532](compiler-error-C2532.md)|"*identifikátor*': Neplatný modifikátor pro odkaz|
|[Chyba kompilátoru C2533](compiler-error-C2533.md)|"*identifikátor*': konstruktory není povolený návratový typ.|
|[Chyba kompilátoru C2534](compiler-error-C2534.md)|"*identifikátor*': konstruktor nemůže vracet hodnotu.|
|[Chyba kompilátoru C2535](compiler-error-C2535.md)|"*identifikátor*': členská funkce, které jsou již definována nebo deklarována|
|C2536 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C2537](compiler-error-C2537.md)|"*specifikátor*': Neplatná specifikace propojení|
|C2538 chyby kompilátoru|Zastaralé.|
|C2539 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C2540](compiler-error-C2540.md)|nekonstantní výraz jako hranice pole|
|[Chyba kompilátoru C2541](compiler-error-C2541.md)|"*identifikátor*': nelze odstranit objekty, které nejsou ukazatele|
|[Chyba kompilátoru C2542](compiler-error-C2542.md)|"*identifikátor*': objekt třídy nemá žádný konstruktor pro inicializaci|
|[Chyba kompilátoru C2543](compiler-error-C2543.md)|byl očekáván ']' pro operátor '[']|
|[Chyba kompilátoru C2544](compiler-error-C2544.md)|byl očekáván ')' pro operátor '().|
|[Chyba kompilátoru C2545](compiler-error-C2545.md)|"*operátor*': Nelze najít přetížený operátor|
|C2546 chyby kompilátoru|"*identifikátor*': když je typ definován ve PIA a no-PIA, musí se nejdřív odkazovat PIA|
|C2547 chyby kompilátoru|"*identifikátor*': všechny parametry publikované metody musí být explicitně pojmenované v deklaraci|
|[Chyba kompilátoru C2548](compiler-error-C2548.md)|"*funkce*': Chybí výchozí parametr parametru *parametr*|
|[Chyba kompilátoru C2549](compiler-error-C2549.md)|uživatelem definovaný převod nemůže specifikovat návratový typ.|
|[Chyba kompilátoru C2550](compiler-error-C2550.md)|"*identifikátor*': seznamy inicializátorů konstruktorů jsou povolené jenom pro definice konstruktorů|
|[Chyba kompilátoru C2551](compiler-error-C2551.md)|"void *" typ vyžaduje explicitní přetypování.|
|[Chyba kompilátoru C2552](compiler-error-C2552.md)|"*identifikátor*': neagregované objekty nejde inicializovat seznamem inicializátorů|
|[Chyba kompilátoru C2553](compiler-error-C2553.md)|"*typ* *derived_class*::*funkce*': přepisující virtuální funkce, návratový typ se liší od"*typ* *base_ Třída*::*funkce*.|
|[Chyba kompilátoru C2555](compiler-error-C2555.md)|"*derived_class*::*funkce*': přepisující virtuální funkce návratový typ se liší a není kovariantem z:"*$base_class*::*funkce*'|
|[Chyba kompilátoru C2556](compiler-error-C2556.md)|"*type1* *třídy*::*funkce*': funkce přetížení se liší pouze o návratový typ z"*type2* *třídy*::*funkce*.|
|[Chyba kompilátoru C2557](compiler-error-C2557.md)|"*identifikátor*': soukromým a chráněným členům nelze inicializovat bez konstruktoru|
|[Chyba kompilátoru C2558](compiler-error-C2558.md)|třídy*třídy*': není k dispozici konstruktor kopie nebo je kopírovací konstuktor je deklarovaný jako explicit.|
|C2559 chyby kompilátoru|"*identifikátor*': nejde přetížit členskou funkci bez kvalifikátoru ref s členskou funkcí s kvalifikátorem ref|
|C2560 chyby kompilátoru|"*identifikátor*': nejde přetížit členskou funkci s kvalifikátorem ref s členskou funkcí bez kvalifikátoru ref|
|[Chyba kompilátoru C2561](compiler-error-C2561.md)|"*funkce*': funkce musí vracet hodnotu|
|[Chyba kompilátoru C2562](compiler-error-C2562.md)|"*funkce*": "void" funkce vrací hodnotu|
|[Chyba kompilátoru C2563](compiler-error-C2563.md)|Neshoda v seznamu formálních parametrů|
|C2564 chyby kompilátoru|Zastaralé.|
|C2565 chyby kompilátoru|"*identifikátor*': kvalifikátor ref není pro konstruktory/destruktory platný|
|[Chyba kompilátoru C2566](compiler-error-C2566.md)|přetížené funkce v podmíněných výrazech|
|[Chyba kompilátoru C2567](compiler-error-C2567.md)|nejde otevřít metadata v: "*filename*", *possible_reason*|
|[Chyba kompilátoru C2568](compiler-error-C2568.md)|"*identifikátor*': nejde vyřešit přetížení funkce|
|[Chyba kompilátoru C2569](compiler-error-C2569.md)|"*identifikátor*': výčet/sjednocení nejde použít jako základní třídu|
|[Chyba kompilátoru C2570](compiler-error-C2570.md)|"*identifikátor*': sjednocení nemůže mít základní třídy|
|[Chyba kompilátoru C2571](compiler-error-C2571.md)|"*identifikátor*': virtuální funkce nemůže být sjednocení"*sjednocení*.|
|[Chyba kompilátoru C2572](compiler-error-C2572.md)|"*funkce*': předefinování výchozího argumentu: Parametr *číslo*|
|[Chyba kompilátoru C2573](compiler-error-C2573.md)|"*třídy*': nelze odstranit ukazatele na objekty tohoto typu; Třída nemá žádné přetížení bez umístění pro: operator delete". Použití:: odstranit, nebo do třídy přidat 'operator delete(void*)'|
|[Chyba kompilátoru C2574](compiler-error-C2574.md)|"*destruktor*': nemůže být deklarované jako statické.|
|[Chyba kompilátoru C2575](compiler-error-C2575.md)|"*identifikátor*': jenom členské funkce a třídy Base můžou být virtuální|
|C2576 chyby kompilátoru|"*identifikátor*': Nelze zavést novou virtuální metodu jako 'veřejné'. Zvažte učinění nevirtuální metodu nebo změňte přístupnost na "vnitřní" nebo "protected private.|
|[Chyba kompilátoru C2577](compiler-error-C2577.md)|"*identifikátor*': destruktor nebo finalizační metoda nemůže mít návratový typ.|
|C2578 chyby kompilátoru|"*třídy*': typ nemůže mít"protected"nebo chráněné veřejný konstruktor|
|[Chyba kompilátoru C2579](compiler-error-C2579.md)|nejde přeložit typ *typ* (*posun*). Očekává se v: *název souboru*|
|C2580 chyby kompilátoru|"*identifikátor*': není povoleno více verzí výchozích speciálních členských funkcí|
|[Chyba kompilátoru C2581](compiler-error-C2581.md)|"*typ*': statické" operátor = "funkce je neplatný|
|[Chyba kompilátoru C2582](compiler-error-C2582.md)|"operátor *operátor*"funkce není k dispozici v"*typ*"|
|[Chyba kompilátoru C2583](compiler-error-C2583.md)|"*identifikátor*": "const/volatile: 'this' ukazatel je neplatný pro konstruktory/destruktory|
|[Chyba kompilátoru C2584](compiler-error-C2584.md)|"*třídy*": přímou základní "*base_class2*" je nedostupná; už třídou base '*base_class1*"|
|[Chyba kompilátoru C2585](compiler-error-C2585.md)|explicitní převod na "*typ*' je nejednoznačný|
|[Chyba kompilátoru C2586](compiler-error-C2586.md)|nesprávný uživatelsky definovaný převod syntaxe: neplatné indirekce|
|[Chyba kompilátoru C2587](compiler-error-C2587.md)|"*identifikátor*': Neplatné použití lokální proměnné jako výchozího parametru|
|[Chyba kompilátoru C2588](compiler-error-C2588.md)|':: ~*identifikátor*': Neplatná globální destruktor nebo finalizační metodu|
|[Chyba kompilátoru C2589](compiler-error-C2589.md)|'*identifikátor*': neplatný token na pravé straně '::'|
|C2590 chyby kompilátoru|"*identifikátor*': pouze konstrukt může mít seznam inicializátorů base/member|
|C2591 chyby kompilátoru|ExclusiveTo nemůže použít '*typ*' jako argument. Pouze "třídy ref class' je platným argumentem|
|[Chyba kompilátoru C2592](compiler-error-C2592.md)|"*třídy*": "*base_class2*"je zděděno od"*base_class1*" a nelze znovu zadat|
|[Chyba kompilátoru C2593](compiler-error-C2593.md)|' operator *identifikátor*' je nejednoznačný|
|[Chyba kompilátoru C2594](compiler-error-C2594.md)|"*operátor*': nejednoznačné převody z:"*type1*"do"*type2*"|
|C2595 chyby kompilátoru|"*identifikátor*" typ atributu WinRT A musí být zapečetěný.|
|C2596 chyby kompilátoru|"*identifikátor*" pole atributu WinRT A může být pouze 'public enum class', "int", "unsigned int", 'bool', "Platform::type –", "Platform::String" nebo "Windows Windows::Foundation:: HResult.|
|[Chyba kompilátoru C2597](compiler-error-C2597.md)|Neplatný odkaz na Nestatický člen "*identifikátor*.|
|[Chyba kompilátoru C2598](compiler-error-C2598.md)|Specifikace propojení musí být v globálním oboru|
|[Chyba kompilátoru C2599](compiler-error-C2599.md)|"*identifikátor*': Dopředná deklarace výčtu spravované/WinRT není povolený.|