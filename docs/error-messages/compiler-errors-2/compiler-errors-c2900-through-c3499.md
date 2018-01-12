---
title: "C2900 chyby kompilátoru prostřednictvím C2999 | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
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
dev_langs: C++
ms.assetid: e3440738-e11b-4878-9ae3-6bc6c53ba461
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9b5e2711b8517a03792cdef312e8cd8ee3b4fe72
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-errors-c2900-through-c2999"></a>C2900 chyby kompilátoru prostřednictvím C2999

Články v této části dokumentace vysvětlují podmnožinu chybové zprávy, které jsou generované kompilátorem.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Chybové zprávy

|Chyba|Zpráva|
|-----------|-------------|
|C2900 chyby kompilátoru|'*deklarátor*': šablony členských funkcí v WinRT třídy musí být "privátní", "interní" nebo "chráněné privátní"|
|C2901 chyby kompilátoru|'*identifikátor*': Obecné rozhraní nebo delegáta nemůže být veřejné|
|[Chyba kompilátoru C2902](compiler-error-c2902.md)|'*tokenu*': Neočekávaný token následující 'šablony nebo obecného', byl očekáván identifikátor.|
|[Chyba kompilátoru C2903](compiler-error-c2903.md)|'*identifikátor*': symbol není třída šablony nebo obecný ani šablony nebo obecný – funkce|
|[Chyba kompilátoru C2904](compiler-error-c2904.md)|'*identifikátor*': název se již používá pro šablonu v aktuálním oboru|
|C2905 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C2906](compiler-error-c2906.md)|'*šablony*': explicitní specializace vyžaduje '<> šablony.|
|C2907 chyby kompilátoru|zaregistrovat argument '*číslo*' neurčuje platnou číslo registru|
|[Chyba kompilátoru C2908](compiler-error-c2908.md)|explicitní specializace; '*šablony*, již byly vytvořeny|
|[Chyba kompilátoru C2909](compiler-error-c2909.md)|'*identifikátor*': explicitní vytvoření instance šablony funkce vyžaduje návratový typ|
|[Chyba kompilátoru C2910](compiler-error-c2910.md)|'*funkce*': nelze explicitně specializuje|
|[Chyba kompilátoru C2911](compiler-error-c2911.md)|'*člen*': nelze deklarovat nebo definované v aktuálním oboru|
|[Chyba kompilátoru C2912](compiler-error-c2912.md)|explicitní specializace '*deklarace*' není specializace šablony funkcí|
|[Chyba kompilátoru C2913](compiler-error-c2913.md)|explicitní specializace; '*deklarace*' není specializace šablony třídy|
|[Chyba kompilátoru C2914](compiler-error-c2914.md)|'*identifikátor*': nelze odvodit šablony nebo obecného argument jako argument funkce nejednoznačný.|
|C2915 chyby kompilátoru|'*identifikátor*': '*typ*' nelze použít přímo na povrchu publikované typu WinRT. Použití ' Platform::Object ^' místo toho k předávání tento typ|
|C2916 chyby kompilátoru|'*identifikátor*': [FlagsAttribute] musí být zadán (pouze) na veřejné výčtu s 'bez znaménka int' základní typ|
|[Chyba kompilátoru C2917](compiler-error-c2917.md)|'*identifikátor*': Neplatný parametr šablony|
|[Chyba kompilátoru C2918](compiler-error-c2918.md)|'*identifikátor*': indexované vlastnosti nelze použít na povrchu publikované WinRT typu|
|[Chyba kompilátoru C2919](compiler-error-c2919.md)|'*typ*': operátory nelze použít na povrchu publikované WinRT typu|
|[Chyba kompilátoru C2920](compiler-error-c2920.md)|Předefinování: '*typ*': třída šablony nebo obecného již byl deklarován jako*deklarace*.|
|[Chyba kompilátoru C2921](compiler-error-c2921.md)|Předefinování: '*typ*': třída šablony nebo obecného byly předeklarovány jako*deklarace*.|
|C2922 chyby kompilátoru|'*rozhraní*': rozhraní A WinRT nesmí obsahovat statické členy|
|[Chyba kompilátoru C2923](compiler-error-c2923.md)|'*typ*': '*identifikátor*'není platný šablony nebo obecného typu argument pro parametr'*parametr*.|
|C2924 chyby kompilátoru|argument rutiny __declspec(Interrupt) není v R2|
|C2925 chyby kompilátoru|rutiny __declspec(Interrupt) nelze použít s plovoucí desetinnou čárkou|
|C2926 chyby kompilátoru|'*identifikátor*': inicializátoru výchozí člen není povolen pro člena anonymní struktury v rámci sjednocení|
|[Chyba kompilátoru C2927](compiler-error-c2927.md)|'*identifikátor*': šablonu funkce musí být volána s alespoň jedním argumentem|
|[Chyba kompilátoru C2928](compiler-error-c2928.md)|Explicitní vytvoření instance; '*identifikátor*'není funkce nebo statických dat člena třídy šablony,*třída*.|
|[Chyba kompilátoru C2929](compiler-error-c2929.md)|'*deklarátor*': explicitní vytvoření instance; nelze explicitně vynutit a potlačit vytvoření instance šablony třídy člena|
|[Chyba kompilátoru C2930](compiler-error-c2930.md)|'*– třída*':-id nebo obecného id šablony předefinovat jako enumerátor z ' výčtu *identifikátor*.|
|[Chyba kompilátoru C2931](compiler-error-c2931.md)|'*class1*':-id nebo obecného id šablony předefinovat jako členské funkce '*class2*.|
|[Chyba kompilátoru C2932](compiler-error-c2932.md)|'*typ*':-id nebo obecného id šablony předefinovat jako člena dat '*identifikátor*.|
|[Chyba kompilátoru C2933](compiler-error-c2933.md)|'*typ*':-id nebo obecného id šablony předefinovat jako člen typedef '*identifikátor*.|
|[Chyba kompilátoru C2934](compiler-error-c2934.md)|'*typ*':-id nebo obecného id šablony předefinovat jako vnořený '*položky*'z'*identifikátor*.|
|[Chyba kompilátoru C2935](compiler-error-c2935.md)|'*typ*':-id nebo obecného id šablony předefinovat jako globální funkce|
|[Chyba kompilátoru C2936](compiler-error-c2936.md)|'*typ*':-id nebo obecného id šablony předefinovat jako proměnnou a globální data|
|[Chyba kompilátoru C2937](compiler-error-c2937.md)|'*typ*':-id nebo obecného id šablony předefinovat jako globální – typedef|
|C2938 chyby kompilátoru|'*identifikátor*': specialize alias šablony se nezdařilo.|
|[Chyba kompilátoru C2939](compiler-error-c2939.md)|'*typ*':-id nebo obecného id šablony předefinovat jako proměnnou a místní data|
|[Chyba kompilátoru C2940](compiler-error-c2940.md)|'*typ*':-id nebo obecného id šablony předefinovat jako místní – typedef|
|[Chyba kompilátoru C2941](compiler-error-c2941.md)|'*typ*':-id nebo obecného id šablony předefinovat jako místní '*položky*.|
|[Chyba kompilátoru C2942](compiler-error-c2942.md)|'*typ*':-id nebo obecného id šablony předefinovat jako formální argument funkce|
|[Chyba kompilátoru C2943](compiler-error-c2943.md)|'*typ*':-id nebo obecného id šablony předefinovat jako argument typu šablony|
|[Chyba kompilátoru C2944](compiler-error-c2944.md)|'*typ*':-id nebo obecného id šablony předefinovat jako hodnotu argumentu šablony|
|[Chyba kompilátoru C2945](compiler-error-c2945.md)|Explicitní vytvoření instance neodkazuje na specializace šablon třídy|
|[Chyba kompilátoru C2946](compiler-error-c2946.md)|Explicitní vytvoření instance; '*typ*' není specializace šablon třídy|
|[Chyba kompilátoru C2947](compiler-error-c2947.md)|byla očekávána ' >' ukončit šablony argumenty, nalezen '*tokenu*.|
|[Chyba kompilátoru C2948](compiler-error-c2948.md)|Explicitní vytvoření instance; specifikátor třídy úložiště se*specifikátor*' není povolený v specializace|
|C2949 chyby kompilátoru|/ Kernel nepodporuje thread_local|
|C2950 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C2951](compiler-error-c2951.md)|šablony/obecného deklarace jsou povolená jenom na globální, obor názvů nebo třídy oboru|
|[Chyba kompilátoru C2952](compiler-error-c2952.md)|'*deklarace*': deklarace šablony nebo obecného seznam parametrů šablony nebo Obecné|
|[Chyba kompilátoru C2953](compiler-error-c2953.md)|'*typ*': již byla definována šablona třídy|
|C2954 chyby kompilátoru|instrukce word argument není v rozsahu|
|[Chyba kompilátoru C2955](compiler-error-c2955.md)|'*typ*': použití třídy šablony nebo obecná vyžaduje šablony/obecného seznam argumentů|
|C2956 chyby kompilátoru|jako funkce navrácení umístění by vybrán velikostí navrácení funkce 'delete – operátor (void *, size_t –)'.|
|[Chyba kompilátoru C2957](compiler-error-c2957.md)|'*tokenu*': Neplatný oddělovač zbývajících: očekávaný ' <'|
|[Chyba kompilátoru C2958](compiler-error-c2958.md)|levé straně *oddělovač* nalezený na '*soubor*(*line_number*)' nebyl správně shodná|
|[Chyba kompilátoru C2959](compiler-error-c2959.md)|– Obecná třída nebo – funkce nemusí být členem šablonu|
|C2960 chyby kompilátoru|Zastaralé.|
|C2961 chyby kompilátoru|'*funkce*': nekonzistentní explicitní konkretizací, předchozí explicitní vytvoření instance nezadali '*argument*.|
|[Chyba kompilátoru C2962](compiler-error-c2962.md)|Chyba syntaxe: '*tokenu*': očekávaný definice funkce člena třídy šablony do končit '}'|
|C2963 chyby kompilátoru|Zastaralé.|
|C2964 chyby kompilátoru|Zastaralé.|
|C2965 chyby kompilátoru|__declspec (*specifikátor*) s/kernel nepodporuje.|
|C2966 chyby kompilátoru|'*identifier1*': musí mít stejné __declspec(code_seg(...)) jako její základní třída*identifier2*.|
|C2967 chyby kompilátoru|'*identifikátor*': přepsání virtuální funkce musí mít stejné __declspec(code_seg(...)) jako přepsané virtuální funkce|
|C2968 chyby kompilátoru|'*identifikátor*': rekurzivní alias deklarace|
|[Chyba kompilátoru C2969](compiler-error-c2969.md)|Chyba syntaxe: '*tokenu*': očekáván člen definici funkce končit '}'|
|[Chyba kompilátoru C2970](compiler-error-c2970.md)|'*typ*': parametr šablony,*parametr*': '*argument*': výraz zahrnující objekty s vnitřní propojení nelze použít jako argument bez typu|
|[Chyba kompilátoru C2971](compiler-error-c2971.md)|'*typ*': parametr šablony,*parametr*': '*argument*': proměnná s trvání uložení nestatické nelze použít jako argument bez typu|
|C2972 chyby kompilátoru|'*typ*': parametr šablony,*parametr*': typ argumentu bez typu je neplatná|
|[Chyba kompilátoru C2973](compiler-error-c2973.md)|'*šablony*': šablony neplatný argument '*číslo*.|
|[Chyba kompilátoru C2974](compiler-error-c2974.md)|'*typ*': argument neplatný šablony nebo obecného '*parametr*', očekávaný typ|
|[Chyba kompilátoru C2975](compiler-error-c2975.md)|'*typ*': argument neplatný šablony pro '*parametr*', očekávána konstantní výraz kompilace|
|[Chyba kompilátoru C2976](compiler-error-c2976.md)|'*typ*': příliš málo argumentů šablony nebo Obecné|
|[Chyba kompilátoru C2977](compiler-error-c2977.md)|'*typ*': příliš mnoho argumentů šablony nebo Obecné|
|[Chyba kompilátoru C2978](compiler-error-c2978.md)|Chyba syntaxe: Očekává se*keyword1*"nebo"*keyword2*'; byl nalezen typ'*typ*'; jiný typ parametry nejsou podporovány v obecných typech|
|[Chyba kompilátoru C2979](compiler-error-c2979.md)|explicitní specializace nejsou podporovány v obecných typech|
|C2980 chyby kompilátoru|Zpracovávání výjimek v jazyce C++ nepodporuje/Kernel|
|C2981 chyby kompilátoru|dynamické formu '*– klíčové slovo*' s/kernel nepodporuje.|
|C2982 chyby kompilátoru|'*deklarace*': různé __declspec(code_seg(...)) používá: byl '*identifier1*'nyní'*identifier2*.|
|C2983 chyby kompilátoru|'*deklarace*': všechny deklarace musí mít identické __declspec(code_seg(...))|
|C2984 chyby kompilátoru|Zastaralé.|
|C2985 chyby kompilátoru|'*argument*': argument __declspec(code_seg(...)) musí být část textu|
|C2986 chyby kompilátoru|'*identifikátor*': __declspec(code_seg(...)) lze použít pouze na třídu nebo funkce|
|C2987 chyby kompilátoru|deklaraci nemůže mít obě __declspec (code_seg ('*identifikátor*.)) a __declspec (code_seg ('*hodnotu*.))|
|[Chyba kompilátoru C2988](compiler-error-c2988.md)|nerozpoznatelný šablony deklarací a definic|
|[Chyba kompilátoru C2989](compiler-error-c2989.md)|'*třída*': třída šablony nebo obecného již byl deklarován jako šablony nebo obecný-– třída|
|[Chyba kompilátoru C2990](compiler-error-c2990.md)|'*třída*': bez třídy šablony nebo obecného již byl deklarován jako šablony nebo obecný – třída|
|[Chyba kompilátoru C2991](compiler-error-c2991.md)|Předefinování šablony nebo obecný parametr '*parametr*.|
|[Chyba kompilátoru C2992](compiler-error-c2992.md)|'*třída*': neplatný nebo chybějící šablony nebo obecný parametr seznamu|
|[Chyba kompilátoru C2993](compiler-error-c2993.md)|'*typ*': Neplatný typ pro parametr šablony bez typu '*identifikátor*.|
|[Chyba kompilátoru C2994](compiler-error-c2994.md)|Nepojmenované – třída v seznamu parametrů šablony|
|[Chyba kompilátoru C2995](compiler-error-c2995.md)|'*deklarace*': funkce šablona již byl definován.|
|[Chyba kompilátoru C2996](compiler-error-c2996.md)|'*funkce*': definice šablony rekurzivní funkce|
|C2997 chyby kompilátoru|'*funkce*': pole vázaný nelze odvodit z inicializátoru výchozí člen|
|[Chyba kompilátoru C2998](compiler-error-c2998.md)|'*deklarátor*': nemůže být definice šablony|
|C2999 chyby kompilátoru|Neznámá chyba Zvolte prosím příkaz se na technickou podporu v nabídce Nápověda Visual C++, nebo otevře soubor nápovědy se na technickou podporu pro další informace|
