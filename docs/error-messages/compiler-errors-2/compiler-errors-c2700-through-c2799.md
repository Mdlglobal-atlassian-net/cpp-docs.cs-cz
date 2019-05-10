---
title: Chyby kompilátoru C2700 až C2799
ms.date: 04/21/2019
f1_keywords:
- C2716
- C2717
- C2727
- C2729
- C2737
- C2740
- C2741
- C2742
- C2744
- C2746
- C2747
- C2759
- C2763
- C2769
- C2772
- C2789
- C2796
- C2799
helpviewer_keywords:
- C2716
- C2717
- C2727
- C2729
- C2737
- C2740
- C2741
- C2742
- C2744
- C2746
- C2747
- C2759
- C2763
- C2769
- C2772
- C2789
- C2796
- C2799
ms.assetid: 6ee257bb-94bc-42b9-af2c-3c73926afba4
ms.openlocfilehash: a6f4391008bf9b0a066ba65f27a41697c6097c2e
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64857636"
---
# <a name="compiler-errors-c2700-through-c2799"></a>Chyby kompilátoru C2700 až C2799

Články v této části dokumentace vysvětlují podmnožinu chybové zprávy, které jsou generovány kompilátorem.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Chybové zprávy

|Chyba|Message|
|-----------|-------------|
|[Chyba kompilátoru C2700](compiler-error-c2700.md)|"*typ*': nejde vyvolat (použijte/W4 pro další informace)|
|[Chyba kompilátoru C2701](compiler-error-c2701.md)|"*funkce*': funkce šablony/obecný nemůže být funkce friend lokální třídy|
|[Chyba kompilátoru C2702](compiler-error-c2702.md)| možnost __except nemůže být v ukončovacím bloku.|
|[Chyba kompilátoru C2703](compiler-error-c2703.md)|Neplatný příkaz __leave|
|[Chyba kompilátoru C2704](compiler-error-c2704.md)|"*funkce*': __va_start – vnitřní jsou povolené jenom ve funkcích varargs|
|[Chyba kompilátoru C2705](compiler-error-c2705.md)|"*popisek*': Neplatný skok na"*exception_block*"oboru|
|[Chyba kompilátoru C2706](compiler-error-c2706.md)|Neplatná možnost __except bez odpovídající možnosti __try (chybějící '}' v bloku __try pravá složená?)|
|[Chyba kompilátoru C2707](compiler-error-c2707.md)|"*identifikátor*': špatný kontext pro vnitřní funkci.|
|[Chyba kompilátoru C2708](compiler-error-c2708.md)|"*identifikátor*': Skutečná délka parametrů v bajtech se liší od předchozího volání nebo odkazu|
|[Chyba kompilátoru C2709](compiler-error-c2709.md)|"*identifikátor*': délka formálních parametrů v bajtech se liší od předchozí deklarace|
|[Chyba kompilátoru C2710](compiler-error-c2710.md)|"*identifikátor*": "__declspec (*modifikátor*) se může používat jedině pro funkci vracející ukazatel|
|[Chyba kompilátoru C2711](compiler-error-c2711.md)|"*funkce*': tuto funkci nejde zkompilovat jako spravovanou, zvažte použití #pragma unmanaged|
|[Chyba kompilátoru C2712](compiler-error-c2712.md)|Nelze použít __try ve funkcích, které vyžadovaly objekt vrácení zpět|
|[Chyba kompilátoru C2713](compiler-error-c2713.md)|jednu funkci je povolená jenom jedna podoba ošetření výjimky|
|[Chyba kompilátoru C2714](compiler-error-c2714.md)|možnost alignof(void) není povolená|
|[Chyba kompilátoru C2715](compiler-error-c2715.md)|"*typ*': nelze operaci throw nebo catch tohoto typu|
|Chyba kompilátoru C2716|Zastaralé.|
|Chyba kompilátoru C2717|Zastaralé.|
|[Chyba kompilátoru C2718](compiler-error-c2718.md)|"*typ*': skutečný parametr s požadovaným zarovnáním *číslo* se nezarovnají|
|[Chyba kompilátoru C2719](compiler-error-c2719.md)|"*parametr*': formální parametr s požadovaným zarovnáním *číslo* se nezarovnají|
|[Chyba kompilátoru C2720](compiler-error-c2720.md)|"*identifikátor*": "*specifikátor*' není pro členy platný specifikátor třídy úložiště|
|[Chyba kompilátoru C2721](compiler-error-c2721.md)|"*specifikátor*': specifikátor storage-class není platný mezi klíčovým slovem operator a typem|
|[Chyba kompilátoru C2722](compiler-error-c2722.md)|"::*– operátor*': Neplatná hodnota po příkazu operátoru; použijte" operátor *operátor*"|
|[Chyba kompilátoru C2723](compiler-error-c2723.md)|"*funkce*": "*specifikátor*" specifikátor není platný v definici funkce|
|[Chyba kompilátoru C2724](compiler-error-c2724.md)|"*funkce*': 'static', neměl by se používat pro členské funkce definované v rozsahu souboru|
|[Chyba kompilátoru C2725](compiler-error-c2725.md)|"*typ*': nelze provést operaci throw nebo catch spravované/WinRT objektu podle hodnoty nebo odkazu|
|[Chyba kompilátoru C2726](compiler-error-c2726.md)|'gcnew' slouží jenom k vytvoření objektu s typem spravované/WinRT|
|Chyba kompilátoru C2727|Zastaralé.|
|[Chyba kompilátoru C2728](compiler-error-c2728.md)|"*typ*': nativní pole nemůže obsahovat tento typ.|
|Chyba kompilátoru C2729|Zastaralé.|
|[Chyba kompilátoru C2730](compiler-error-c2730.md)|"*třídy*': nemůže být základní třídou sebe sama|
|[Chyba kompilátoru C2731](compiler-error-c2731.md)|"*funkce*': funkce nemůže být přetížená.|
|[Chyba kompilátoru C2732](compiler-error-c2732.md)|Specifikace propojení konfliktu s předchozí specifikací pro "*funkce*.|
|[Chyba kompilátoru C2733](compiler-error-c2733.md)|"*funkce*': druhé propojení C-linkage přetížení funkce není povolená|
|[Chyba kompilátoru C2734](compiler-error-c2734.md)|"*identifikátor*': 'const' objekt musí být inicializovaný, pokud není extern|
|[Chyba kompilátoru C2735](compiler-error-c2735.md)|"*– klíčové slovo*" klíčové slovo není povolené ve specifikátoru typu formálního parametru|
|[Chyba kompilátoru C2736](compiler-error-c2736.md)|"*– klíčové slovo*" není v přetypování povolené – klíčové slovo|
|Chyba kompilátoru C2737|"*identifikátor*': musí se inicializovat objekt specifikátorem constexpr.|
|[Chyba kompilátoru C2738](compiler-error-c2738.md)|"operátor *typ*": je nejednoznačný nebo není členem "*třídy*.|
|[Chyba kompilátoru C2739](compiler-error-c2739.md)|"*číslo*': explicitní pole spravovaných/WinRT dimenze musí být mezi 1 a 32|
|Chyba kompilátoru C2740|hodnota operandu "*číslo*"je mimo rozsah"*lower_bound* - *upper_bound*.|
|Chyba kompilátoru C2741|moc velká velikost rámce|
|Chyba kompilátoru C2742|Zastaralé.|
|[Chyba kompilátoru C2743](compiler-error-c2743.md)|"*typ*': nelze zachytit nativní typ s destruktorem __clrcall nebo kopírovacím konstuktorem|
|Chyba kompilátoru C2744|"*operátor*' není platný operátor CLR/WinRT|
|[Chyba kompilátoru C2745](compiler-error-c2745.md)|"*token*': Tento token nejde převést na identifikátor rozhraní|
|Chyba kompilátoru C2746|Zastaralé.|
|Chyba kompilátoru C2747|Zastaralé.|
|[Chyba kompilátoru C2748](compiler-error-c2748.md)|Vytvoření spravované/WinRT pole musí mít velikost pole nebo inicializátor pole.|
|[Chyba kompilátoru C2749](compiler-error-c2749.md)|"*typ*': můžete pouze operaci throw nebo catch popisovač pro spravovanou třídu s/clr: safe|
|[Chyba kompilátoru C2750](compiler-error-c2750.md)|"*typ*': nelze použít 'new' v rámci odkazu na typ; místo toho použijte"gcnew.|
|[Chyba kompilátoru C2751](compiler-error-c2751.md)|"*parametr*': název parametru funkce nemůže být kvalifikovaný.|
|[Chyba kompilátoru C2752](compiler-error-c2752.md)|"*šablony*': více než jedna částečná specializace odpovídá seznamu argumentů šablony|
|[Chyba kompilátoru C2753](compiler-error-c2753.md)|"*šablony*': částečná specializace se nemůže shodovat seznam argumentů pro primární šablonu|
|[Chyba kompilátoru C2754](compiler-error-c2754.md)|"*šablony*': částečná specializace nemůže mít parametr závislé šablony bez typu|
|[Chyba kompilátoru C2755](compiler-error-c2755.md)|"*parametr*': beztypový parametr částečné specializace musí být jednoduchý identifikátor.|
|[Chyba kompilátoru C2756](compiler-error-c2756.md)|"*šablony*': výchozí argumenty šablony nejsou pro částečnou specializaci povolené.|
|[Chyba kompilátoru C2757](compiler-error-c2757.md)|"*identifikátor*': symbol s tímto názvem už existuje, a proto nelze použít tento název jako název oboru názvů|
|[Chyba kompilátoru C2758](compiler-error-c2758.md)|"*člen*': člen odkazového typu musí být inicializován.|
|Chyba kompilátoru C2759|vložené sestavy assembleru vloženého kódu: *error_message*|
|[Chyba kompilátoru C2760](compiler-error-c2760.md)|Chyba syntaxe: byl očekáván '*token1*"not"*token2*.|
|[Chyba kompilátoru C2761](compiler-error-c2761.md)|"*funkce*': opětovná deklarace členské funkce nejsou povoleny|
|[Chyba kompilátoru C2762](compiler-error-c2762.md)|"*šablony*': Neplatný výraz jako argument šablony pro"*parametr*.|
|Chyba kompilátoru C2763|"*šablony*': Neplatné použití řetězcového literálu jako argumentu šablony pro"*parametr*.|
|[Chyba kompilátoru C2764](compiler-error-c2764.md)|"*parametr*': parametr šablony nepoužívá nebo není odvoditelný v částečné specializaci"*specializace*.|
|[Chyba kompilátoru C2765](compiler-error-c2765.md)|"*funkce*': explicitní specializace šablony funkcí nemůže mít žádné výchozí argumenty|
|[Chyba kompilátoru C2766](compiler-error-c2766.md)|explicitní specializace; "*specializace*' již byl definován.|
|[Chyba kompilátoru C2767](compiler-error-c2767.md)|Neshoda dimenze polí spravovaných/WinRT: byl očekáván *číslo* argumentů - *číslo* k dispozici|
|[Chyba kompilátoru C2768](compiler-error-c2768.md)|"*funkce*': Neplatné použití explicitních argumentů šablony|
|Chyba kompilátoru C2769|je nelze inicializovat složenou závorku spravované/WinRT pole v seznamu inicializátorů base/member|
|[Chyba kompilátoru C2770](compiler-error-c2770.md)|Neplatné explicitní šablony nebo generické argumenty pro '*šablony*.|
|[Chyba kompilátoru C2771](compiler-error-c2771.md)|#import je povolená jedině globální nebo obor názvů|
|Chyba kompilátoru C2772|Zastaralé.|
|[Chyba kompilátoru C2773](compiler-error-c2773.md)|#import a #using k dispozici pouze v kompilátoru jazyka C++|
|[Chyba kompilátoru C2774](compiler-error-c2774.md)|"*identifikátor*": je tato vlastnost přidružená žádná metoda put.|
|[Chyba kompilátoru C2775](compiler-error-c2775.md)|"*identifikátor*": je tato vlastnost přidružená žádná metoda get.|
|[Chyba kompilátoru C2776](compiler-error-c2776.md)|jednu vlastnost může být zadaná jenom jedna metoda get.|
|[Chyba kompilátoru C2777](compiler-error-c2777.md)|jednu vlastnost může být zadaná jenom jedna metoda put.|
|[Chyba kompilátoru C2778](compiler-error-c2778.md)|nesprávně vytvořené GUID v: __declspec(uuid())|
|[Chyba kompilátoru C2779](compiler-error-c2779.md)|"*deklarace*': metody vlastností lze přidružit pouze s nestatických datových členů|
|[Chyba kompilátoru C2780](compiler-error-c2780.md)|"*deklarace*': očekává, že *číslo* argumenty - *číslo* k dispozici|
|[Chyba kompilátoru C2781](compiler-error-c2781.md)|"*deklarace*': očekává minimálně *číslo* argument - *číslo* k dispozici|
|[Chyba kompilátoru C2782](compiler-error-c2782.md)|"*deklarace*': parametr šablony nebo generické"*parametr*' je nejednoznačný|
|[Chyba kompilátoru C2783](compiler-error-c2783.md)|"*deklarace*': nepovedlo se odvodit argument šablony nebo generické pro"*identifikátor*.|
|[Chyba kompilátoru C2784](compiler-error-c2784.md)|"*deklarace*': nepovedlo se odvodit argument šablony nebo generické pro"*type1*"z"*type2*.|
|[Chyba kompilátoru C2785](compiler-error-c2785.md)|"*declaration1*"a"*declaration2*' mají rozdílné návratové typy|
|[Chyba kompilátoru C2786](compiler-error-c2786.md)|"*typ*': Neplatný operand pro: __uuidof|
|[Chyba kompilátoru C2787](compiler-error-c2787.md)|"*identifikátor*': žádný identifikátor GUID je přidružen k tomuto objektu|
|[Chyba kompilátoru C2788](compiler-error-c2788.md)|"*identifikátor*': více než jeden identifikátor GUID přidružený k tomuto objektu|
|Chyba kompilátoru C2789|"*identifikátor*': objekt typ const-qualified musí být inicializován.|
|[Chyba kompilátoru C2790](compiler-error-c2790.md)|"super: Toto klíčové slovo jde použít jenom v těle funkce člena třídy|
|[Chyba kompilátoru C2791](compiler-error-c2791.md)|Neplatné použití "super": "*třídy*' nemá žádné základní třídy|
|[Chyba kompilátoru C2792](compiler-error-c2792.md)|'super: Toto klíčové slovo musí být následován znakem '::'|
|[Chyba kompilátoru C2793](compiler-error-c2793.md)|"*token*': Neočekávaný token za '::', identifikátor nebo klíčové slovo očekáván operátor|
|[Chyba kompilátoru C2794](compiler-error-c2794.md)|"*identifikátor*': není člen žádné přímé ani nepřímé základní třídu '*třídy*.|
|[Chyba kompilátoru C2795](compiler-error-c2795.md)|"super::*identifikátor*" není členská funkce|
|Chyba kompilátoru C2796|možnost ref new' slouží jenom k vytvoření instance typu WinRT|
|[Chyba kompilátoru C2797](compiler-error-c2797.md)|(Zastaralé) "*identifikátor*': Inicializace seznamu je uvnitř seznamu inicializátoru členů nebo nestatický datový člen inicializátor není implementována.|
|[Chyba kompilátoru C2798](compiler-error-c2798.md)|"super::*identifikátor*' je nejednoznačný|
|Chyba kompilátoru C2799|"*identifikátor*': objekt typu třídy const-qualified bez uživatelem zadaného výchozího konstruktoru musí být inicializován.|

## <a name="see-also"></a>Viz také:

[C /C++ nástroje chyby a upozornění kompilátoru a sestavení](../compiler-errors-1/c-cpp-build-errors.md) \
[Chyby kompilátoru C2000 - C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
