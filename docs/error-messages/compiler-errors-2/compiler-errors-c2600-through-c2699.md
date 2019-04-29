---
title: Chyby kompilátoru C2600 až C2699
ms.date: 04/21/2019
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
ms.assetid: 73c6319f-cbea-4a2f-913b-90dc1af61f64
ms.openlocfilehash: 9ac5f5724490574aecf0e5b542f6fdd42b0ae5bb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406506"
---
# <a name="compiler-errors-c2600-through-c2699"></a>Chyby kompilátoru C2600 až C2699

Články v této části dokumentace vysvětlují podmnožinu chybové zprávy, které jsou generovány kompilátorem.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Chybové zprávy

|Chyba|Zpráva|
|-----------|-------------|
|[Chyba kompilátoru C2600](compiler-error-c2600.md)|"*funkce*': nelze definovat kompilátorem generované zvláštní členské funkce (nejprve musí být deklarován ve třídě)|
|[Chyba kompilátoru C2601](compiler-error-c2601.md)|"*funkce*': definice lokální funkce jsou neplatné|
|[Chyba kompilátoru C2602](compiler-error-c2602.md)|"*třídy*::*identifikátor*"není členem základní třídy"*třídy*.|
|[Chyba kompilátoru C2603](compiler-error-c2603.md)|"*funkce*": Příliš mnoho statických objektů oboru bloku s konstruktory/destruktory ve funkci|
|Chyba kompilátoru C2604|"*identifikátor*": Nejde implementovat víc než jednu metodu rozhraní|
|[Chyba kompilátoru C2605](compiler-error-c2605.md)|"*identifikátor*': Tato metoda je vyhrazená v rámci třídy spravované/WinRT|
|Chyba kompilátoru C2606|"*class1*': nejde znova implementovat '*člen*", protože je zděděno z modulu runtime základní"*class2*"|
|Chyba kompilátoru C2607|Chyba statického kontrolního výrazu|
|Chyba kompilátoru C2608|Zastaralé.|
|Chyba kompilátoru C2609|Zastaralé.|
|Chyba kompilátoru C2610|"*třídy*::*člen*': není speciální členská funkce, která by se dala|
|[Chyba kompilátoru C2611](compiler-error-c2611.md)|"*token*': neplatný následující ' ~" (očekával se identifikátor)|
|[Chyba kompilátoru C2612](compiler-error-c2612.md)|na konci "*znak*" neplatné v seznamu inicializátorů base/member|
|[Chyba kompilátoru C2613](compiler-error-c2613.md)|na konci "*znak*" neplatné v seznamu základních tříd|
|[Chyba kompilátoru C2614](compiler-error-c2614.md)|"*třídy*': Neplatná inicializace členu:"*identifikátor*"není základní nebo členský|
|Chyba kompilátoru C2615|Zastaralé.|
|[Chyba kompilátoru C2616](compiler-error-c2616.md)|"*převod*': nelze implicitně převést na jiné hodnoty lvalue"*type1*"k"*type2*", který není const|
|[Chyba kompilátoru C2617](compiler-error-c2617.md)|"*funkce*': nekonzistentní návratový příkaz.|
|Chyba kompilátoru C2618|Zastaralé.|
|[Chyba kompilátoru C2619](compiler-error-c2619.md)|"*identifikátor*': Statický datový člen není povolený v anonymní struktuře/sjednocení|
|Chyba kompilátoru C2620|Zastaralé.|
|Chyba kompilátoru C2621|Zastaralé.|
|Chyba kompilátoru C2622|Zastaralé.|
|Chyba kompilátoru C2623|Zastaralé.|
|[Chyba kompilátoru C2624](compiler-error-c2624.md)|"*oboru*::*typ*': lokální třídy nejde používat pro deklarování proměnných"extern"|
|Chyba kompilátoru C2625|"*identifikátor*': Neplatný člen sjednocení; typ"*typ*"je odkazový typ.|
|[Chyba kompilátoru C2626](compiler-error-c2626.md)|"*identifikátor*': private nebo protected. datový člen není povolený v anonymní struktuře/sjednocení|
|[Chyba kompilátoru C2627](compiler-error-c2627.md)|"*funkce*': členská funkce není v anonymním sjednocení povolená.|
|[Chyba kompilátoru C2628](compiler-error-c2628.md)|"*type1*"následované"*type2*" je neplatné. (Nezapomněli jste středník (;)?)|
|Chyba kompilátoru C2629|"*identifikátor*': anonymní struktuře/sjednocení nejde deklarovat vnořený typ.|
|[Chyba kompilátoru C2630](compiler-error-c2630.md)|"*symbol*" v co by měl být seznam oddělený čárkami|
|Chyba kompilátoru C2631|"*identifikátor*': třída nebo výčet se nedá definovat v šabloně aliasů|
|[Chyba kompilátoru C2632](compiler-error-c2632.md)|"*type1*"následované"*type2*" je neplatné.|
|[Chyba kompilátoru C2633](compiler-error-c2633.md)|"*identifikátor*": "vložené" je jedinou platnou třídou úložiště pro konstruktory|
|[Chyba kompilátoru C2634](compiler-error-c2634.md)|"*třídy*::*člen*': ukazatel na odkazový člen je neplatný|
|[Chyba kompilátoru C2635](compiler-error-c2635.md)|nelze převést "*type1*\*" k "*type2*\*'; implicitní převod z virtuální základní třídy|
|[Chyba kompilátoru C2636](compiler-error-c2636.md)|"*identifikátor*': ukazatel na odkazový člen je neplatný|
|[Chyba kompilátoru C2637](compiler-error-c2637.md)|"*identifikátor*': nejdou upravovat ukazatele na datové členy|
|[Chyba kompilátoru C2638](compiler-error-c2638.md)|"*identifikátor*': ukazatel na ukazatel na člena je neplatný modifikátor __based|
|Chyba kompilátoru C2639|Zastaralé.|
|[Chyba kompilátoru C2640](compiler-error-c2640.md)|"*identifikátor*': pro odkaz neplatný modifikátor __based|
|Chyba kompilátoru C2641|Zastaralé.|
|Chyba kompilátoru C2642|Zastaralé.|
|Chyba kompilátoru C2643|Zastaralé.|
|Chyba kompilátoru C2644|Zastaralé.|
|[Chyba kompilátoru C2645](compiler-error-c2645.md)|neexistuje kvalifikovaný název pro ukazatel na člen (nalezen ':: *')|
|[Chyba kompilátoru C2646](compiler-error-c2646.md)|anonymní struktuře/sjednocení globální nebo obor názvů musí být deklarované jako statické.|
|[Chyba kompilátoru C2647](compiler-error-c2647.md)|"*– operátor*': Nelze přistoupit přes ukazatel"*type1*"na"*type2*"|
|[Chyba kompilátoru C2648](compiler-error-c2648.md)|"*identifikátor*': použití členu jako výchozího parametru vyžaduje statický člen|
|[Chyba kompilátoru C2649](compiler-error-c2649.md)|"*identifikátor*': není"class/struct/union.|
|[Chyba kompilátoru C2650](compiler-error-c2650.md)|"*operátor*': nemůže být virtuální funkce|
|[Chyba kompilátoru C2651](compiler-error-c2651.md)|"*typ*': Levá strana '::' musí být třída, struktura nebo sjednocení|
|[Chyba kompilátoru C2652](compiler-error-c2652.md)|"*identifikátor*': neplatné kopírovací konstuktor: první parametr nesmí být"*typ*"|
|[Chyba kompilátoru C2653](compiler-error-c2653.md)|"*identifikátor*': není název třídy nebo oboru názvů|
|[Chyba kompilátoru C2654](compiler-error-c2654.md)|"*identifikátor*': Pokus o přístup k členu mimo členskou funkci|
|[Chyba kompilátoru C2655](compiler-error-c2655.md)|"*identifikátor*': definice nebo opětovná deklarace není v aktuálním rozsahu.|
|[Chyba kompilátoru C2656](compiler-error-c2656.md)|"*funkce*': funkce není povolená jako bitové pole.|
|[Chyba kompilátoru C2657](compiler-error-c2657.md)|"*třídy*:: *" na začátku příkazu (Nezapomněli jste zadat typ?)|
|[Chyba kompilátoru C2658](compiler-error-c2658.md)|"*identifikátor*': předefinování v anonymní struktuře/sjednocení|
|[Chyba kompilátoru C2659](compiler-error-c2659.md)|"*operátor*': funkce jako levý operand|
|[Chyba kompilátoru C2660](compiler-error-c2660.md)|"*funkce*': funkce nepřijímá *číslo* argumenty|
|[Chyba kompilátoru C2661](compiler-error-c2661.md)|"*funkce*': funkce overloaded má *číslo* argumenty|
|[Chyba kompilátoru C2662](compiler-error-c2662.md)|"*funkce*': nelze převést 'this' ukazatel z"*type1*"do"*type2*.|
|[Chyba kompilátoru C2663](compiler-error-c2663.md)|"*funkce*': *číslo* přetížení nemají žádný platný převod pro ukazatele"this"|
|[Chyba kompilátoru C2664](compiler-error-c2664.md)|"*funkce*': nelze převést argument *číslo* z"*type1*"do"*type2*"|
|[Chyba kompilátoru C2665](compiler-error-c2665.md)|"*funkce*': žádná z *číslo* přetížení nemohlo převést všechny typy argumentů|
|[Chyba kompilátoru C2666](compiler-error-c2666.md)|"*funkce*': *číslo* přetížení má podobné převody|
|[Chyba kompilátoru C2667](compiler-error-c2667.md)|"*funkce*': žádná z *číslo* přetížení nemá nejlepší převod|
|[Chyba kompilátoru C2668](compiler-error-c2668.md)|"*funkce*': nejednoznačné volání přetížené funkce|
|[Chyba kompilátoru C2669](compiler-error-c2669.md)|Členská funkce není v anonymním sjednocení povolená.|
|[Chyba kompilátoru C2670](compiler-error-c2670.md)|"*funkce*': Šablona funkcí nemůže převést parametr *číslo* z typu '*typ*.|
|[Chyba kompilátoru C2671](compiler-error-c2671.md)|"*funkce*': statické členské funkce nemají ukazatele"this"|
|[Chyba kompilátoru C2672](compiler-error-c2672.md)|"*funkce*': žádná odpovídající Přetížená funkce nalezen|
|[Chyba kompilátoru C2673](compiler-error-c2673.md)|"*funkce*': globální funkce nemají ukazatele"this"|
|[Chyba kompilátoru C2674](compiler-error-c2674.md)|Obecná deklarace není v tomto kontextu povolená.|
|[Chyba kompilátoru C2675](compiler-error-c2675.md)|Unární "*operátor*": "*typ*' nedefinuje tento operátor nebo převod na typ přijatelný pro předdefinovaný operátor|
|[Chyba kompilátoru C2676](compiler-error-c2676.md)|binární '*operátor*":"*typ*' nedefinuje tento operátor nebo převod na typ přijatelný pro předdefinovaný operátor|
|[Chyba kompilátoru C2677](compiler-error-c2677.md)|binární '*operátor*': nenašel se žádný globální operátor, který převezme typ "*typ*" (nebo neexistuje žádný přijatelný převod)|
|[Chyba kompilátoru C2678](compiler-error-c2678.md)|binární '*operátor*': nenašel se žádný operátor, který by zpracovával levý operand typu "*typ*" (nebo neexistuje žádný přijatelný převod)|
|[Chyba kompilátoru C2679](compiler-error-c2679.md)|binární '*operátor*': nenašel se žádný operátor, který by zpracovával pravý operand typu "*typ*" (nebo neexistuje žádný přijatelný převod)|
|[Chyba kompilátoru C2680](compiler-error-c2680.md)|"*typ*': Neplatný cílový typ pro *přetypování*|
|[Chyba kompilátoru C2681](compiler-error-c2681.md)|"*typ*': Neplatný typ výrazu pro *přetypování*|
|[Chyba kompilátoru C2682](compiler-error-c2682.md)|nelze použít '*přetypování*"pro převod z'*type1*"do"*type2*.|
|[Chyba kompilátoru C2683](compiler-error-c2683.md)|"*přetypování*": "*typ*" není polymorfní typ|
|Chyba kompilátoru C2684|"*deklarátor*': odstraněné a výchozí funkce nejsou podporované v třídách spravované/WinRT|
|Chyba kompilátoru C2685|"*deklarátor*': odstraněné a výchozí funkce nejsou podporované s explicitními specifikátory omezení|
|Chyba kompilátoru C2686|nejde přetížit statické a nestatické členské funkce se stejnými typy parametrů|
|[Chyba kompilátoru C2687](compiler-error-c2687.md)|"*typ*': deklarace výjimky nemůže být void' nebo označení neúplný typ nebo ukazatel nebo odkaz na neúplný typ.|
|[Chyba kompilátoru C2688](compiler-error-c2688.md)|"*typ*::*člen*': kovariant se vrací s několika nebo virtual, což není podporované funkcemi varargs|
|[Chyba kompilátoru C2689](compiler-error-c2689.md)|"*funkce*': funkce friend nemůže být definovaná v rámci lokální třídy|
|[Chyba kompilátoru C2690](compiler-error-c2690.md)|"*operátor*': nejde provést aritmetiku ukazatele na pole spravovaných/WinRT|
|[Chyba kompilátoru C2691](compiler-error-c2691.md)|"*typ*': pole spravovaných/WinRT nemůže mít tento typ elementu|
|[Chyba kompilátoru C2692](compiler-error-c2692.md)|"*funkce*': v kompilátoru C používat plně prototypované funkce" / clr' možnost|
|[Chyba kompilátoru C2693](compiler-error-c2693.md)|"*operátor*': Neplatné porovnání pro odkazy na pole spravovaných/WinRT|
|[Chyba kompilátoru C2694](compiler-error-c2694.md)|"*override_function*': přepisující virtuální funkce má míň omezující specifikaci výjimky než virtuální členskou funkci základní třídy"*base_function*.|
|[Chyba kompilátoru C2695](compiler-error-c2695.md)|"*override_function*': přepisující virtuální funkce se liší od"*base_function*"pouze podle konvence volání|
|[Chyba kompilátoru C2696](compiler-error-c2696.md)|Nelze vytvořit dočasný objekt typu spravované/WinRT "*typ*.|
|Chyba kompilátoru C2697|Zastaralé.|
|[Chyba kompilátoru C2698](compiler-error-c2698.md)|deklarace using pro '*declaration1*'nemůže společně existovat s existující deklarace using pro'*declaration2*.|

## <a name="see-also"></a>Viz také:

[C /C++ nástroje chyby a upozornění kompilátoru a sestavení](../compiler-errors-1/c-cpp-build-errors.md) \
[Chyby kompilátoru C2000 - C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
