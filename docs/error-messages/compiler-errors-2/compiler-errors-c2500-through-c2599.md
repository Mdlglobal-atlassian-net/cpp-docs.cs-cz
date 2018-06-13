---
title: C2500 chyby kompilátoru prostřednictvím C2599 | Microsoft Docs
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
ms.openlocfilehash: 994f29009294e6b49851a817a5872fcaa122b153
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33284261"
---
# <a name="compiler-errors-c2500-through-c2599"></a>C2500 chyby kompilátoru prostřednictvím C2599

Články v této části dokumentace vysvětlují podmnožinu chybové zprávy, které jsou generované kompilátorem.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Chybové zprávy

|Chyba|Zpráva|
|-----------|-------------|
|[Chyba kompilátoru C2500](compiler-error-C2500.md)|'*identifier1*': '*identifier2*' je již přímé základní třída|
|C2501 chyby kompilátoru|'*identifikátor*': ' __declspec (*specifikátor*), lze použít pouze pro struktury, sjednocení, třídy nebo bez znaménka bitová pole členů|
|[Chyba kompilátoru C2502](compiler-error-C2502.md)|'*identifikátor*': příliš mnoho modifikátory přístupu na základní třídě.|
|[Chyba kompilátoru C2503](compiler-error-C2503.md)|'*třída*': základní třídy, nemůže obsahovat pole s nulovou velikostí|
|[Chyba kompilátoru C2504](compiler-error-C2504.md)|'*třída*': základní třída není definována|
|[Chyba kompilátoru C2505](compiler-error-C2505.md)|'*symbol*': ' __declspec (*specifikátor*), můžete použít jenom pro deklarace nebo definice globální objekty nebo členy statických dat|
|[Chyba kompilátoru C2506](compiler-error-C2506.md)|'*člen*': ' __declspec (*specifikátor*), nelze použít pro tento symbol|
|[Chyba kompilátoru C2507](compiler-error-C2507.md)|'*identifikátor*': příliš mnoho virtuálních modifikátory na základní třídě.|
|C2508 chyby kompilátoru|'*identifikátor*': ' __declspec (*specifier1*), nelze kombinovat s ' __declspec (*specifier2*).|
|[Chyba kompilátoru C2509](compiler-error-C2509.md)|'*identifikátor*': členská funkce není deklarován v '*– třída*.|
|[Chyba kompilátoru C2510](compiler-error-C2510.md)|'*identifikátor*': nalevo od '::' musí být třída nebo struktura/sjednocení|
|[Chyba kompilátoru C2511](compiler-error-C2511.md)|'*identifikátor*': přetížený – členská funkce nebyla nalezena v '*– třída*.|
|[Chyba kompilátoru C2512](compiler-error-C2512.md)|'*identifikátor*': žádný odpovídající výchozí konstruktor k dispozici|
|[Chyba kompilátoru C2513](compiler-error-C2513.md)|' * typ ': žádné proměnné deklarovány před '='|
|[Chyba kompilátoru C2514](compiler-error-C2514.md)|'*třída*': Třída nemá žádné konstruktory|
|C2515 chyby kompilátoru|'*identifikátor*': 'vtguard' lze použít pouze na deklaracích třídy nebo definice|
|[Chyba kompilátoru C2516](compiler-error-C2516.md)|'*třída*': není právní základní třída|
|[Chyba kompilátoru C2517](compiler-error-C2517.md)|'*identifikátor*': napravo od '::' není definován|
|[Chyba kompilátoru C2518](compiler-error-C2518.md)|– klíčové slovo '*– klíčové slovo*se v seznamu základní třída neplatné; ignorováno|
|C2519 chyby kompilátoru|'*identifikátor*': WinRT atributy mohou obsahovat pouze veřejná pole|
|C2520 chyby kompilátoru|'*třída*': žádný jiný explicitní konstruktor, který je k dispozici pro implicitní převod|
|[Chyba kompilátoru C2521](compiler-error-C2521.md)|destruktor/finalizační metodu nepřijímá žádné argumenty|
|C2522 chyby kompilátoru|'*identifikátor*': přetížení identifikátoru nelze použít na '*identifier1*, jako jsou již zadány na'*identifier2*.|
|[Chyba kompilátoru C2523](compiler-error-C2523.md)|'*třída*:: ~*identifikátor*': Neshoda značky destruktor/finalizační metodu|
|[Chyba kompilátoru C2524](compiler-error-C2524.md)|'*identifikátor*': destruktor/finalizační metodu musí mít seznam parametrů, void.|
|C2525 chyby kompilátoru|'*identifikátor*': Parametr '*identifier1*má název*identifier2*se na základní funkce a musí odpovídat v publikované implementaci|
|[Chyba kompilátoru C2526](compiler-error-C2526.md)|'*identifier1*': C propojení funkce nemůže vrátit třídami C++*identifier2*.|
|C2527 chyby kompilátoru|'*identifikátor*': DefaultOverload nelze zadat obě '*function1*'a'*funkce2*'. Jeden odeberte nebo přejmenujte funkce během implementace|
|[Chyba kompilátoru C2528](compiler-error-C2528.md)|'*identifikátor*': ukazatel na odkaz je neplatný|
|[Chyba kompilátoru C2529](compiler-error-C2529.md)|'*identifikátor*': na odkaz je neplatný|
|[Chyba kompilátoru C2530](compiler-error-C2530.md)|'*identifikátor*': odkazy musí být inicializován.|
|[Chyba kompilátoru C2531](compiler-error-C2531.md)|'*identifikátor*': odkaz na trochu neplatné pole|
|[Chyba kompilátoru C2532](compiler-error-C2532.md)|'*identifikátor*': Neplatný modifikátor pro – referenční informace|
|[Chyba kompilátoru C2533](compiler-error-C2533.md)|'*identifikátor*': konstruktory nejsou povoleny návratový typ.|
|[Chyba kompilátoru C2534](compiler-error-C2534.md)|'*identifikátor*': konstruktor nemůže vrátit hodnotu|
|[Chyba kompilátoru C2535](compiler-error-C2535.md)|'*identifikátor*': členská funkce již definována nebo deklarovaný|
|C2536 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C2537](compiler-error-C2537.md)|'*specifikátor*': specifikace neplatný propojení|
|C2538 chyby kompilátoru|Zastaralé.|
|C2539 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C2540](compiler-error-C2540.md)|není konstantní výraz jako pole vázán|
|[Chyba kompilátoru C2541](compiler-error-C2541.md)|'*identifikátor*': nelze odstranit objekty, které nejsou ukazatele|
|[Chyba kompilátoru C2542](compiler-error-C2542.md)|'*identifikátor*': objektu třídy nemá žádný konstruktor pro inicializaci|
|[Chyba kompilátoru C2543](compiler-error-C2543.md)|Očekávaný ']' pro operátor '[']|
|[Chyba kompilátoru C2544](compiler-error-C2544.md)|Očekávaný ')' pro operátor '().|
|[Chyba kompilátoru C2545](compiler-error-C2545.md)|'*operátor*': Nelze najít přetížený – operátor|
|C2546 chyby kompilátoru|'*identifikátor*': při typ je definován v PIA a ne PIA nejprve musí odkazovat PIA –|
|C2547 chyby kompilátoru|'*identifikátor*': všechny parametry metody publikovanou musí být explicitně s názvem v prohlášení o|
|[Chyba kompilátoru C2548](compiler-error-C2548.md)|'*funkce*': Chybějící výchozí parametr pro parametr *parametr*|
|[Chyba kompilátoru C2549](compiler-error-C2549.md)|uživatelem definované převod nelze zadat návratový typ.|
|[Chyba kompilátoru C2550](compiler-error-C2550.md)|'*identifikátor*': konstruktor inicializační seznamy jsou povoleny pouze na definice – konstruktor|
|[Chyba kompilátoru C2551](compiler-error-C2551.md)|' void *' typ musí explicitní přetypování|
|[Chyba kompilátoru C2552](compiler-error-C2552.md)|'*identifikátor*': neagregované položky nemůže být inicializovaný s inicializačním seznam|
|[Chyba kompilátoru C2553](compiler-error-C2553.md)|'*typ* *derived_class*::*funkce*': přepisování virtuální funkce návratový typ se liší od '*typ* *base_ Třída*::*funkce*.|
|[Chyba kompilátoru C2555](compiler-error-C2555.md)|'*derived_class*::*funkce*': přepisování virtuální funkce návratový typ se liší a není kovariantní z '*base_class*::*funkce*'|
|[Chyba kompilátoru C2556](compiler-error-C2556.md)|'*type1* *– třída*::*funkce*': přetížené funkce se liší pouze o návratový typ z '*type2* *–Třída*::*funkce*.|
|[Chyba kompilátoru C2557](compiler-error-C2557.md)|'*identifikátor*': privátní a chráněné členy nelze inicializovat bez konstruktor|
|[Chyba kompilátoru C2558](compiler-error-C2558.md)|třída*třída*': žádné kopírovacího konstruktoru, které jsou k dispozici nebo kopírovací konstruktor je deklarován 'explicitní.|
|C2559 chyby kompilátoru|'*identifikátor*': nelze přetížení členské funkce bez ref kvalifikátor s s ref kvalifikátor členské funkce|
|C2560 chyby kompilátoru|'*identifikátor*': nelze přetížení členské funkce s ref kvalifikátor s bez ref kvalifikátor členské funkce|
|[Chyba kompilátoru C2561](compiler-error-C2561.md)|'*funkce*': funkce musí vrátit hodnotu|
|[Chyba kompilátoru C2562](compiler-error-C2562.md)|'*funkce*': 'void' funkce návrat hodnoty|
|[Chyba kompilátoru C2563](compiler-error-C2563.md)|Neshoda v seznamu formální parametr|
|C2564 chyby kompilátoru|Zastaralé.|
|C2565 chyby kompilátoru|'*identifikátor*': ref kvalifikátor je neplatný pro konstruktory/destruktorů|
|[Chyba kompilátoru C2566](compiler-error-C2566.md)|přetížené funkce podmíněného výrazu|
|[Chyba kompilátoru C2567](compiler-error-C2567.md)|Nelze otevřít metadata v '*filename*', *possible_reason*|
|[Chyba kompilátoru C2568](compiler-error-C2568.md)|'*identifikátor*': nelze vyřešit přetížení funkce|
|[Chyba kompilátoru C2569](compiler-error-C2569.md)|'*identifikátor*': výčtu nebo union nelze použít jako základní třída|
|[Chyba kompilátoru C2570](compiler-error-C2570.md)|'*identifikátor*': union nemohou mít základní třídy|
|[Chyba kompilátoru C2571](compiler-error-C2571.md)|'*identifikátor*': virtuální funkce nelze v sjednocení '*– typ union*.|
|[Chyba kompilátoru C2572](compiler-error-C2572.md)|'*funkce*': předefinování výchozí argument: Parametr *číslo*|
|[Chyba kompilátoru C2573](compiler-error-C2573.md)|'*třída*': nelze odstranit ukazatelé na objekty tohoto typu; Třída nemá žádné přetížení jiné umístění pro 'odstranit operátor'. Použití:: odstranit nebo přidejte do třídy 'delete(void*) operátor.|
|[Chyba kompilátoru C2574](compiler-error-C2574.md)|'*destruktor*': nelze deklarovat statickou|
|[Chyba kompilátoru C2575](compiler-error-C2575.md)|'*identifikátor*': pouze členských funkcí a databáze, které mohou být virtuální|
|C2576 chyby kompilátoru|'*identifikátor*': Nelze zavést nové virtuální metody jako 'veřejné'. Zvažte nevirtuálních metodu nebo změnit usnadnění přístupu k "interní" nebo "chráněné privátní"|
|[Chyba kompilátoru C2577](compiler-error-C2577.md)|'*identifikátor*': destruktor/finalizační metodu nemůže mít typ vrácené hodnoty.|
|C2578 chyby kompilátoru|'*třída*': typ nemůže mít "chráněné" nebo chráněné veřejný konstruktor|
|[Chyba kompilátoru C2579](compiler-error-C2579.md)|nelze vyřešit typ *typ* (*posun*). Je očekávána v *filename*|
|C2580 chyby kompilátoru|'*identifikátor*': více verzí uvedena speciální členské funkce nejsou povoleny.|
|[Chyba kompilátoru C2581](compiler-error-C2581.md)|'*typ*': statické, operátor =' funkce je neplatný|
|[Chyba kompilátoru C2582](compiler-error-C2582.md)|"operátor *operátor*'funkce je k dispozici v'*typu*.|
|[Chyba kompilátoru C2583](compiler-error-C2583.md)|'*identifikátor*': 'const nebo volatile' 'Tento ukazatel je neplatný pro konstruktory/destruktorů|
|[Chyba kompilátoru C2584](compiler-error-C2584.md)|'*– třída*': přímé základní '*base_class2*' je nepřístupný; již základ '*base_class1*'|
|[Chyba kompilátoru C2585](compiler-error-C2585.md)|explicitní převod na '*typ*' je nejednoznačný|
|[Chyba kompilátoru C2586](compiler-error-C2586.md)|nesprávné uživatelské převod syntaxe: Neplatný indirections|
|[Chyba kompilátoru C2587](compiler-error-C2587.md)|'*identifikátor*': Neplatné použití místní proměnné jako výchozí parametr|
|[Chyba kompilátoru C2588](compiler-error-C2588.md)|':: ~*identifikátor*': Neplatný globální destruktor/finalizační metodu|
|[Chyba kompilátoru C2589](compiler-error-C2589.md)|'*identifikátor*': neplatný token na pravé straně '::'|
|C2590 chyby kompilátoru|'*identifikátor*': pouze konstruktor může mít základní nebo člen inicializátoru seznamu|
|C2591 chyby kompilátoru|Nelze použít ExclusiveTo '*typu*' jako argument. Pouze 'ref Třída' je platný argument|
|[Chyba kompilátoru C2592](compiler-error-C2592.md)|'*– třída*': '*base_class2*'je zděděn z'*base_class1*' a nelze jej znovu zadat.|
|[Chyba kompilátoru C2593](compiler-error-C2593.md)|"operátor *identifikátor*' je nejednoznačný|
|[Chyba kompilátoru C2594](compiler-error-C2594.md)|'*operátor*': nejednoznačné převody z '*type1*'do'*type2*.|
|C2595 chyby kompilátoru|'*identifikátor*' A WinRT typ atributu musí být zapečetěna.|
|C2596 chyby kompilátoru|'*identifikátor*' A WinRT atribut pole lze pouze 'veřejný výčet třídu', 'int', 'unsigned int,, bool, 'Platform::Type', 'Platform::String' nebo 'Windows:: Foundation:: HResult.|
|[Chyba kompilátoru C2597](compiler-error-C2597.md)|Neplatný odkaz na člena nestatické '*identifikátor*.|
|[Chyba kompilátoru C2598](compiler-error-C2598.md)|Specifikace propojení se musí nacházet v globálním oboru|
|[Chyba kompilátoru C2599](compiler-error-C2599.md)|'*identifikátor*': předat dál deklaraci spravované nebo WinRT výčtu není povolen.|  