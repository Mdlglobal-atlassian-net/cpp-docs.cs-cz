---
title: "C2600 chyby kompilátoru prostřednictvím C2699 | Microsoft Docs"
ms.date: 11/17/2017
ms.technology: cpp-tools
ms.topic: error-reference
f1_keywords:
- C2604
- C2606
- C2607
- C2608
- C2609
- C2610
- C2615
- C2618
- C2620
- C2621
- C2622
- C2623
- C2625
- C2629
- C2631
- C2639
- C2641
- C2642
- C2643
- C2644
- C2684
- C2685
- C2686
- C2697
helpviewer_keywords:
- C2604
- C2606
- C2607
- C2608
- C2609
- C2610
- C2615
- C2618
- C2620
- C2621
- C2622
- C2623
- C2625
- C2629
- C2631
- C2639
- C2641
- C2642
- C2643
- C2644
- C2684
- C2685
- C2686
- C2697
dev_langs: C++
ms.assetid: 73c6319f-cbea-4a2f-913b-90dc1af61f64
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7b67597e6b841546b624d235ab017f138b969135
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-errors-c2600-through-c2699"></a>C2600 chyby kompilátoru prostřednictvím C2699

Články v této části dokumentace vysvětlují podmnožinu chybové zprávy, které jsou generované kompilátorem.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Chybové zprávy

