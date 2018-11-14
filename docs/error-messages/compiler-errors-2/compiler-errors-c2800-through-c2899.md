---
title: Chyby kompilátoru C2800 až C2899
ms.date: 11/17/2017
f1_keywords:
- C2816
- C2820
- C2822
- C2826
- C2832
- C2836
- C2837
- C2840
- C2841
- C2848
- C2851
- C2852
- C2853
- C2866
- C2880
- C2887
- C2889
- C2895
- C2899
helpviewer_keywords:
- C2816
- C2820
- C2822
- C2826
- C2832
- C2836
- C2837
- C2840
- C2841
- C2848
- C2851
- C2852
- C2853
- C2866
- C2880
- C2887
- C2889
- C2895
- C2899
ms.assetid: e5de1e92-746a-4315-a331-c5d9efb76dbb
ms.openlocfilehash: 7c35cd91f836070ff45faa489e1c16c40909f922
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51332072"
---
# <a name="compiler-errors-c2800-through-c2899"></a>Chyby kompilátoru C2800 až C2899

Články v této části dokumentace vysvětlují podmnožinu chybové zprávy, které jsou generovány kompilátorem.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Chybové zprávy

|Chyba|Zpráva|
|-----------|-------------|
|[Chyba kompilátoru C2800](compiler-error-c2800.md)|' operator *operátor*"nemohou být přetíženy|
|[Chyba kompilátoru C2801](compiler-error-c2801.md)|"*člen*' musí být Nestatický člen|
|[Chyba kompilátoru C2802](compiler-error-c2802.md)|statický člen ' operátor *operátor*' nemá žádné formální parametry|
|[Chyba kompilátoru C2803](compiler-error-c2803.md)|' operator *operátor*"musí mít aspoň jeden formální parametr typu třídy|
|[Chyba kompilátoru C2804](compiler-error-c2804.md)|binární ' operátor *operátor*' má moc velký počet parametrů|
|[Chyba kompilátoru C2805](compiler-error-c2805.md)|binární ' operátor *operátor*"moc malý počet parametrů|
|[Chyba kompilátoru C2806](compiler-error-c2806.md)|' operator *– operátor*' má moc velký počet formálních parametrů.|
|[Chyba kompilátoru C2807](compiler-error-c2807.md)|druhý formální parametr k postfixovému "operátor *operátor*' musí být"int"|
|[Chyba kompilátoru C2808](compiler-error-c2808.md)|Unární "operátor *operátor*' má moc velký počet formálních parametrů.|
|[Chyba kompilátoru C2809](compiler-error-c2809.md)|' operator *operátor*' nemá žádné formální parametry|
|[Chyba kompilátoru C2810](compiler-error-c2810.md)|"*rozhraní*': rozhraní může dědit jedině z jiného rozhraní|
|[Chyba kompilátoru C2811](compiler-error-c2811.md)|"*type1*": nejde dědit z: "*type2*", referenční třída může dědit jedině z ref class nebo interface class|
|[Chyba kompilátoru C2812](compiler-error-c2812.md)|#import není podporovaná s možnostmi/CLR: pure a/CLR: safe|
|[Chyba kompilátoru C2813](compiler-error-c2813.md)|#import není podporováno s možností/MP|
|[Chyba kompilátoru C2814](compiler-error-c2814.md)|"*člen*': nativní typ nemůže být vnořený v rámci typu spravované/WinRT"*třídy*.|
|[Chyba kompilátoru C2815](compiler-error-c2815.md)|operátor delete: první formální parametr musí být "void \*", ale "*typ*' byl použit|
|C2816 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C2817](compiler-error-c2817.md)|Návratový typ pro operátor delete musí být void.|
|[Chyba kompilátoru C2818](compiler-error-c2818.md)|použití přetíženého operátoru operator ->' je rekurzivní prostřednictvím typu "*třídy*.|
|[Chyba kompilátoru C2819](compiler-error-c2819.md)|Typ '*třídy*' nemá přetíženého členu 'operator ->.|
|C2820 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C2821](compiler-error-c2821.md)|prvním formálním parametrem pro operator new musí být parametr size_t.|
|C2822 chyby kompilátoru|místní uvolnění není na této platformě podporována.|
|[Chyba kompilátoru C2823](compiler-error-c2823.md)|šablony/obecný definice typedef je neplatné.|
|[Chyba kompilátoru C2824](compiler-error-c2824.md)|Návratový typ pro operátor new musí být "void \*.|
|[Chyba kompilátoru C2825](compiler-error-c2825.md)|'*identifikátor*': musí být třída nebo obor názvů v případě, že následuje '::'|
|C2826 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C2827](compiler-error-c2827.md)|' operator *operátor*"nedá globálně přepsat jeho unární podobou.|
|[Chyba kompilátoru C2828](compiler-error-c2828.md)|' operator *operátor*"nedá globálně přepsat jeho binární podobou.|
|[Chyba kompilátoru C2829](compiler-error-c2829.md)|' operator *operátor*' nemůže mít seznam parametrů proměnných|
|[Chyba kompilátoru C2830](compiler-error-c2830.md)|výchozí hodnoty můžou mít jenom parametry umístění pro operátor operator new.|
|[Chyba kompilátoru C2831](compiler-error-c2831.md)|' operator *– operátor*' nemůže mít výchozí parametry|
|C2832 chyby kompilátoru|"*identifikátor*': typ odkazu se nedá inicializovat pomocí hodnoty.|
|[Chyba kompilátoru C2833](compiler-error-c2833.md)|"operátor *token*" není rozpoznaná jako operátor nebo typ.|
|[Chyba kompilátoru C2834](compiler-error-c2834.md)|' operator *operátor*' musí být globálně kvalifikovaný|
|[Chyba kompilátoru C2835](compiler-error-c2835.md)|uživatelem definovaný převod "*typ*' nemá žádné formální parametry|
|C2836 chyby kompilátoru|"*identifikátor*': pouze jeden nestatický datový člen sjednocení může mít výchozí inicializátor členu|
|C2837 chyby kompilátoru|"*funkce*': nelze použít direktivy OpenMP a direktivu #pragma loop(hint_parallel) ve stejné funkci|
|[Chyba kompilátoru C2838](compiler-error-c2838.md)|"*identifikátor*': Neplatný kvalifikovaný název v deklaraci člena|
|[Chyba kompilátoru C2839](compiler-error-c2839.md)|Neplatný návratový typ '*typ*"pro přetíženou -> – operátor|
|C2840 chyby kompilátoru|argument word instrukce není konstanta.|
|C2841 chyby kompilátoru|argument registru není konstanta|
|[Chyba kompilátoru C2842](compiler-error-c2842.md)|"*třídy*': typ spravovaného/WinRT nesmí definovat vlastní 'operator new" nebo operátor delete|
|[Chyba kompilátoru C2843](compiler-error-c2843.md)|"*člen*': Nelze převzít adresu nestatický datový člen nebo metodu typu spravované/WinRT|
|[Chyba kompilátoru C2844](compiler-error-c2844.md)|"*identifikátor*': nemůže být členem rozhraní"*rozhraní*.|
|[Chyba kompilátoru C2845](compiler-error-c2845.md)|"*typ*': není povolené pro tento typ aritmetika ukazatele|
|[Chyba kompilátoru C2846](compiler-error-c2846.md)|"*rozhraní*': rozhraní nemůže mít konstruktor|
|[Chyba kompilátoru C2847](compiler-error-c2847.md)|nelze použít nastavení sizeof pro typ spravovaného/WinRT "*třídy*.|
|C2848 chyby kompilátoru|"*třídy*': typ spravovaného/WinRT nemůže být členem sjednocení|
|[Chyba kompilátoru C2849](compiler-error-c2849.md)|"*rozhraní*': rozhraní nemůže mít destruktor|
|[Chyba kompilátoru C2850](compiler-error-c2850.md)|"*vytvořit*': povolené jenom v rozsahu souboru; nemusí být ve vnořeném konstruktoru|
|C2851 chyby kompilátoru|"*výčtu*': Veřejný výčet WinRT může použít pouze"int"nebo"unsigned int"jako základní typ|
|C2852 chyby kompilátoru|"*identifikátor*': v rámci třídy mohou být inicializovány pouze datové členy|
|C2853 chyby kompilátoru|"*identifikátor*': nestatický datový člen nemůže mít typ, který obsahuje nastavení auto.|
|[Chyba kompilátoru C2854](compiler-error-c2854.md)|Chyba syntaxe v direktivě #pragma hdrstop|
|[Chyba kompilátoru C2855](compiler-error-c2855.md)|možnost příkazového řádku "*možnost*" konzistentní s předkompilovanou hlavičkou|
|[Chyba kompilátoru C2856](compiler-error-c2856.md)|#pragma hdrstop nemůže být uvnitř bloku #if.|
|[Chyba kompilátoru C2857](compiler-error-c2857.md)|"#include" výraz zadaný s možností / Yc*filename* možnost příkazového řádku se nenašel ve zdrojovém souboru|
|[Chyba kompilátoru C2858](compiler-error-c2858.md)|možnost příkazového řádku "/Yc (/Fd*filename*)" konzistentní s předkompilovanou hlavičkou, která používá "/Fd*filename*.|
|[Chyba kompilátoru C2859](compiler-error-c2859.md)|*Název souboru* není *filetype* soubor, který byl použit při vytváření této předkompilované hlavičky, znovu vytvořte předkompilované hlavičky.|
|[Chyba kompilátoru C2860](compiler-error-c2860.md)|"void" nemůže být typ argumentu, jedině (void)|
|[Chyba kompilátoru C2861](compiler-error-c2861.md)|"*deklarace*': členská funkce rozhraní nemůže být definovaná.|
|[Chyba kompilátoru C2862](compiler-error-c2862.md)|"*rozhraní*': rozhraní může mít pouze veřejné členy|
|[Chyba kompilátoru C2863](compiler-error-c2863.md)|"*rozhraní*': rozhraní nemá žádné specifikátory Friend|
|[Chyba kompilátoru C2864](compiler-error-c2864.md)|"*identifikátor*': Statický datový člen/šablony proměnné s inicializátorem ve třídě musí mít celočíselný typ const není typu volatile.|
|[Chyba kompilátoru C2865](compiler-error-c2865.md)|"*operátor*': Neplatné porovnání pro ukazatel nebo popisovač objektu|
|C2866 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C2867](compiler-error-c2867.md)|"*identifikátor*': není obor názvů|
|[Chyba kompilátoru C2868](compiler-error-c2868.md)|"*identifikátor*': Neplatná syntaxe pro deklarace using; očekávaný název kvalifikovaný|
|[Chyba kompilátoru C2869](compiler-error-c2869.md)|"*identifikátor*': již byl definován jako obor názvů|
|[Chyba kompilátoru C2870](compiler-error-c2870.md)|"*identifikátor*': definice oboru názvů musí být buď v rozsahu souboru, nebo v bezprostředně jiné definici oboru názvů|
|[Chyba kompilátoru C2871](compiler-error-c2871.md)|"*identifikátor*': obor názvů s tímto názvem neexistuje.|
|[Chyba kompilátoru C2872](compiler-error-c2872.md)|"*identifikátor*': nejednoznačný symbol|
|[Chyba kompilátoru C2873](compiler-error-c2873.md)|"*symbol*': symbol nejde používat v deklarace using|
|[Chyba kompilátoru C2874](compiler-error-c2874.md)|Using-declaration způsobí vícenásobnou deklaraci '*identifikátor*.|
|[Chyba kompilátoru C2875](compiler-error-c2875.md)|Using-declaration způsobí vícenásobnou deklaraci '*třídy*::*identifikátor*.|
|[Chyba kompilátoru C2876](compiler-error-c2876.md)|"*třídy*::*člen*': Ne všechny přetížení jsou k dispozici|
|[Chyba kompilátoru C2877](compiler-error-c2877.md)|"*člen*"není přístupný z"*třídy*.|
|[Chyba kompilátoru C2878](compiler-error-c2878.md)|"*identifikátor*': obor názvů nebo třída s tímto názvem neexistuje|
|[Chyba kompilátoru C2879](compiler-error-c2879.md)|"*identifikátor*': pouze existujícího oboru názvů může být dán alternativní název definice aliasu oboru názvů|
|C2880 chyby kompilátoru|__swi nebo __hvc vyžaduje platnou konstantu jako první argument (číslo SWI).|
|[Chyba kompilátoru C2881](compiler-error-c2881.md)|"*identifikátor*': se už používá jako alias pro"*třídy*.|
|[Chyba kompilátoru C2882](compiler-error-c2882.md)|"*identifikátor*': Neplatné použití identifikátoru oboru názvů ve výrazu|
|[Chyba kompilátoru C2883](compiler-error-c2883.md)|"*funkce*': deklarace funkce je v konfliktu s"*identifikátor*"zavedené deklarace using|
|[Chyba kompilátoru C2884](compiler-error-c2884.md)|"*identifikátor*': zavedené pomocí deklarace je v konfliktu s lokální funkcí"*funkce*.|
|[Chyba kompilátoru C2885](compiler-error-c2885.md)|"*třídy*::*identifikátor*': není platná deklarace using na netřídním oborem|
|[Chyba kompilátoru C2886](compiler-error-c2886.md)|"*třídy*::*identifikátor*': symbol nejde používat v členu using-declaration|
|C2887 chyby kompilátoru|__swi nebo __hvc nemůže mít víc než pět argumentů (číslo SWI, r0 – r3)|
|[Chyba kompilátoru C2888](compiler-error-c2888.md)|"*identifikátor*': symbol nemůže být definovaný v rámci oboru názvů '*obor názvů*.|
|C2889 chyby kompilátoru|"*třídy*': typ třídy spravované/WinRT nemůže být virtuální základní třídy|
|[Chyba kompilátoru C2890](compiler-error-c2890.md)|"*třídy*': třídy ref class. může mít pouze jednu základní třídu jiného typu než rozhraní|
|[Chyba kompilátoru C2891](compiler-error-c2891.md)|"*parametr*': nejde adresovat parametr šablony|
|[Chyba kompilátoru C2892](compiler-error-c2892.md)|lokální třída Local nebude mít šablony členů|
|[Chyba kompilátoru C2893](compiler-error-c2893.md)|Nepovedlo se specializovat šablonu funkcí "*šablony*.|
|[Chyba kompilátoru C2894](compiler-error-c2894.md)|šablony nemůžou být deklarované mít "c."|
|C2895 chyby kompilátoru|"*deklarace*': nejde explicitně vytvářet instance šablony funkcí, které jsou deklarované v rámci atributu dllimport|
|[Chyba kompilátoru C2896](compiler-error-c2896.md)|"*function1*': nelze použít funkci šablony nebo generické"*function2*' jako argument funkce|
|[Chyba kompilátoru C2897](compiler-error-c2897.md)|destruktor nebo finalizační metoda nemůže být šablona – funkce|
|[Chyba kompilátoru C2898](compiler-error-c2898.md)|"*deklarace*': šablony členských funkcí nemůže být virtuální|
|C2899 chyby kompilátoru|Zastaralé.|
