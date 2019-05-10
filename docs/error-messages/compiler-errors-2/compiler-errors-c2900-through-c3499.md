---
title: Compiler errors C2900 Through C2999
ms.date: 04/21/2019
f1_keywords:
- C2900
- C2901
- C2905
- C2907
- C2915
- C2916
- C2922
- C2924
- C2925
- C2926
- C2938
- C2949
- C2950
- C2954
- C2956
- C2960
- C2961
- C2963
- C2964
- C2965
- C2966
- C2967
- C2968
- C2972
- C2980
- C2981
- C2982
- C2983
- C2984
- C2985
- C2986
- C2987
- C2997
- C2999
helpviewer_keywords:
- C2900
- C2901
- C2905
- C2907
- C2915
- C2916
- C2922
- C2924
- C2925
- C2926
- C2938
- C2949
- C2950
- C2954
- C2956
- C2960
- C2961
- C2963
- C2964
- C2965
- C2966
- C2967
- C2968
- C2972
- C2980
- C2981
- C2982
- C2983
- C2984
- C2985
- C2986
- C2987
- C2997
- C2999
ms.assetid: e3440738-e11b-4878-9ae3-6bc6c53ba461
ms.openlocfilehash: 5d443153582921775a72e5af647d65b102b80b0b
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64857224"
---
# <a name="compiler-errors-c2900-through-c2999"></a>Compiler errors C2900 Through C2999

Články v této části dokumentace vysvětlují podmnožinu chybové zprávy, které jsou generovány kompilátorem.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Chybové zprávy

