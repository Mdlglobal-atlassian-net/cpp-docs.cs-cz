---
title: "C2500 chyby kompilátoru prostřednictvím C2599 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
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
dev_langs: C++
ms.assetid: a869aaed-e9f6-49e3-b273-00ea7f45bed7
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e66a789de4a1b5cfd64ff73f6dbecd4e85bfdffd
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2017
---
# <a name="compiler-errors-c2500-through-c2599"></a>C2500 chyby kompilátoru prostřednictvím C2599
Články v této části dokumentace obsahují informace o část chyb kompilátoru Visual C++. Můžete přístup k informacím zde nebo v **výstup** oken v sadě Visual Studio, můžete vybrat číslo chyby a potom vyberte klávesy F1.  
  
> [!NOTE]
>  Ne každý [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] chyba je popsána v MSDN. Diagnostické zprávy v mnoha případech poskytuje všechny informace, které jsou k dispozici. Pokud se domníváte, že chybovou zprávu potřebuje další vysvětlení, můžete dejte nám vědět. Můžete použít formulář zpětné vazby na této stránce, nebo přejít na panelu nabídek v sadě Visual Studio a zvolte **pomoci**, **ohlásit chybu**, nebo můžete odeslat zprávu návrhu nebo chyb na [Microsoft Connect](http://connect.microsoft.com/VisualStudio).  
  
 Chyby a upozornění na veřejných fórech MSDN můžete najít další pomoc. [Jazyka Visual C++](http://go.microsoft.com/fwlink/?LinkId=158195) fórum je pro dotazy a v diskusích o [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] syntaxi a kompilátoru jazyka. [Visual C++ Obecné](http://go.microsoft.com/fwlink/?LinkId=158194) fórum je pro dotazy o [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] které nejsou popsané v dalších fóra. Můžete také zjistit nápovědu k nástroji chyby a upozornění na [Stack Overflow](http://stackoverflow.com/).  
  
|Chyba|Zpráva|  
|-----------|-------------|  
|[C2500 chyby kompilátoru](compiler-error-C2500.md)|'*identifier1*': '*identifier2*' je již přímé základní třída|  
|C2501 chyby kompilátoru|'*identifikátor*': ' __declspec (*specifikátor*), lze použít pouze pro struktury, sjednocení, třídy nebo bez znaménka bitová pole členů|  
|[C2502 chyby kompilátoru](compiler-error-C2502.md)|'*identifikátor*': příliš mnoho modifikátory přístupu na základní třídě.|  
|[C2503 chyby kompilátoru](compiler-error-C2503.md)|'*třída*': základní třídy, nemůže obsahovat pole s nulovou velikostí|  
|[C2504 chyby kompilátoru](compiler-error-C2504.md)|'*třída*': základní třída není definována|  
|[C2505 chyby kompilátoru](compiler-error-C2505.md)|'*symbol*': ' __declspec (*specifikátor*), můžete použít jenom pro deklarace nebo definice globální objekty nebo členy statických dat|  
|[C2506 chyby kompilátoru](compiler-error-C2506.md)|'*člen*': ' __declspec (*specifikátor*), nelze použít pro tento symbol|  
|[C2507 chyby kompilátoru](compiler-error-C2507.md)|'*identifikátor*': příliš mnoho virtuálních modifikátory na základní třídě.|  
|C2508 chyby kompilátoru|'*identifikátor*': ' __declspec (*specifier1*), nelze kombinovat s ' __declspec (*specifier2*).|  
|[C2509 chyby kompilátoru](compiler-error-C2509.md)|'*identifikátor*': členská funkce není deklarován v '*– třída*.|  
|[C2510 chyby kompilátoru](compiler-error-C2510.md)|'*identifikátor*': nalevo od '::' musí být třída nebo struktura/sjednocení|  
|[C2511 chyby kompilátoru](compiler-error-C2511.md)|'*identifikátor*': přetížený – členská funkce nebyla nalezena v '*– třída*.|  
|[C2512 chyby kompilátoru](compiler-error-C2512.md)|'*identifikátor*': žádný odpovídající výchozí konstruktor k dispozici|  
|[C2513 chyby kompilátoru](compiler-error-C2513.md)|' * typ ': žádné proměnné deklarovány před '='|  
|[C2514 chyby kompilátoru](compiler-error-C2514.md)|'*třída*': Třída nemá žádné konstruktory|  
|C2515 chyby kompilátoru|'*identifikátor*': 'vtguard' lze použít pouze na deklaracích třídy nebo definice|  
|[C2516 chyby kompilátoru](compiler-error-C2516.md)|'*třída*': není právní základní třída|  
|[C2517 chyby kompilátoru](compiler-error-C2517.md)|'*identifikátor*': napravo od '::' není definován|  
|[C2518 chyby kompilátoru](compiler-error-C2518.md)|– klíčové slovo '*– klíčové slovo*se v seznamu základní třída neplatné; ignorováno|  
|C2519 chyby kompilátoru|'*identifikátor*': WinRT atributy mohou obsahovat pouze veřejná pole|  
|C2520 chyby kompilátoru|'*třída*': žádný jiný explicitní konstruktor, který je k dispozici pro implicitní převod|  
|[C2521 chyby kompilátoru](compiler-error-C2521.md)|destruktor/finalizační metodu nepřijímá žádné argumenty|  
|C2522 chyby kompilátoru|'*identifikátor*': přetížení identifikátoru nelze použít na '*identifier1*, jako jsou již zadány na'*identifier2*.|  
|[C2523 chyby kompilátoru](compiler-error-C2523.md)|'*třída*:: ~*identifikátor*': Neshoda značky destruktor/finalizační metodu|  
|[C2524 chyby kompilátoru](compiler-error-C2524.md)|'*identifikátor*': destruktor/finalizační metodu musí mít seznam parametrů, void.|  
|C2525 chyby kompilátoru|'*identifikátor*': Parametr '*identifier1*má název*identifier2*se na základní funkce a musí odpovídat v publikované implementaci|  
|[C2526 chyby kompilátoru](compiler-error-C2526.md)|'*identifier1*': C propojení funkce nemůže vrátit třídami C++*identifier2*.|  
|C2527 chyby kompilátoru|'*identifikátor*': DefaultOverload nelze zadat obě '*function1*'a'*funkce2*'. Jeden odeberte nebo přejmenujte funkce během implementace|  
|[C2528 chyby kompilátoru](compiler-error-C2528.md)|'*identifikátor*': ukazatel na odkaz je neplatný|  
|[C2529 chyby kompilátoru](compiler-error-C2529.md)|'*identifikátor*': na odkaz je neplatný|  
|[C2530 chyby kompilátoru](compiler-error-C2530.md)|'*identifikátor*': odkazy musí být inicializován.|  
|[C2531 chyby kompilátoru](compiler-error-C2531.md)|'*identifikátor*': odkaz na trochu neplatné pole|  
|[C2532 chyby kompilátoru](compiler-error-C2532.md)|'*identifikátor*': Neplatný modifikátor pro – referenční informace|  
|[C2533 chyby kompilátoru](compiler-error-C2533.md)|'*identifikátor*': konstruktory nejsou povoleny návratový typ.|  
|[C2534 chyby kompilátoru](compiler-error-C2534.md)|'*identifikátor*': konstruktor nemůže vrátit hodnotu|  
|[C2535 chyby kompilátoru](compiler-error-C2535.md)|'*identifikátor*': členská funkce již definována nebo deklarovaný|  
|C2536 chyby kompilátoru|Zastaralé.|  
|[C2537 chyby kompilátoru](compiler-error-C2537.md)|'*specifikátor*': specifikace neplatný propojení|  
|C2538 chyby kompilátoru|Zastaralé.|  
|C2539 chyby kompilátoru|Zastaralé.|
|[C2540 chyby kompilátoru](compiler-error-C2540.md)|není konstantní výraz jako pole vázán|  
|[C2541 chyby kompilátoru](compiler-error-C2541.md)|'*identifikátor*': nelze odstranit objekty, které nejsou ukazatele|  
|[C2542 chyby kompilátoru](compiler-error-C2542.md)|'*identifikátor*': objektu třídy nemá žádný konstruktor pro inicializaci|  
|[C2543 chyby kompilátoru](compiler-error-C2543.md)|Očekávaný ']' pro operátor '[']|  
|[C2544 chyby kompilátoru](compiler-error-C2544.md)|Očekávaný ')' pro operátor '().|  
|[C2545 chyby kompilátoru](compiler-error-C2545.md)|'*operátor*': Nelze najít přetížený – operátor|  
|C2546 chyby kompilátoru|'*identifikátor*': při typ je definován v PIA a ne PIA nejprve musí odkazovat PIA –|  
|C2547 chyby kompilátoru|'*identifikátor*': všechny parametry metody publikovanou musí být explicitně s názvem v prohlášení o|  
|[C2548 chyby kompilátoru](compiler-error-C2548.md)|'*funkce*': Chybějící výchozí parametr pro parametr *parametr*|  
|[C2549 chyby kompilátoru](compiler-error-C2549.md)|uživatelem definované převod nelze zadat návratový typ.|  
|[C2550 chyby kompilátoru](compiler-error-C2550.md)|'*identifikátor*': konstruktor inicializační seznamy jsou povoleny pouze na definice – konstruktor|  
|[C2551 chyby kompilátoru](compiler-error-C2551.md)|' void *' typ musí explicitní přetypování|  
|[C2552 chyby kompilátoru](compiler-error-C2552.md)|'*identifikátor*': neagregované položky nemůže být inicializovaný s inicializačním seznam|  
|[C2553 chyby kompilátoru](compiler-error-C2553.md)|'*typ* *derived_class*::*funkce*': přepisování virtuální funkce návratový typ se liší od '*typ* *base_ Třída*::*funkce*.|  
|[C2555 chyby kompilátoru](compiler-error-C2555.md)|'*derived_class*::*funkce*': přepisování virtuální funkce návratový typ se liší a není kovariantní z '*base_class*::*funkce*'|  
|[C2556 chyby kompilátoru](compiler-error-C2556.md)|'*type1* *– třída*::*funkce*': přetížené funkce se liší pouze o návratový typ z '*type2* *–Třída*::*funkce*.|  
|[C2557 chyby kompilátoru](compiler-error-C2557.md)|'*identifikátor*': privátní a chráněné členy nelze inicializovat bez konstruktor|  
|[C2558 chyby kompilátoru](compiler-error-C2558.md)|třída*třída*': žádné kopírovacího konstruktoru, které jsou k dispozici nebo kopírovací konstruktor je deklarován 'explicitní.|  
|C2559 chyby kompilátoru|'*identifikátor*': nelze přetížení členské funkce bez ref kvalifikátor s s ref kvalifikátor členské funkce|  
|C2560 chyby kompilátoru|'*identifikátor*': nelze přetížení členské funkce s ref kvalifikátor s bez ref kvalifikátor členské funkce|  
|[C2561 chyby kompilátoru](compiler-error-C2561.md)|'*funkce*': funkce musí vrátit hodnotu|  
|[C2562 chyby kompilátoru](compiler-error-C2562.md)|'*funkce*': 'void' funkce návrat hodnoty|  
|[C2563 chyby kompilátoru](compiler-error-C2563.md)|Neshoda v seznamu formální parametr|  
|C2564 chyby kompilátoru|Zastaralé.|  
|C2565 chyby kompilátoru|'*identifikátor*': ref kvalifikátor je neplatný pro konstruktory/destruktorů|  
|[C2566 chyby kompilátoru](compiler-error-C2566.md)|přetížené funkce podmíněného výrazu|  
|[C2567 chyby kompilátoru](compiler-error-C2567.md)|Nelze otevřít metadata v '*filename*', *possible_reason*|  
|[C2568 chyby kompilátoru](compiler-error-C2568.md)|'*identifikátor*': nelze vyřešit přetížení funkce|  
|[C2569 chyby kompilátoru](compiler-error-C2569.md)|'*identifikátor*': výčtu nebo union nelze použít jako základní třída|  
|[C2570 chyby kompilátoru](compiler-error-C2570.md)|'*identifikátor*': union nemohou mít základní třídy|  
|[C2571 chyby kompilátoru](compiler-error-C2571.md)|'*identifikátor*': virtuální funkce nelze v sjednocení '*– typ union*.|  
|[C2572 chyby kompilátoru](compiler-error-C2572.md)|'*funkce*': předefinování výchozí argument: Parametr *číslo*|  
|[C2573 chyby kompilátoru](compiler-error-C2573.md)|'*třída*': nelze odstranit ukazatelé na objekty tohoto typu; Třída nemá žádné přetížení jiné umístění pro 'odstranit operátor'. Použití:: odstranit nebo přidejte do třídy 'delete(void*) operátor.|  
|[C2574 chyby kompilátoru](compiler-error-C2574.md)|'*destruktor*': nelze deklarovat statickou|  
|[C2575 chyby kompilátoru](compiler-error-C2575.md)|'*identifikátor*': pouze členských funkcí a databáze, které mohou být virtuální|  
|C2576 chyby kompilátoru|'*identifikátor*': Nelze zavést nové virtuální metody jako 'veřejné'. Zvažte nevirtuálních metodu nebo změnit usnadnění přístupu k "interní" nebo "chráněné privátní"|  
|[C2577 chyby kompilátoru](compiler-error-C2577.md)|'*identifikátor*': destruktor/finalizační metodu nemůže mít typ vrácené hodnoty.|  
|C2578 chyby kompilátoru|'*třída*': typ nemůže mít "chráněné" nebo chráněné veřejný konstruktor|  
|[C2579 chyby kompilátoru](compiler-error-C2579.md)|nelze vyřešit typ *typ* (*posun*). Je očekávána v *filename*|  
|C2580 chyby kompilátoru|'*identifikátor*': více verzí uvedena speciální členské funkce nejsou povoleny.|  
|[C2581 chyby kompilátoru](compiler-error-C2581.md)|'*typ*': statické, operátor =' funkce je neplatný|  
|[C2582 chyby kompilátoru](compiler-error-C2582.md)|"operátor *operátor*'funkce je k dispozici v'*typu*.|  
|[C2583 chyby kompilátoru](compiler-error-C2583.md)|'*identifikátor*': 'const nebo volatile' 'Tento ukazatel je neplatný pro konstruktory/destruktorů|  
|[C2584 chyby kompilátoru](compiler-error-C2584.md)|'*– třída*': přímé základní '*base_class2*' je nepřístupný; již základ '*base_class1*'|  
|[C2585 chyby kompilátoru](compiler-error-C2585.md)|explicitní převod na '*typ*' je nejednoznačný|  
|[C2586 chyby kompilátoru](compiler-error-C2586.md)|nesprávné uživatelské převod syntaxe: Neplatný indirections|  
|[C2587 chyby kompilátoru](compiler-error-C2587.md)|'*identifikátor*': Neplatné použití místní proměnné jako výchozí parametr|  
|[C2588 chyby kompilátoru](compiler-error-C2588.md)|':: ~*identifikátor*': Neplatný globální destruktor/finalizační metodu|  
|[C2589 chyby kompilátoru](compiler-error-C2589.md)|'*identifikátor*': neplatný token na pravé straně '::'|  
|C2590 chyby kompilátoru|'*identifikátor*': pouze konstruktor může mít základní nebo člen inicializátoru seznamu|  
|C2591 chyby kompilátoru|Nelze použít ExclusiveTo '*typu*' jako argument. Pouze 'ref Třída' je platný argument|  
|[C2592 chyby kompilátoru](compiler-error-C2592.md)|'*– třída*': '*base_class2*'je zděděn z'*base_class1*' a nelze jej znovu zadat.|  
|[C2593 chyby kompilátoru](compiler-error-C2593.md)|"operátor *identifikátor*' je nejednoznačný|  
|[C2594 chyby kompilátoru](compiler-error-C2594.md)|'*operátor*': nejednoznačné převody z '*type1*'do'*type2*.|  
|C2595 chyby kompilátoru|'*identifikátor*' A WinRT typ atributu musí být zapečetěna.|  
|C2596 chyby kompilátoru|'*identifikátor*' A WinRT atribut pole lze pouze 'veřejný výčet třídu', 'int', 'unsigned int,, bool, 'Platform::Type', 'Platform::String' nebo 'Windows:: Foundation:: HResult.|  
|[C2597 chyby kompilátoru](compiler-error-C2597.md)|Neplatný odkaz na člena nestatické '*identifikátor*.|  
|[C2598 chyby kompilátoru](compiler-error-C2598.md)|Specifikace propojení se musí nacházet v globálním oboru|  
|[C2599 chyby kompilátoru](compiler-error-C2599.md)|'*identifikátor*': předat dál deklaraci spravované nebo WinRT výčtu není povolen.|  