|Chyba|Zpráva|
|-----------|-------------|
|[Chyba kompilátoru C2600](compiler-error-c2600.md)|'*funkce*': nelze definovat generované kompilátorem speciální členské funkce (musí být deklarován v třídě nejprve)|
|[Chyba kompilátoru C2601](compiler-error-c2601.md)|'*funkce*': definice místní funkcí jsou neplatné|
|[Chyba kompilátoru C2602](compiler-error-c2602.md)|'*– třída*::*identifikátor*, není členem základní třídě'*třída*.|
|[Chyba kompilátoru C2603](compiler-error-c2603.md)|'*funkce*': příliš mnoho bloku oboru statické objekty s konstruktor/destruktory ve funkci|
|C2604 chyby kompilátoru|'*identifikátor*': nelze implementovat, víc než jedné metody rozhraní|
|[Chyba kompilátoru C2605](compiler-error-c2605.md)|'*identifikátor*': Tato metoda je vyhrazena v rámci spravované nebo WinRT třídy|
|C2606 chyby kompilátoru|'*class1*': nelze implementovat, znovu se*člen*', protože je zděděno od runtime základní'*class2*.|
|C2607 chyby kompilátoru|statické kontrolní výraz systému se nezdařilo|
|C2608 chyby kompilátoru|Zastaralé.|
|C2609 chyby kompilátoru|Zastaralé.|
|C2610 chyby kompilátoru|'*třída*::*člen*': není speciální členské funkce, které může být nastavena výchozí hodnota|
|[Chyba kompilátoru C2611](compiler-error-c2611.md)|'*tokenu*': neplatný následující ' ~' (očekávaný identifikátor)|
|[Chyba kompilátoru C2612](compiler-error-c2612.md)|Koncové '*znak*se v seznamu inicializátoru základní nebo člen neplatné|
|[Chyba kompilátoru C2613](compiler-error-c2613.md)|Koncové '*znak*' Neplatný základní třídy seznamu|
|[Chyba kompilátoru C2614](compiler-error-c2614.md)|'*– třída*': Neplatný člen inicializace: '*identifikátor*' není základní nebo člen|
|C2615 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C2616](compiler-error-c2616.md)|'*převod*': nelze implicitně převést jiný lvalue '*type1*' k '*type2*' není const|
|[Chyba kompilátoru C2617](compiler-error-c2617.md)|'*funkce*': nekonzistentní příkaz return|
|C2618 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C2619](compiler-error-c2619.md)|'*identifikátor*': statických dat člena není povolena v anonymní struktura/sjednocení|
|C2620 chyby kompilátoru|Zastaralé.|
|C2621 chyby kompilátoru|Zastaralé.|
|C2622 chyby kompilátoru|Zastaralé.|
|C2623 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C2624](compiler-error-c2624.md)|'*oboru*::*typ*': místní třídy nelze použít k deklarujte proměnné, externí.|
|C2625 chyby kompilátoru|'*identifikátor*': Neplatný členů sjednocení; typ '*typ*' je typ odkazu|
|[Chyba kompilátoru C2626](compiler-error-c2626.md)|'*identifikátor*': privátní nebo chráněná data člena není povolena v anonymní struktura/sjednocení|
|[Chyba kompilátoru C2627](compiler-error-c2627.md)|'*funkce*': není povoleno v anonymní sjednocení – členská funkce|
|[Chyba kompilátoru C2628](compiler-error-c2628.md)|'*type1*"doplněno"*type2*' je neplatný (Zapomněli jste ';'?)|
|C2629 chyby kompilátoru|'*identifikátor*': anonymní struktura/union nelze deklarovat vnořené typy|
|[Chyba kompilátoru C2630](compiler-error-c2630.md)|'*symbol*se v co by měl být čárkami oddělený seznam nalezen|
|C2631 chyby kompilátoru|'*identifikátor*': třídu nebo výčtu nemůže být definovaný ve šablonu alias|
|[Chyba kompilátoru C2632](compiler-error-c2632.md)|'*type1*"doplněno"*type2*' je neplatný.|
|[Chyba kompilátoru C2633](compiler-error-c2633.md)|'*identifikátor*': 'vložené' je třída platné úložiště pro konstruktory|
|[Chyba kompilátoru C2634](compiler-error-c2634.md)|'*třída*::*člen*': ukazatel na odkaz na člena je neplatný|
|[Chyba kompilátoru C2635](compiler-error-c2635.md)|nelze převést '*type1*\*' k '*type2*\*'; je implicitní převod z virtuální třídy base|
|[Chyba kompilátoru C2636](compiler-error-c2636.md)|'*identifikátor*': ukazatel na odkaz na člena je neplatný|
|[Chyba kompilátoru C2637](compiler-error-c2637.md)|'*identifikátor*': ukazatelé na členy dat nelze upravit.|
|[Chyba kompilátoru C2638](compiler-error-c2638.md)|'*identifikátor*': __based – modifikátor neplatná na ukazatel na člena|
|C2639 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C2640](compiler-error-c2640.md)|'*identifikátor*': __based – modifikátor neplatná na odkaz|
|C2641 chyby kompilátoru|Zastaralé.|
|C2642 chyby kompilátoru|Zastaralé.|
|C2643 chyby kompilátoru|Zastaralé.|
|C2644 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C2645](compiler-error-c2645.md)|žádné úplný název pro ukazatel na člena (nalezen ':: * ")|
|[Chyba kompilátoru C2646](compiler-error-c2646.md)|anonymní struktura/union na globální nebo oboru názvů musí být deklarován statické|
|[Chyba kompilátoru C2647](compiler-error-c2647.md)|'*operátor*': nelze dereference '*type1*' na '*type2*.|
|[Chyba kompilátoru C2648](compiler-error-c2648.md)|'*identifikátor*': použijte člena jako výchozí parametr vyžaduje statický člen|
|[Chyba kompilátoru C2649](compiler-error-c2649.md)|'*identifikátor*': není 'třída nebo struktura/sjednocení.|
|[Chyba kompilátoru C2650](compiler-error-c2650.md)|'*operátor*': nemůže být virtuální funkce|
|[Chyba kompilátoru C2651](compiler-error-c2651.md)|'*typ*': nalevo od '::' musí být třída, struktura nebo sjednocení|
|[Chyba kompilátoru C2652](compiler-error-c2652.md)|'*identifikátor*': Neplatný kopírovacího konstruktoru: první parametr nesmí být '*typu*.|
|[Chyba kompilátoru C2653](compiler-error-c2653.md)|'*identifikátor*': není třída nebo obor názvů|
|[Chyba kompilátoru C2654](compiler-error-c2654.md)|'*identifikátor*': Pokus o přístup člena mimo členské funkce|
|[Chyba kompilátoru C2655](compiler-error-c2655.md)|'*identifikátor*': definice nebo opětovná deklarace neplatný v aktuálním oboru|
|[Chyba kompilátoru C2656](compiler-error-c2656.md)|'*funkce*': funkce nejsou povoleny jako bitová pole|
|[Chyba kompilátoru C2657](compiler-error-c2657.md)|'*– třída*:: *' nalezeno na začátku prohlášení (Zapomněli jste k určení typu?)|
|[Chyba kompilátoru C2658](compiler-error-c2658.md)|'*identifikátor*': předefinování ve anonymní struktura/sjednocení|
|[Chyba kompilátoru C2659](compiler-error-c2659.md)|'*operátor*': fungovat jako levý operand|
|[Chyba kompilátoru C2660](compiler-error-c2660.md)|'*funkce*': – funkce nemusí provádět žádné *číslo* argumenty|
|[Chyba kompilátoru C2661](compiler-error-c2661.md)|'*funkce*': žádné přetížené funkce přebírá *číslo* argumenty|
|[Chyba kompilátoru C2662](compiler-error-c2662.md)|'*funkce*': nelze převést "this" ukazatel z '*type1*'do'*type2*.|
|[Chyba kompilátoru C2663](compiler-error-c2663.md)|'*funkce*': *číslo* přetížení mít žádný právní převod "this" ukazatele|
|[Chyba kompilátoru C2664](compiler-error-c2664.md)|'*funkce*': nelze převést argument *číslo* z '*type1*'do'*type2*.|
|[Chyba kompilátoru C2665](compiler-error-c2665.md)|'*funkce*': žádná z *číslo* přetížení může převést všechny typy argumentů|
|[Chyba kompilátoru C2666](compiler-error-c2666.md)|'*funkce*': *číslo* přetížení mají podobné převody|
|[Chyba kompilátoru C2667](compiler-error-c2667.md)|'*funkce*': žádná z *číslo* přetížení mít nejlepší převod|
|[Chyba kompilátoru C2668](compiler-error-c2668.md)|'*funkce*': nejednoznačné volání přetížené funkce|
|[Chyba kompilátoru C2669](compiler-error-c2669.md)|Členská funkce není povoleno v anonymní sjednocení|
|[Chyba kompilátoru C2670](compiler-error-c2670.md)|'*funkce*': funkce šablony nelze převést parametr *číslo* z typu '*typu*.|
|[Chyba kompilátoru C2671](compiler-error-c2671.md)|'*funkce*': statické členské funkce nemají 'tomto ukazatele|
|[C2672 chyby kompilátoru](compiler-error-c2672.md)|'*funkce*': funkce najít žádný odpovídající přetížený.|
|[Chyba kompilátoru C2673](compiler-error-c2673.md)|'*funkce*': globální funkce nemají 'tomto ukazatele|
|[Chyba kompilátoru C2674](compiler-error-c2674.md)|v tomto kontextu není povoleno obecné deklarace|
|[Chyba kompilátoru C2675](compiler-error-c2675.md)|Unární '*operátor*': '*typ*' nedefinuje tento operátor nebo převod na typ přijatelné předdefinované operátor|
|[Chyba kompilátoru C2676](compiler-error-c2676.md)|binární '*operátor*': '*typ*' nedefinuje tento operátor nebo převod na typ přijatelné předdefinované operátor|
|[Chyba kompilátoru C2677](compiler-error-c2677.md)|binární '*operátor*': žádné globální operátor nalezen, což trvá typu '*typ*' (nebo není žádný převod přijatelné)|
|[Chyba kompilátoru C2678](compiler-error-c2678.md)|binární '*operátor*': žádná operátorem najít, což trvá levé operand typu '*typ*' (nebo není žádný převod přijatelné)|
|[Chyba kompilátoru C2679](compiler-error-c2679.md)|binární '*operátor*': žádná operátorem najít, což trvá pravém operand typu '*typ*' (nebo není žádný převod přijatelné)|
|[Chyba kompilátoru C2680](compiler-error-c2680.md)|'*typ*': Neplatný typ cíle pro *přetypování*|
|[Chyba kompilátoru C2681](compiler-error-c2681.md)|'*typ*': Neplatný výraz typu pro *přetypování*|
|[Chyba kompilátoru C2682](compiler-error-c2682.md)|nelze použít se*přetypování*' Chcete-li převést z'*type1*'do'*type2*.|
|[Chyba kompilátoru C2683](compiler-error-c2683.md)|'*přetypování*': '*typ*' není polymorfní typ|
|C2684 chyby kompilátoru|'*deklarátor*': odstraněné a uvedena funkce nejsou podporovány ve spravované nebo WinRT třídy|
|C2685 chyby kompilátoru|'*deklarátor*': odstraněné a uvedena funkce nejsou podporovány s specifikátory explicitní omezení|
|C2686 chyby kompilátoru|Nelze se stejnými typy parametr přetížení statické a nestatické členské funkce|
|[Chyba kompilátoru C2687](compiler-error-c2687.md)|'*typ*': výjimka deklarace nemůže být 'void' nebo označují neúplné typu nebo ukazatel nebo odkaz na typ neúplné|
|[Chyba kompilátoru C2688](compiler-error-c2688.md)|'*typ*::*člen*': kovariantní vrátí s více nebo není podporována pro funkce vararg virtuální dědičnost|
|[Chyba kompilátoru C2689](compiler-error-c2689.md)|'*funkce*': funkce friend nemůže být definován v rámci místního – třída|
|[Chyba kompilátoru C2690](compiler-error-c2690.md)|'*operátor*': nelze provést aritmetika ukazatele na pole spravované nebo WinRT|
|[Chyba kompilátoru C2691](compiler-error-c2691.md)|'*typ*': pole spravované nebo WinRT nemůže mít tento typ elementu|
|[Chyba kompilátoru C2692](compiler-error-c2692.md)|'*funkce*': plně deklaraci funkce vyžadované v kompilátoru jazyka C s ' / clr se možnost|
|[Chyba kompilátoru C2693](compiler-error-c2693.md)|'*operátor*': Neplatný porovnání pro odkazy na pole spravované nebo WinRT|
|[Chyba kompilátoru C2694](compiler-error-c2694.md)|'*override_function*': přepisování virtuální funkce má méně omezující specifikace výjimek než funkce člena virtuální základní třída '*base_function*.|
|[Chyba kompilátoru C2695](compiler-error-c2695.md)|'*override_function*': přepisování virtuální funkce se liší od '*base_function*' pouze podle konvence volání|
|[Chyba kompilátoru C2696](compiler-error-c2696.md)|Nelze vytvořit dočasný objekt typu spravované/WinRT '*typu*.|
|C2697 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C2698](compiler-error-c2698.md)|pomocí deklaraci pro '*declaration1*'nemohou existovat společně s existující pomocí deklaraci pro'*declaration2*.|
