---
title: "C2600 chyby kompilátoru prostřednictvím C2699 | Microsoft Docs"
ms.date: 10/25/2017
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
ms.openlocfilehash: 70ea205ef770fe98cb94cbfc4107fdb4af6560b5
ms.sourcegitcommit: 69632887f7a85f4841c49b4c1353d3144927a52c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/11/2017
---
# <a name="compiler-errors-c2600-through-c2699"></a>C2600 chyby kompilátoru prostřednictvím C2699

Články v této části dokumentace obsahují informace o část chyb kompilátoru Visual C++. Můžete přístup k informacím zde nebo v **výstup** oken v sadě Visual Studio, můžete vybrat číslo chyby a potom vyberte klávesy F1.

> [!NOTE]
> Ne každý [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] chyba je popsána v MSDN. Diagnostické zprávy v mnoha případech poskytuje všechny informace, které jsou k dispozici. Pokud se domníváte, že chybovou zprávu potřebuje další vysvětlení, můžete dejte nám vědět. Můžete použít formulář zpětné vazby na této stránce, nebo přejít na panelu nabídek v sadě Visual Studio a zvolte **pomoci**, **ohlásit chybu**, nebo můžete odeslat zprávu návrhu nebo chyb na [Microsoft Connect](http://connect.microsoft.com/VisualStudio).

Chyby a upozornění na veřejných fórech MSDN můžete najít další pomoc. [Jazyka Visual C++](http://go.microsoft.com/fwlink/?LinkId=158195) fórum je pro dotazy a v diskusích o [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] syntaxi a kompilátoru jazyka. [Visual C++ Obecné](http://go.microsoft.com/fwlink/?LinkId=158194) fórum je pro dotazy o [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] které nejsou popsané v dalších fóra. Můžete také zjistit nápovědu k nástroji chyby a upozornění na [Stack Overflow](http://stackoverflow.com/).

|Chyba|Zpráva|
|-----------|-------------|
|[C2600 chyby kompilátoru](compiler-error-c2600.md)|'*funkce*': nelze definovat generované kompilátorem speciální členské funkce (musí být deklarován v třídě nejprve)|
|[C2601 chyby kompilátoru](compiler-error-c2601.md)|'*funkce*': definice místní funkcí jsou neplatné|
|[C2602 chyby kompilátoru](compiler-error-c2602.md)|'*– třída*::*identifikátor*, není členem základní třídě'*třída*.|
|[C2603 chyby kompilátoru](compiler-error-c2603.md)|'*funkce*': příliš mnoho bloku oboru statické objekty s konstruktor/destruktory ve funkci|
|C2604 chyby kompilátoru|'*identifikátor*': nelze implementovat, víc než jedné metody rozhraní|
|[C2605 chyby kompilátoru](compiler-error-c2605.md)|'*identifikátor*': Tato metoda je vyhrazena v rámci spravované nebo WinRT třídy|
|C2606 chyby kompilátoru|'*class1*': nelze implementovat, znovu se*člen*', protože je zděděno od runtime základní'*class2*.|
|C2607 chyby kompilátoru|statické kontrolní výraz systému se nezdařilo|
|C2608 chyby kompilátoru|Zastaralé.|
|C2609 chyby kompilátoru|Zastaralé.|
|C2610 chyby kompilátoru|'*třída*::*člen*': není speciální členské funkce, které může být nastavena výchozí hodnota|
|[C2611 chyby kompilátoru](compiler-error-c2611.md)|'*tokenu*': neplatný následující ' ~' (očekávaný identifikátor)|
|[C2612 chyby kompilátoru](compiler-error-c2612.md)|Koncové '*znak*se v seznamu inicializátoru základní nebo člen neplatné|
|[C2613 chyby kompilátoru](compiler-error-c2613.md)|Koncové '*znak*' Neplatný základní třídy seznamu|
|[C2614 chyby kompilátoru](compiler-error-c2614.md)|'*– třída*': Neplatný člen inicializace: '*identifikátor*' není základní nebo člen|
|C2615 chyby kompilátoru|Zastaralé.|
|[C2616 chyby kompilátoru](compiler-error-c2616.md)|'*převod*': nelze implicitně převést jiný lvalue '*type1*' k '*type2*' není const|
|[C2617 chyby kompilátoru](compiler-error-c2617.md)|'*funkce*': nekonzistentní příkaz return|
|C2618 chyby kompilátoru|Zastaralé.|
|[C2619 chyby kompilátoru](compiler-error-c2619.md)|'*identifikátor*': statických dat člena není povolena v anonymní struktura/sjednocení|
|C2620 chyby kompilátoru|Zastaralé.|
|C2621 chyby kompilátoru|Zastaralé.|
|C2622 chyby kompilátoru|Zastaralé.|
|C2623 chyby kompilátoru|Zastaralé.|
|[C2624 chyby kompilátoru](compiler-error-c2624.md)|'*oboru*::*typ*': místní třídy nelze použít k deklarujte proměnné, externí.|
|C2625 chyby kompilátoru|'*identifikátor*': Neplatný členů sjednocení; typ '*typ*' je typ odkazu|
|[C2626 chyby kompilátoru](compiler-error-c2626.md)|'*identifikátor*': privátní nebo chráněná data člena není povolena v anonymní struktura/sjednocení|
|[C2627 chyby kompilátoru](compiler-error-c2627.md)|'*funkce*': není povoleno v anonymní sjednocení – členská funkce|
|[C2628 chyby kompilátoru](compiler-error-c2628.md)|'*type1*"doplněno"*type2*' je neplatný (Zapomněli jste ';'?)|
|C2629 chyby kompilátoru|'*identifikátor*': anonymní struktura/union nelze deklarovat vnořené typy|
|[C2630 chyby kompilátoru](compiler-error-c2630.md)|'*symbol*se v co by měl být čárkami oddělený seznam nalezen|
|C2631 chyby kompilátoru|'*identifikátor*': třídu nebo výčtu nemůže být definovaný ve šablonu alias|
|[C2632 chyby kompilátoru](compiler-error-c2632.md)|'*type1*"doplněno"*type2*' je neplatný.|
|[C2633 chyby kompilátoru](compiler-error-c2633.md)|'*identifikátor*': 'vložené' je třída platné úložiště pro konstruktory|
|[C2634 chyby kompilátoru](compiler-error-c2634.md)|'*třída*::*člen*': ukazatel na odkaz na člena je neplatný|
|[C2635 chyby kompilátoru](compiler-error-c2635.md)|nelze převést '*type1*\*' k '*type2*\*'; je implicitní převod z virtuální třídy base|
|[C2636 chyby kompilátoru](compiler-error-c2636.md)|'*identifikátor*': ukazatel na odkaz na člena je neplatný|
|[C2637 chyby kompilátoru](compiler-error-c2637.md)|'*identifikátor*': ukazatelé na členy dat nelze upravit.|
|[C2638 chyby kompilátoru](compiler-error-c2638.md)|'*identifikátor*': __based – modifikátor neplatná na ukazatel na člena|
|C2639 chyby kompilátoru|Zastaralé.|
|[C2640 chyby kompilátoru](compiler-error-c2640.md)|'*identifikátor*': __based – modifikátor neplatná na odkaz|
|C2641 chyby kompilátoru|Zastaralé.|
|C2642 chyby kompilátoru|Zastaralé.|
|C2643 chyby kompilátoru|Zastaralé.|
|C2644 chyby kompilátoru|Zastaralé.|
|[C2645 chyby kompilátoru](compiler-error-c2645.md)|žádné úplný název pro ukazatel na člena (nalezen ':: * ")|
|[C2646 chyby kompilátoru](compiler-error-c2646.md)|anonymní struktura/union na globální nebo oboru názvů musí být deklarován statické|
|[C2647 chyby kompilátoru](compiler-error-c2647.md)|'*operátor*': nelze dereference '*type1*' na '*type2*.|
|[C2648 chyby kompilátoru](compiler-error-c2648.md)|'*identifikátor*': použijte člena jako výchozí parametr vyžaduje statický člen|
|[C2649 chyby kompilátoru](compiler-error-c2649.md)|'*identifikátor*': není 'třída nebo struktura/sjednocení.|
|[C2650 chyby kompilátoru](compiler-error-c2650.md)|'*operátor*': nemůže být virtuální funkce|
|[C2651 chyby kompilátoru](compiler-error-c2651.md)|'*typ*': nalevo od '::' musí být třída, struktura nebo sjednocení|
|[C2652 chyby kompilátoru](compiler-error-c2652.md)|'*identifikátor*': Neplatný kopírovacího konstruktoru: první parametr nesmí být '*typu*.|
|[C2653 chyby kompilátoru](compiler-error-c2653.md)|'*identifikátor*': není třída nebo obor názvů|
|[C2654 chyby kompilátoru](compiler-error-c2654.md)|'*identifikátor*': Pokus o přístup člena mimo členské funkce|
|[C2655 chyby kompilátoru](compiler-error-c2655.md)|'*identifikátor*': definice nebo opětovná deklarace neplatný v aktuálním oboru|
|[C2656 chyby kompilátoru](compiler-error-c2656.md)|'*funkce*': funkce nejsou povoleny jako bitová pole|
|[C2657 chyby kompilátoru](compiler-error-c2657.md)|'*– třída*:: *' nalezeno na začátku prohlášení (Zapomněli jste k určení typu?)|
|[C2658 chyby kompilátoru](compiler-error-c2658.md)|'*identifikátor*': předefinování ve anonymní struktura/sjednocení|
|[C2659 chyby kompilátoru](compiler-error-c2659.md)|'*operátor*': fungovat jako levý operand|
|[C2660 chyby kompilátoru](compiler-error-c2660.md)|'*funkce*': – funkce nemusí provádět žádné *číslo* argumenty|
|[C2661 chyby kompilátoru](compiler-error-c2661.md)|'*funkce*': žádné přetížené funkce přebírá *číslo* argumenty|
|[C2662 chyby kompilátoru](compiler-error-c2662.md)|'*funkce*': nelze převést "this" ukazatel z '*type1*'do'*type2*.|
|[C2663 chyby kompilátoru](compiler-error-c2663.md)|'*funkce*': *číslo* přetížení mít žádný právní převod "this" ukazatele|
|[C2664 chyby kompilátoru](compiler-error-c2664.md)|'*funkce*': nelze převést argument *číslo* z '*type1*'do'*type2*.|
|[C2665 chyby kompilátoru](compiler-error-c2665.md)|'*funkce*': žádná z *číslo* přetížení může převést všechny typy argumentů|
|[C2666 chyby kompilátoru](compiler-error-c2666.md)|'*funkce*': *číslo* přetížení mají podobné převody|
|[C2667 chyby kompilátoru](compiler-error-c2667.md)|'*funkce*': žádná z *číslo* přetížení mít nejlepší převod|
|[C2668 chyby kompilátoru](compiler-error-c2668.md)|'*funkce*': nejednoznačné volání přetížené funkce|
|[C2669 chyby kompilátoru](compiler-error-c2669.md)|Členská funkce není povoleno v anonymní sjednocení|
|[C2670 chyby kompilátoru](compiler-error-c2670.md)|'*funkce*': funkce šablony nelze převést parametr *číslo* z typu '*typu*.|
|[C2671 chyby kompilátoru](compiler-error-c2671.md)|'*funkce*': statické členské funkce nemají 'tomto ukazatele|
|[C2672 chyby kompilátoru](compiler-error-c2672.md)|'*funkce*': funkce najít žádný odpovídající přetížený.|
|[C2673 chyby kompilátoru](compiler-error-c2673.md)|'*funkce*': globální funkce nemají 'tomto ukazatele|
|[C2674 chyby kompilátoru](compiler-error-c2674.md)|v tomto kontextu není povoleno obecné deklarace|
|[C2675 chyby kompilátoru](compiler-error-c2675.md)|Unární '*operátor*': '*typ*' nedefinuje tento operátor nebo převod na typ přijatelné předdefinované operátor|
|[C2676 chyby kompilátoru](compiler-error-c2676.md)|binární '*operátor*': '*typ*' nedefinuje tento operátor nebo převod na typ přijatelné předdefinované operátor|
|[C2677 chyby kompilátoru](compiler-error-c2677.md)|binární '*operátor*': žádné globální operátor nalezen, což trvá typu '*typ*' (nebo není žádný převod přijatelné)|
|[C2678 chyby kompilátoru](compiler-error-c2678.md)|binární '*operátor*': žádná operátorem najít, což trvá levé operand typu '*typ*' (nebo není žádný převod přijatelné)|
|[C2679 chyby kompilátoru](compiler-error-c2679.md)|binární '*operátor*': žádná operátorem najít, což trvá pravém operand typu '*typ*' (nebo není žádný převod přijatelné)|
|[C2680 chyby kompilátoru](compiler-error-c2680.md)|'*typ*': Neplatný typ cíle pro *přetypování*|
|[C2681 chyby kompilátoru](compiler-error-c2681.md)|'*typ*': Neplatný výraz typu pro *přetypování*|
|[C2682 chyby kompilátoru](compiler-error-c2682.md)|nelze použít se*přetypování*' Chcete-li převést z'*type1*'do'*type2*.|
|[C2683 chyby kompilátoru](compiler-error-c2683.md)|'*přetypování*': '*typ*' není polymorfní typ|
|C2684 chyby kompilátoru|'*deklarátor*': odstraněné a uvedena funkce nejsou podporovány ve spravované nebo WinRT třídy|
|C2685 chyby kompilátoru|'*deklarátor*': odstraněné a uvedena funkce nejsou podporovány s specifikátory explicitní omezení|
|C2686 chyby kompilátoru|Nelze se stejnými typy parametr přetížení statické a nestatické členské funkce|
|[C2687 chyby kompilátoru](compiler-error-c2687.md)|'*typ*': výjimka deklarace nemůže být 'void' nebo označují neúplné typu nebo ukazatel nebo odkaz na typ neúplné|
|[C2688 chyby kompilátoru](compiler-error-c2688.md)|'*typ*::*člen*': kovariantní vrátí s více nebo není podporována pro funkce vararg virtuální dědičnost|
|[C2689 chyby kompilátoru](compiler-error-c2689.md)|'*funkce*': funkce friend nemůže být definován v rámci místního – třída|
|[C2690 chyby kompilátoru](compiler-error-c2690.md)|'*operátor*': nelze provést aritmetika ukazatele na pole spravované nebo WinRT|
|[C2691 chyby kompilátoru](compiler-error-c2691.md)|'*typ*': pole spravované nebo WinRT nemůže mít tento typ elementu|
|[C2692 chyby kompilátoru](compiler-error-c2692.md)|'*funkce*': plně deklaraci funkce vyžadované v kompilátoru jazyka C s ' / clr se možnost|
|[C2693 chyby kompilátoru](compiler-error-c2693.md)|'*operátor*': Neplatný porovnání pro odkazy na pole spravované nebo WinRT|
|[C2694 chyby kompilátoru](compiler-error-c2694.md)|'*override_function*': přepisování virtuální funkce má méně omezující specifikace výjimek než funkce člena virtuální základní třída '*base_function*.|
|[C2695 chyby kompilátoru](compiler-error-c2695.md)|'*override_function*': přepisování virtuální funkce se liší od '*base_function*' pouze podle konvence volání|
|[C2696 chyby kompilátoru](compiler-error-c2696.md)|Nelze vytvořit dočasný objekt typu spravované/WinRT '*typu*.|
|C2697 chyby kompilátoru|Zastaralé.|
|[C2698 chyby kompilátoru](compiler-error-c2698.md)|pomocí deklaraci pro '*declaration1*'nemohou existovat společně s existující pomocí deklaraci pro'*declaration2*.|