|Chyba|Message|
|-----------|-------------|
|Chyba kompilátoru C2900|"*deklarátor*': šablony členských funkcí v třídách WinRT musí být"Soukromé","vnitřní"nebo protected private|
|Chyba kompilátoru C2901|"*identifikátor*": Obecná rozhraní nebo delegát nemůžou být veřejné|
|[Chyba kompilátoru C2902](compiler-error-c2902.md)|"*token*': Neočekávaný token následující"šablony nebo generické', byl očekáván identifikátor|
|[Chyba kompilátoru C2903](compiler-error-c2903.md)|"*identifikátor*': symbol není šablony třídy nebo generické ani šablony/obecný – funkce|
|[Chyba kompilátoru C2904](compiler-error-c2904.md)|"*identifikátor*': název se už používá pro šablonu v aktuálním rozsahu.|
|Chyba kompilátoru C2905|Zastaralé.|
|[Chyba kompilátoru C2906](compiler-error-c2906.md)|"*šablony*': explicitní specializace vyžaduje"<> šablony.|
|Chyba kompilátoru C2907|argument registru "*číslo*' neurčuje platné číslo registru|
|[Chyba kompilátoru C2908](compiler-error-c2908.md)|explicitní specializace; "*šablony*' již byla vytvořena|
|[Chyba kompilátoru C2909](compiler-error-c2909.md)|"*identifikátor*': explicitní vytváření instancí šablony funkcí vyžaduje návratový typ.|
|[Chyba kompilátoru C2910](compiler-error-c2910.md)|"*funkce*': nemůže být explicitně specializovaný.|
|[Chyba kompilátoru C2911](compiler-error-c2911.md)|"*člen*': nelze deklarovat nebo definovat v aktuálním rozsahu.|
|[Chyba kompilátoru C2912](compiler-error-c2912.md)|explicitní specializace "*deklarace*" není specializací šablony funkcí|
|[Chyba kompilátoru C2913](compiler-error-c2913.md)|explicitní specializace; "*deklarace*" není specializací šablony třídy|
|[Chyba kompilátoru C2914](compiler-error-c2914.md)|"*identifikátor*': nelze odvodit argument šablony nebo generické jako argument funkce je nejednoznačný|
|Chyba kompilátoru C2915|"*identifikátor*": "*typ*' nelze použít přímo na publikované ploše typu WinRT. Použití "Platform::Object ^' místo toho k předání tohoto typu|
|Chyba kompilátoru C2916|"*identifikátor*": [FlagsAttribute] musí být zadaný (jenom) pro výčet public pomocí "unsigned int" základní typ|
|[Chyba kompilátoru C2917](compiler-error-c2917.md)|"*identifikátor*': Neplatné zadání template-parameter|
|[Chyba kompilátoru C2918](compiler-error-c2918.md)|"*identifikátor*": Indexované vlastnosti nejde používat na publikované ploše typu WinRT|
|[Chyba kompilátoru C2919](compiler-error-c2919.md)|"*typ*": Operátory nejde používat na publikované ploše typu WinRT|
|[Chyba kompilátoru C2920](compiler-error-c2920.md)|Předefinování: "*typ*': třída šablony nebo generické již byl deklarován jako*deklarace*"|
|[Chyba kompilátoru C2921](compiler-error-c2921.md)|Předefinování: "*typ*': třída šablony nebo generické byly předeklarovány jako*deklarace*"|
|Chyba kompilátoru C2922|"*rozhraní*": Rozhraní WinRT nemůže obsahovat statické členy|
|[Chyba kompilátoru C2923](compiler-error-c2923.md)|"*typ*": "*identifikátor*'není platnou šablonu/obecný argument typu pro parametr'*parametr*.|
|Chyba kompilátoru C2924|argument rutiny __declspec(Interrupt) není v R2|
|Chyba kompilátoru C2925|rutina __declspec(Interrupt) nemůže používat s plovoucí desetinnou čárkou|
|Chyba kompilátoru C2926|"*identifikátor*': výchozí inicializátor členu se nepovoluje pro člen anonymní struktury v rámci sjednocení|
|[Chyba kompilátoru C2927](compiler-error-c2927.md)|"*identifikátor*': Šablona funkcí se musí volat s alespoň jeden argument.|
|[Chyba kompilátoru C2928](compiler-error-c2928.md)|explicitní vytváření instancí; "*identifikátor*'není funkce nebo statický datový člen template-class'*třídy*.|
|[Chyba kompilátoru C2929](compiler-error-c2929.md)|"*deklarátor*': explicitní vytváření instancí; nejde explicitně vynutit a potlačit vytváření instancí členu šablony třídy|
|[Chyba kompilátoru C2930](compiler-error-c2930.md)|"*třídy*': id nebo obecný id šablony se předefinovalo jako enumerátor" výčtu *identifikátor*.|
|[Chyba kompilátoru C2931](compiler-error-c2931.md)|"*class1*': id nebo obecný id šablony se předefinovalo jako členské funkce typu"*class2*.|
|[Chyba kompilátoru C2932](compiler-error-c2932.md)|"*typ*': id nebo obecný id šablony se předefinovalo jako datový člen třídy"*identifikátor*.|
|[Chyba kompilátoru C2933](compiler-error-c2933.md)|"*typ*': id nebo obecný id šablony se předefinovalo jako člen typedef"*identifikátor*"|
|[Chyba kompilátoru C2934](compiler-error-c2934.md)|"*typ*': id nebo obecný id šablony se předefinovalo jako vnořený"*položky*"z"*identifikátor*.|
|[Chyba kompilátoru C2935](compiler-error-c2935.md)|"*typ*': id nebo obecný id šablony se předefinovalo jako globální funkce|
|[Chyba kompilátoru C2936](compiler-error-c2936.md)|"*typ*': id nebo obecný id šablony se předefinovalo jako proměnnou globálních dat|
|[Chyba kompilátoru C2937](compiler-error-c2937.md)|"*typ*': id nebo obecný id šablony se předefinovalo jako globální definice typedef|
|Chyba kompilátoru C2938|"*identifikátor*": Nepovedlo se specializovat šablonu aliasů|
|[Chyba kompilátoru C2939](compiler-error-c2939.md)|"*typ*': id nebo obecný id šablony se předefinovalo jako místní datová proměnná|
|[Chyba kompilátoru C2940](compiler-error-c2940.md)|"*typ*': id nebo obecný id šablony se předefinovalo jako místní – typedef|
|[Chyba kompilátoru C2941](compiler-error-c2941.md)|"*typ*': id nebo obecný id šablony se předefinovalo jako místní"*položky*.|
|[Chyba kompilátoru C2942](compiler-error-c2942.md)|"*typ*': id nebo obecný id šablony se předefinovalo jako formální argument funkce|
|[Chyba kompilátoru C2943](compiler-error-c2943.md)|"*typ*': id nebo obecný id šablony se předefinovalo jako argument typu šablony|
|[Chyba kompilátoru C2944](compiler-error-c2944.md)|"*typ*': id nebo obecný id šablony se předefinovalo jako hodnotu argumentu šablony|
|[Chyba kompilátoru C2945](compiler-error-c2945.md)|explicitní vytváření instancí neodkazuje na specializaci šablony třídy|
|[Chyba kompilátoru C2946](compiler-error-c2946.md)|explicitní vytváření instancí; "*typ*" není specializace template-class|
|[Chyba kompilátoru C2947](compiler-error-c2947.md)|Očekává se ' >' ukončit argumenty šablony, nalezeno '*token*"|
|[Chyba kompilátoru C2948](compiler-error-c2948.md)|explicitní vytváření instancí; specifikátor třídy úložiště "*specifikátor*' není pro specializaci povolený.|
|Chyba kompilátoru C2949|možnost thread_local není podporovaná s možností/Kernel.|
|Chyba kompilátoru C2950|Zastaralé.|
|[Chyba kompilátoru C2951](compiler-error-c2951.md)|Šablona nebo obecná deklarace jsou povolené jenom v globálním, oboru názvů nebo třídy|
|[Chyba kompilátoru C2952](compiler-error-c2952.md)|"*deklarace*': chybějící seznam parametrů šablony nebo generické deklarace šablony/Obecné|
|[Chyba kompilátoru C2953](compiler-error-c2953.md)|"*typ*': Šablona tříd už je definovaný|
|Chyba kompilátoru C2954|argument word instrukce není v rozsahu|
|[Chyba kompilátoru C2955](compiler-error-c2955.md)|"*typ*': použití třídy šablony nebo generické vyžaduje seznam argumentů šablony nebo generické|
|Chyba kompilátoru C2956|vybrala jako funkce dealokace vybere velikostí dealokace funkce 'operator delete (void *, size_t)".|
|[Chyba kompilátoru C2957](compiler-error-c2957.md)|'*token*': Neplatný levý oddělovač: byl očekáván ' <'|
|[Chyba kompilátoru C2958](compiler-error-c2958.md)|levé straně *oddělovač* nalezený na "*souboru*(*line_number*)" se neshodovala. správně|
|[Chyba kompilátoru C2959](compiler-error-c2959.md)|Obecná třída nebo funkce nemůže být členem šablony|
|Chyba kompilátoru C2960|Zastaralé.|
|Chyba kompilátoru C2961|"*funkce*': nekonzistentní explicitní vytváření instancí, předchozí explicitní vytváření instancí nejsou specifikovány"*argument*.|
|[Chyba kompilátoru C2962](compiler-error-c2962.md)|Chyba syntaxe: "*token*": byl očekáván definice třídy šablony členské funkce bude končit '}'|
|Chyba kompilátoru C2963|Zastaralé.|
|Chyba kompilátoru C2964|Zastaralé.|
|Chyba kompilátoru C2965|__declspec (*specifikátor*) není podporovaná s možností/Kernel.|
|Chyba kompilátoru C2966|"*identifier1*': musí mít stejné __declspec(code_seg(...)) jako svou základní třídou*identifier2*.|
|Chyba kompilátoru C2967|"*identifikátor*': přepisující virtuální funkce musí mít stejné __declspec(code_seg(...)) jako přepsané virtuální funkce|
|Chyba kompilátoru C2968|"*identifikátor*': rekurzivní deklarace aliasu|
|[Chyba kompilátoru C2969](compiler-error-c2969.md)|Chyba syntaxe: "*token*": byl očekáván definice členské funkce bude končit '}'|
|[Chyba kompilátoru C2970](compiler-error-c2970.md)|"*typ*': parametr šablony"*parametr*":"*argument*': výraz zahrnuje objekty s vnitřním propojením nelze použít jako beztypový argument|
|[Chyba kompilátoru C2971](compiler-error-c2971.md)|"*typ*': parametr šablony"*parametr*":"*argument*': proměnná s trváním úložiště nestatické nelze použít jako beztypový argument|
|Chyba kompilátoru C2972|"*typ*': parametr šablony"*parametr*': typ beztypového argumentu není platný|
|[Chyba kompilátoru C2973](compiler-error-c2973.md)|"*šablony*': Neplatný argument šablony"*číslo*.|
|[Chyba kompilátoru C2974](compiler-error-c2974.md)|"*typ*': Neplatný šablony/obecný argument pro"*parametr*', byl očekáván typ|
|[Chyba kompilátoru C2975](compiler-error-c2975.md)|"*typ*': Neplatný argument šablony pro"*parametr*", očekával se konstantní výraz za kompilace|
|[Chyba kompilátoru C2976](compiler-error-c2976.md)|"*typ*': moc malý počet argumentů šablony nebo generické|
|[Chyba kompilátoru C2977](compiler-error-c2977.md)|"*typ*': příliš mnoho argumentů šablony nebo generické|
|[Chyba kompilátoru C2978](compiler-error-c2978.md)|Chyba syntaxe: byl očekáván '*keyword1*"nebo"*keyword2*"; našel se typ"*typ*"; bez typu v obecných typech nejsou podporované parametry|
|[Chyba kompilátoru C2979](compiler-error-c2979.md)|explicitní specializace nejsou v obecných typech podporované.|
|Chyba kompilátoru C2980|Zpracování výjimek jazyka C++ není podporovaná s možností/Kernel.|
|Chyba kompilátoru C2981|Dynamická podoba "*– klíčové slovo*" není podporovaná s možností/Kernel.|
|Chyba kompilátoru C2982|"*deklarace*': používá jiný __declspec(code_seg(...)): byl"*identifier1*'now'*identifier2*"|
|Chyba kompilátoru C2983|"*deklarace*': všechny deklarace musí mít stejné __declspec(code_seg(...))|
|Chyba kompilátoru C2984|Zastaralé.|
|Chyba kompilátoru C2985|"*argument*': argument __declspec(code_seg(...)) musí být textový oddíl|
|Chyba kompilátoru C2986|"*identifikátor*': __declspec(code_seg(...)) může používat jedině pro třídu nebo funkci|
|Chyba kompilátoru C2987|deklarace nemůže mít oba __declspec (code_seg ("*identifikátor*")) a __declspec (code_seg ("*hodnotu*"))|
|[Chyba kompilátoru C2988](compiler-error-c2988.md)|deklarace/definice šablony nelze rozpoznat|
|[Chyba kompilátoru C2989](compiler-error-c2989.md)|"*třídy*': třída šablony nebo generické již byla deklarována jako mimo třídu šablony nebo generické|
|[Chyba kompilátoru C2990](compiler-error-c2990.md)|"*třídy*': bez třídy šablony nebo generické již byla deklarována jako třída šablony nebo generické|
|[Chyba kompilátoru C2991](compiler-error-c2991.md)|Předefinování parametru šablony/generické:*parametr*.|
|[Chyba kompilátoru C2992](compiler-error-c2992.md)|"*třídy*': šablony nebo generické neplatné nebo chybějící seznam parametrů|
|[Chyba kompilátoru C2993](compiler-error-c2993.md)|"*typ*': Neplatný typ pro parametr šablony bez typu"*identifikátor*.|
|[Chyba kompilátoru C2994](compiler-error-c2994.md)|Nepojmenovaná třída v seznamu parametrů šablony|
|[Chyba kompilátoru C2995](compiler-error-c2995.md)|"*deklarace*': Šablona funkcí už je definovaná.|
|[Compiler error C2996](compiler-error-c2996.md)|"*funkce*': rekurzivní definice šablony funkcí|
|Chyba kompilátoru C2997|"*funkce*': hranice pole se nedá dedukovat z výchozí inicializátor členu|
|[Chyba kompilátoru C2998](compiler-error-c2998.md)|"*deklarátor*': nemůže být definice šablony|
|Chyba kompilátoru C2999|Neznámá chyba Zvolte prosím příkaz technická podpora v nabídce Nápověda pro Visual C++, nebo otevřete soubor nápovědy technické podpory pro další informace|

## <a name="see-also"></a>Viz také:

[C /C++ nástroje chyby a upozornění kompilátoru a sestavení](../compiler-errors-1/c-cpp-build-errors.md) \
[Chyby kompilátoru C2000 - C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
