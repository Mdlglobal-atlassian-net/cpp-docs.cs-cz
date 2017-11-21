---
title: "C2900 chyby kompilátoru prostřednictvím C2999 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
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
ms.openlocfilehash: 535a1d42d9d43022bbf513b72bac18dd5accad82
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-errors-c2900-through-c2999"></a>C2900 chyby kompilátoru prostřednictvím C2999
Články v této části dokumentace obsahují informace o část chyb kompilátoru Visual C++. Můžete přístup k informacím zde nebo v **výstup** oken v sadě Visual Studio, můžete vybrat číslo chyby a potom vyberte klávesy F1.  
  
> [!NOTE]
>  Ne každý [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] chyba je popsána v MSDN. Diagnostické zprávy v mnoha případech poskytuje všechny informace, které jsou k dispozici. Pokud se domníváte, že chybovou zprávu potřebuje další vysvětlení, můžete dejte nám vědět. Můžete použít formulář zpětné vazby na této stránce, nebo přejít na panelu nabídek v sadě Visual Studio a zvolte **pomoci**, **ohlásit chybu**, nebo můžete odeslat zprávu návrhu nebo chyb na [Microsoft Connect](http://connect.microsoft.com/VisualStudio).  
  
 Chyby a upozornění na veřejných fórech MSDN můžete najít další pomoc. [Jazyka Visual C++](http://go.microsoft.com/fwlink/?LinkId=158195) fórum je pro dotazy a v diskusích o [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] syntaxi a kompilátoru jazyka. [Visual C++ Obecné](http://go.microsoft.com/fwlink/?LinkId=158194) fórum je pro dotazy o [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] které nejsou popsané v dalších fóra. Můžete také zjistit nápovědu k nástroji chyby a upozornění na [Stack Overflow](http://stackoverflow.com/).  
  
|Chyba|Zpráva|  
|-----------|-------------|  
|C2900 chyby kompilátoru|'*deklarátor*': šablony členských funkcí v WinRT třídy musí být "privátní", "interní" nebo "chráněné privátní"|  
|C2901 chyby kompilátoru|'*identifikátor*': Obecné rozhraní nebo delegáta nemůže být veřejné|  
|[C2902 chyby kompilátoru](compiler-error-c2902.md)|'*tokenu*': Neočekávaný token následující 'šablony nebo obecného', byl očekáván identifikátor.|  
|[C2903 chyby kompilátoru](compiler-error-c2903.md)|'*identifikátor*': symbol není třída šablony nebo obecný ani šablony nebo obecný – funkce|  
|[C2904 chyby kompilátoru](compiler-error-c2904.md)|'*identifikátor*': název se již používá pro šablonu v aktuálním oboru|  
|C2905 chyby kompilátoru|Zastaralé.|  
|[C2906 chyby kompilátoru](compiler-error-c2906.md)|'*šablony*': explicitní specializace vyžaduje '<> šablony.|  
|C2907 chyby kompilátoru|zaregistrovat argument '*číslo*' neurčuje platnou číslo registru|  
|[C2908 chyby kompilátoru](compiler-error-c2908.md)|explicitní specializace; '*šablony*, již byly vytvořeny|  
|[C2909 chyby kompilátoru](compiler-error-c2909.md)|'*identifikátor*': explicitní vytvoření instance šablony funkce vyžaduje návratový typ|  
|[C2910 chyby kompilátoru](compiler-error-c2910.md)|'*funkce*': nelze explicitně specializuje|  
|[C2911 chyby kompilátoru](compiler-error-c2911.md)|'*člen*': nelze deklarovat nebo definované v aktuálním oboru|  
|[C2912 chyby kompilátoru](compiler-error-c2912.md)|explicitní specializace '*deklarace*' není specializace šablony funkcí|  
|[C2913 chyby kompilátoru](compiler-error-c2913.md)|explicitní specializace; '*deklarace*' není specializace šablony třídy|  
|[C2914 chyby kompilátoru](compiler-error-c2914.md)|'*identifikátor*': nelze odvodit šablony nebo obecného argument jako argument funkce nejednoznačný.|  
|C2915 chyby kompilátoru|'*identifikátor*': '*typ*' nelze použít přímo na povrchu publikované typu WinRT. Použití ' Platform::Object ^' místo toho k předávání tento typ|  
|C2916 chyby kompilátoru|'*identifikátor*': [FlagsAttribute] musí být zadán (pouze) na veřejné výčtu s 'bez znaménka int' základní typ|  
|[C2917 chyby kompilátoru](compiler-error-c2917.md)|'*identifikátor*': Neplatný parametr šablony|  
|[C2918 chyby kompilátoru](compiler-error-c2918.md)|'*identifikátor*': indexované vlastnosti nelze použít na povrchu publikované WinRT typu|  
|[C2919 chyby kompilátoru](compiler-error-c2919.md)|'*typ*': operátory nelze použít na povrchu publikované WinRT typu|  
|[C2920 chyby kompilátoru](compiler-error-c2920.md)|Předefinování: '*typ*': třída šablony nebo obecného již byl deklarován jako*deklarace*.|  
|[C2921 chyby kompilátoru](compiler-error-c2921.md)|Předefinování: '*typ*': třída šablony nebo obecného byly předeklarovány jako*deklarace*.|  
|C2922 chyby kompilátoru|'*rozhraní*': rozhraní A WinRT nesmí obsahovat statické členy|  
|[C2923 chyby kompilátoru](compiler-error-c2923.md)|'*typ*': '*identifikátor*'není platný šablony nebo obecného typu argument pro parametr'*parametr*.|  
|C2924 chyby kompilátoru|argument rutiny __declspec(Interrupt) není v R2|  
|C2925 chyby kompilátoru|rutiny __declspec(Interrupt) nelze použít s plovoucí desetinnou čárkou|  
|C2926 chyby kompilátoru|'*identifikátor*': inicializátoru výchozí člen není povolen pro člena anonymní struktury v rámci sjednocení|  
|[C2927 chyby kompilátoru](compiler-error-c2927.md)|'*identifikátor*': šablonu funkce musí být volána s alespoň jedním argumentem|  
|[C2928 chyby kompilátoru](compiler-error-c2928.md)|Explicitní vytvoření instance; '*identifikátor*'není funkce nebo statických dat člena třídy šablony,*třída*.|  
|[C2929 chyby kompilátoru](compiler-error-c2929.md)|'*deklarátor*': explicitní vytvoření instance; nelze explicitně vynutit a potlačit vytvoření instance šablony třídy člena|  
|[C2930 chyby kompilátoru](compiler-error-c2930.md)|'*– třída*':-id nebo obecného id šablony předefinovat jako enumerátor z ' výčtu *identifikátor*.|  
|[C2931 chyby kompilátoru](compiler-error-c2931.md)|'*class1*':-id nebo obecného id šablony předefinovat jako členské funkce '*class2*.|  
|[C2932 chyby kompilátoru](compiler-error-c2932.md)|'*typ*':-id nebo obecného id šablony předefinovat jako člena dat '*identifikátor*.|  
|[C2933 chyby kompilátoru](compiler-error-c2933.md)|'*typ*':-id nebo obecného id šablony předefinovat jako člen typedef '*identifikátor*.|  
|[C2934 chyby kompilátoru](compiler-error-c2934.md)|'*typ*':-id nebo obecného id šablony předefinovat jako vnořený '*položky*'z'*identifikátor*.|  
|[C2935 chyby kompilátoru](compiler-error-c2935.md)|'*typ*':-id nebo obecného id šablony předefinovat jako globální funkce|  
|[C2936 chyby kompilátoru](compiler-error-c2936.md)|'*typ*':-id nebo obecného id šablony předefinovat jako proměnnou a globální data|  
|[C2937 chyby kompilátoru](compiler-error-c2937.md)|'*typ*':-id nebo obecného id šablony předefinovat jako globální – typedef|  
|C2938 chyby kompilátoru|'*identifikátor*': specialize alias šablony se nezdařilo.|  
|[C2939 chyby kompilátoru](compiler-error-c2939.md)|'*typ*':-id nebo obecného id šablony předefinovat jako proměnnou a místní data|  
|[C2940 chyby kompilátoru](compiler-error-c2940.md)|'*typ*':-id nebo obecného id šablony předefinovat jako místní – typedef|  
|[C2941 chyby kompilátoru](compiler-error-c2941.md)|'*typ*':-id nebo obecného id šablony předefinovat jako místní '*položky*.|  
|[C2942 chyby kompilátoru](compiler-error-c2942.md)|'*typ*':-id nebo obecného id šablony předefinovat jako formální argument funkce|  
|[C2943 chyby kompilátoru](compiler-error-c2943.md)|'*typ*':-id nebo obecného id šablony předefinovat jako argument typu šablony|  
|[C2944 chyby kompilátoru](compiler-error-c2944.md)|'*typ*':-id nebo obecného id šablony předefinovat jako hodnotu argumentu šablony|  
|[C2945 chyby kompilátoru](compiler-error-c2945.md)|Explicitní vytvoření instance neodkazuje na specializace šablon třídy|  
|[C2946 chyby kompilátoru](compiler-error-c2946.md)|Explicitní vytvoření instance; '*typ*' není specializace šablon třídy|  
|[C2947 chyby kompilátoru](compiler-error-c2947.md)|byla očekávána ' >' ukončit šablony argumenty, nalezen '*tokenu*.|  
|[C2948 chyby kompilátoru](compiler-error-c2948.md)|Explicitní vytvoření instance; specifikátor třídy úložiště se*specifikátor*' není povolený v specializace|  
|C2949 chyby kompilátoru|/ Kernel nepodporuje thread_local|  
|C2950 chyby kompilátoru|Zastaralé.|  
|[C2951 chyby kompilátoru](compiler-error-c2951.md)|šablony/obecného deklarace jsou povolená jenom na globální, obor názvů nebo třídy oboru|  
|[C2952 chyby kompilátoru](compiler-error-c2952.md)|'*deklarace*': deklarace šablony nebo obecného seznam parametrů šablony nebo Obecné|  
|[C2953 chyby kompilátoru](compiler-error-c2953.md)|'*typ*': již byla definována šablona třídy|  
|C2954 chyby kompilátoru|instrukce word argument není v rozsahu|  
|[C2955 chyby kompilátoru](compiler-error-c2955.md)|'*typ*': použití třídy šablony nebo obecná vyžaduje šablony/obecného seznam argumentů|  
|C2956 chyby kompilátoru|jako funkce navrácení umístění by vybrán velikostí navrácení funkce 'delete – operátor (void *, size_t –)'.|  
|[C2957 chyby kompilátoru](compiler-error-c2957.md)|'*tokenu*': Neplatný oddělovač zbývajících: očekávaný ' <'|  
|[C2958 chyby kompilátoru](compiler-error-c2958.md)|levé straně *oddělovač* nalezený na '*soubor*(*line_number*)' nebyl správně shodná|  
|[C2959 chyby kompilátoru](compiler-error-c2959.md)|– Obecná třída nebo – funkce nemusí být členem šablonu|  
|C2960 chyby kompilátoru|Zastaralé.|  
|C2961 chyby kompilátoru|'*funkce*': nekonzistentní explicitní konkretizací, předchozí explicitní vytvoření instance nezadali '*argument*.|  
|[C2962 chyby kompilátoru](compiler-error-c2962.md)|Chyba syntaxe: '*tokenu*': očekávaný definice funkce člena třídy šablony do končit '}'|  
|C2963 chyby kompilátoru|Zastaralé.|  
|C2964 chyby kompilátoru|Zastaralé.|  
|C2965 chyby kompilátoru|__declspec (*specifikátor*) s/kernel nepodporuje.|  
|C2966 chyby kompilátoru|'*identifier1*': musí mít stejné __declspec(code_seg(...)) jako její základní třída*identifier2*.|  
|C2967 chyby kompilátoru|'*identifikátor*': přepsání virtuální funkce musí mít stejné __declspec(code_seg(...)) jako přepsané virtuální funkce|  
|C2968 chyby kompilátoru|'*identifikátor*': rekurzivní alias deklarace|  
|[C2969 chyby kompilátoru](compiler-error-c2969.md)|Chyba syntaxe: '*tokenu*': očekáván člen definici funkce končit '}'|  
|[C2970 chyby kompilátoru](compiler-error-c2970.md)|'*typ*': parametr šablony,*parametr*': '*argument*': výraz zahrnující objekty s vnitřní propojení nelze použít jako argument bez typu|  
|[C2971 chyby kompilátoru](compiler-error-c2971.md)|'*typ*': parametr šablony,*parametr*': '*argument*': proměnná s trvání uložení nestatické nelze použít jako argument bez typu|  
|C2972 chyby kompilátoru|'*typ*': parametr šablony,*parametr*': typ argumentu bez typu je neplatná|  
|[C2973 chyby kompilátoru](compiler-error-c2973.md)|'*šablony*': šablony neplatný argument '*číslo*.|  
|[C2974 chyby kompilátoru](compiler-error-c2974.md)|'*typ*': argument neplatný šablony nebo obecného '*parametr*', očekávaný typ|  
|[C2975 chyby kompilátoru](compiler-error-c2975.md)|'*typ*': argument neplatný šablony pro '*parametr*', očekávána konstantní výraz kompilace|  
|[C2976 chyby kompilátoru](compiler-error-c2976.md)|'*typ*': příliš málo argumentů šablony nebo Obecné|  
|[C2977 chyby kompilátoru](compiler-error-c2977.md)|'*typ*': příliš mnoho argumentů šablony nebo Obecné|  
|[C2978 chyby kompilátoru](compiler-error-c2978.md)|Chyba syntaxe: Očekává se*keyword1*"nebo"*keyword2*'; byl nalezen typ'*typ*'; jiný typ parametry nejsou podporovány v obecných typech|  
|[C2979 chyby kompilátoru](compiler-error-c2979.md)|explicitní specializace nejsou podporovány v obecných typech|  
|C2980 chyby kompilátoru|Zpracovávání výjimek v jazyce C++ nepodporuje/Kernel|  
|C2981 chyby kompilátoru|dynamické formu '*– klíčové slovo*' s/kernel nepodporuje.|  
|C2982 chyby kompilátoru|'*deklarace*': různé __declspec(code_seg(...)) používá: byl '*identifier1*'nyní'*identifier2*.|  
|C2983 chyby kompilátoru|'*deklarace*': všechny deklarace musí mít identické __declspec(code_seg(...))|  
|C2984 chyby kompilátoru|Zastaralé.|  
|C2985 chyby kompilátoru|'*argument*': argument __declspec(code_seg(...)) musí být část textu|  
|C2986 chyby kompilátoru|'*identifikátor*': __declspec(code_seg(...)) lze použít pouze na třídu nebo funkce|  
|C2987 chyby kompilátoru|deklaraci nemůže mít obě __declspec (code_seg ('*identifikátor*.)) a __declspec (code_seg ('*hodnotu*.))|  
|[C2988 chyby kompilátoru](compiler-error-c2988.md)|nerozpoznatelný šablony deklarací a definic|  
|[C2989 chyby kompilátoru](compiler-error-c2989.md)|'*třída*': třída šablony nebo obecného již byl deklarován jako šablony nebo obecný-– třída|  
|[C2990 chyby kompilátoru](compiler-error-c2990.md)|'*třída*': bez třídy šablony nebo obecného již byl deklarován jako šablony nebo obecný – třída|  
|[C2991 chyby kompilátoru](compiler-error-c2991.md)|Předefinování šablony nebo obecný parametr '*parametr*.|  
|[C2992 chyby kompilátoru](compiler-error-c2992.md)|'*třída*': neplatný nebo chybějící šablony nebo obecný parametr seznamu|  
|[C2993 chyby kompilátoru](compiler-error-c2993.md)|'*typ*': Neplatný typ pro parametr šablony bez typu '*identifikátor*.|  
|[C2994 chyby kompilátoru](compiler-error-c2994.md)|Nepojmenované – třída v seznamu parametrů šablony|  
|[C2995 chyby kompilátoru](compiler-error-c2995.md)|'*deklarace*': funkce šablona již byl definován.|  
|[C2996 chyby kompilátoru](compiler-error-c2996.md)|'*funkce*': definice šablony rekurzivní funkce|  
|C2997 chyby kompilátoru|'*funkce*': pole vázaný nelze odvodit z inicializátoru výchozí člen|  
|[C2998 chyby kompilátoru](compiler-error-c2998.md)|'*deklarátor*': nemůže být definice šablony|  
|C2999 chyby kompilátoru|Neznámá chyba Zvolte prosím příkaz se na technickou podporu v nabídce Nápověda Visual C++, nebo otevře soubor nápovědy se na technickou podporu pro další informace|  
