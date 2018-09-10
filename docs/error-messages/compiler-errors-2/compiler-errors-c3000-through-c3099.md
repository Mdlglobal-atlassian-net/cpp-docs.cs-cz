---
title: Chyby kompilátoru C3000 až C3099 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/17/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3051
- C3061
- C3064
- C3067
- C3074
- C3078
- C3079
- C3081
- C3082
- C3086
- C3088
- C3089
- C3090
- C3091
- C3092
- C3093
- C3098
helpviewer_keywords:
- C3051
- C3061
- C3064
- C3067
- C3074
- C3078
- C3079
- C3081
- C3082
- C3086
- C3088
- C3089
- C3090
- C3091
- C3092
- C3093
- C3098
dev_langs:
- C++
ms.assetid: 01b7b9cb-b351-4b5a-8cb0-1fcddb08d2ab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7565a2656bcb5c9ad10c83179b563423d42be7b5
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44319042"
---
# <a name="compiler-errors-c3000-through-c3099"></a>Chyby kompilátoru C3000 až C3099

Články v této části dokumentace vysvětlují podmnožinu chybové zprávy, které jsou generovány kompilátorem.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Chybové zprávy

|Chyba|Zpráva|
|-----------|-------------|
|Kompilátoru C3000 chyba|Zastaralé.|
|[Chyba kompilátoru C3001](compiler-error-c3001.md)|"*zpráva*': očekával se název direktivy OpenMP|
|[Chyba kompilátoru C3002](compiler-error-c3002.md)|"*name1* *name2*': několik názvů direktiv OpenMP|
|[Chyba kompilátoru C3003](compiler-error-c3003.md)|"*směrnice*': Název direktivy OpenMP není povolený po klauzulích direktiv|
|[Chyba kompilátoru C3004](compiler-error-c3004.md)|"*klauzule*': není platný na OpenMP – klauzule"*směrnice*"– direktiva|
|[Chyba kompilátoru C3005](compiler-error-c3005.md)|"*zpráva*': na OpenMP se našel neočekávaný token"*směrnice*"– direktiva|
|[Chyba kompilátoru C3006](compiler-error-c3006.md)|"*klauzule*': klauzuli OpenMP '*– direktiva*" direktivě chybí očekávaný argument|
|[Chyba kompilátoru C3007](compiler-error-c3007.md)|"*klauzule*': klauzuli OpenMP '*– direktiva*" direktiva nepřijímá argument|
|[Chyba kompilátoru C3008](compiler-error-c3008.md)|"*argument*': argumentu chybí pravá ')' na OpenMP '*– direktiva*" – direktiva|
|[Chyba kompilátoru C3009](compiler-error-c3009.md)|"*popisek*': přejděte do strukturovaného bloku OpenMP není povolený.|
|[Chyba kompilátoru C3010](compiler-error-c3010.md)|"*popisek*': přejít mimo strukturovaný blok OpenMP není povolený.|
|[Chyba kompilátoru C3011](compiler-error-c3011.md)|vložené sestavení není povolené přímo v paralelní oblasti|
|[Chyba kompilátoru C3012](compiler-error-c3012.md)|"*funkce*': vnitřní funkce není povolená přímo v paralelní oblasti|
|[Chyba kompilátoru C3013](compiler-error-c3013.md)|"*klauzule*': klauzule se může vyskytovat jenom jednou na OpenMP '*– direktiva*" – direktiva|
|[Chyba kompilátoru C3014](compiler-error-c3014.md)|byl očekáván pro smyčky po OpenMP '*– direktiva*"– direktiva|
|[Chyba kompilátoru C3015](compiler-error-c3015.md)|Inicializace v OpenMP for – příkaz má nesprávnou podobu.|
|[Chyba kompilátoru C3016](compiler-error-c3016.md)|"*identifikátor*': indexovaná proměnná příkazu for v OpenMP musí mít celočíselný typ se znaménkem|
|[Chyba kompilátoru C3017](compiler-error-c3017.md)|test ukončení v OpenMP for – příkaz má nesprávnou podobu.|
|[Chyba kompilátoru C3018](compiler-error-c3018.md)|"*identifikátor*': OpenMP 'pro' test nebo přírůstek musí používat indexovaná proměnná"*proměnnou*.|
|[Chyba kompilátoru C3019](compiler-error-c3019.md)|přírůstek v OpenMP for – příkaz má nesprávnou podobu.|
|[Chyba kompilátoru C3020](compiler-error-c3020.md)|"*proměnnou*': indexovaná proměnná OpenMP smyčku for nejde upravovat v těle smyčky|
|[Chyba kompilátoru C3021](compiler-error-c3021.md)|"*argument*': argument je prázdný v OpenMP '*směrnice*" – direktiva|
|[Chyba kompilátoru C3022](compiler-error-c3022.md)|"*– direktiva*': Neplatný typ plánu z"*– direktiva*"na OpenMP'*směrnice*" – direktiva|
|[Chyba kompilátoru C3023](compiler-error-c3023.md)|"*argument*': Parametr OpenMP se našel neočekávaný token"*– direktiva*"– klauzule|
|[Chyba kompilátoru C3024](compiler-error-c3024.md)|'schedule(runtime)': výraz chunk_size není povolený|
|[Chyba kompilátoru C3025](compiler-error-c3025.md)|"*klauzule*': očekával se celočíselný výraz|
|[Chyba kompilátoru C3026](compiler-error-c3026.md)|"*klauzule*': konstantní výraz musí být kladná|
|[Chyba kompilátoru C3027](compiler-error-c3027.md)|"*klauzule*": byl očekáván výraz aritmetické operace nebo ukazatel|
|[Chyba kompilátoru C3028](compiler-error-c3028.md)|"*člen*': Proměnná nebo statický datový člen lze použít v klauzuli data-sharing|
|[Chyba kompilátoru C3029](compiler-error-c3029.md)|"*symbol*': může být pouze jednou v data-sharing v direktivě OpenMP – klauzule|
|[Chyba kompilátoru C3030](compiler-error-c3030.md)|"*identifikátor*': Proměnná v"*– direktiva*"klauzuli/direktivě nemůže mít odkazový typ.|
|[Chyba kompilátoru C3031](compiler-error-c3031.md)|"*identifikátor*': Proměnná v klauzuli"omezení"musí mít skalární aritmetický typ.|
|[Chyba kompilátoru C3032](compiler-error-c3032.md)|"*identifikátor*': proměnné v"*klauzule*"klauzule nemůže mít nekompletní typ"*typ*.|
|[Chyba kompilátoru C3033](compiler-error-c3033.md)|"*identifikátor*": Proměnná v "*klauzule*" klauzule nemůže mít typ const-qualified|
|[Chyba kompilátoru C3034](compiler-error-c3034.md)|OpenMP '*– direktiva*"direktiva nemůže být přímo vnořená v rámci"*– direktiva*"– direktiva|
|[Chyba kompilátoru C3035](compiler-error-c3035.md)|OpenMP – "řazení" musí mít směrnice vazbu přímo na 'pro' nebo parallel for s klauzulí ordered.|
|[Chyba kompilátoru C3036](compiler-error-c3036.md)|"*klauzule*': neplatný token operátoru v klauzuli OpenMP reduction|
|[Chyba kompilátoru C3037](compiler-error-c3037.md)|"*identifikátor*": Proměnná v "*klauzule*" klauzule musí být sdílená v kontextu|
|[Chyba kompilátoru C3038](compiler-error-c3038.md)|"*identifikátor*': Proměnná v klauzuli 'private' nemůže být redukční proměnná v kontextu|
|[Chyba kompilátoru C3039](compiler-error-c3039.md)|"*identifikátor*': indexovaná proměnná v OpenMP for – příkaz nemůže být redukční proměnná|
|[Chyba kompilátoru C3040](compiler-error-c3040.md)|"*identifikátor*': typ proměnné v klauzuli 'snížení' není kompatibilní s operátorem reduction"*operátor*.|
|[Chyba kompilátoru C3041](compiler-error-c3041.md)|"*identifikátor*': Proměnná v klauzuli 'copyprivate' musí být v kontextu privátní|
|[Chyba kompilátoru C3042](compiler-error-c3042.md)|"copyprivate" a 'nowait' nemůžou být společně v OpenMP '*směrnice*"– direktiva|
|[Chyba kompilátoru C3043](compiler-error-c3043.md)|OpenMP – direktiva "kritický" nemůže být vnořená v direktivě "kritický" se stejným názvem|
|[Chyba kompilátoru C3044](compiler-error-c3044.md)|'sekce': pouze povolené přímo vnořená v direktivě OpenMP 'sections.|
|[Chyba kompilátoru C3045](compiler-error-c3045.md)|Byl očekáván složený příkaz direktivě OpenMP 'sections'. Chybí "{"|
|[Chyba kompilátoru C3046](compiler-error-c3046.md)|Chybí strukturovaný blok v oblasti OpenMP '#pragma omp sections.|
|[Chyba kompilátoru C3047](compiler-error-c3047.md)|Strukturovaný blok v OpenMP 'sections' oblast musí být předcházen '#pragma omp section'.|
|[Chyba kompilátoru C3048](compiler-error-c3048.md)|Výraz, který následuje '#pragma omp atomic' má nesprávnou podobu.|
|[Chyba kompilátoru C3049](compiler-error-c3049.md)|"*argument*': Neplatný argument v 'default' OpenMP – klauzule|
|[Chyba kompilátoru C3050](compiler-error-c3050.md)|"*třídy*': třídy ref class nemůže dědit od třídy"*identifikátor*.|
|C3051 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C3052](compiler-error-c3052.md)|"*identifikátor*': proměnná se neobjevuje v klauzuli data-sharing pod klauzulí default(none)|
|[Chyba kompilátoru C3053](compiler-error-c3053.md)|"*identifikátor*": 'threadprivate' platí pouze pro globální nebo statické datové položky|
|[Chyba kompilátoru C3054](compiler-error-c3054.md)|v obecné třídě nebo funkci aktuálně nepodporuje "#pragma omp parallel.|
|[Chyba kompilátoru C3055](compiler-error-c3055.md)|"*identifikátor*': symbol nejde odkazovat dříve, než se používá v direktivě threadprivate.|
|[Chyba kompilátoru C3056](compiler-error-c3056.md)|"*identifikátor*': symbol není ve stejném oboru jako direktiva threadprivate.|
|[Chyba kompilátoru C3057](compiler-error-c3057.md)|"*identifikátor*': dynamická inicializace symbolů 'threadprivate' v tuto chvíli nepodporuje|
|[Chyba kompilátoru C3058](compiler-error-c3058.md)|"*identifikátor*': symbol není deklarovaný jako 'threadprivate' než se použijí v klauzuli copyin.|
|[Chyba kompilátoru C3059](compiler-error-c3059.md)|"*identifikátor*": 'threadprivate' symbol nejde používat v "*klauzule*" – klauzule|
|[Chyba kompilátoru C3060](compiler-error-c3060.md)|"*identifikátor*': funkce friend nemůže být definovaná uvnitř třídy pomocí kvalifikovaného názvu (to může být jedině deklarovaná)|
|C3061 chyby kompilátoru|operátor "*– operátor*': není povolené pro výčet"*typ*"s podkladovým typem"*typ*"|
|[Chyba kompilátoru C3062](compiler-error-c3062.md)|"*identifikátor*': enumerátor vyžaduje hodnotu, protože základní typ je '*typ*.|
|[Chyba kompilátoru C3063](compiler-error-c3063.md)|operátor '*operátor*': všechny operandy musí mít stejný typ výčtu|
|C3064 chyby kompilátoru|"*identifikátor*': musí být jednoduchý typ. nebo překládat|
|[Chyba kompilátoru C3065](compiler-error-c3065.md)|deklarace vlastnosti v oboru bez třídy není povolená.|
|[Chyba kompilátoru C3066](compiler-error-c3066.md)|existuje více způsobů, že objekt tohoto typu lze volat s těmito argumenty|
|C3067 chyby kompilátoru|seznam inicializátorů nejde v předdefinované operator]|
|[Chyba kompilátoru C3068](compiler-error-c3068.md)|"*identifikátor*': funkci naked' nemůže obsahovat objekty, které by vyžadovaly vrácení zpět, pokud došlo k výjimce C++|
|[Chyba kompilátoru C3069](compiler-error-c3069.md)|operátor '*operátor*': není povolený pro výčtový typ.|
|[Chyba kompilátoru C3070](compiler-error-c3070.md)|"*identifikátor*': vlastnost nemá metodu set.|
|[Chyba kompilátoru C3071](compiler-error-c3071.md)|operátor '*operátor*"může používat jedině pro instanci ref class nebo value-type.|
|[Chyba kompilátoru C3072](compiler-error-c3072.md)|operátor '*operátor*' nelze použít pro instanci třídy ref použití operátoru unární % převeďte instanci ref třídy na typ popisovače|
|[Chyba kompilátoru C3073](compiler-error-c3073.md)|"*identifikátor*': Třída ref class nemá žádné uživatelem definovaného kopírovacího konstruktoru|
|C3074 chyby kompilátoru|pole se nedá inicializovat pomocí inicializátoru v závorkách.|
|[Chyba kompilátoru C3075](compiler-error-c3075.md)|"*identifikátor*': nemůžete vložit instanci typu odkazu"*typ*", v typu hodnoty|
|[Chyba kompilátoru C3076](compiler-error-c3076.md)|"*identifikátor*': nemůžete vložit instanci typu odkazu"*typ*", v nativním typu|
|[Chyba kompilátoru C3077](compiler-error-c3077.md)|"*identifikátor*': finalizační metoda může být jenom členem odkazového typu|
|C3078 chyby kompilátoru|Velikost pole musí být zadán ve výrazu new|
|C3079 chyby kompilátoru|seznam inicializátorů nejde používat jako pravý operand tohoto operátoru přiřazení|
|[Chyba kompilátoru C3080](compiler-error-c3080.md)|"*finalizační metodu*': finalizační metoda nemůže mít storage-class-specifier|
|C3081 chyby kompilátoru|Zastaralé.|
|C3082 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C3083](compiler-error-c3083.md)|"*identifikátor*': symbol nalevo od '::' musí být typu|
|[Chyba kompilátoru C3084](compiler-error-c3084.md)|"*identifikátor*': destruktor nebo finalizační metoda nemůže být"*– klíčové slovo*.|
|[Chyba kompilátoru C3085](compiler-error-c3085.md)|"*identifikátor*': konstruktor nemůže být"*– klíčové slovo*.|
|C3086 chyby kompilátoru|Nelze najít "std::initializer_list": je potřeba #include \<initializer_list >|
|[Chyba kompilátoru C3087](compiler-error-c3087.md)|"*identifikátor*': volání"*deklarace*"už tento člen inicializuje|
|C3088 chyby kompilátoru|"*třídy*': konstruktor atributu musí mít pojmenované formální argumenty|
|C3089 chyby kompilátoru|"*identifikátor*': název parametru se neshoduje s názvem datového členu|
|C3090 chyby kompilátoru|"*třídy*': třída atributů nemůže být šablona|
|C3091 chyby kompilátoru|"*třídy*': třída atributů nemůže mít základní třídy|
|C3092 chyby kompilátoru|"*třídy*': člen třídy atributu nemůže být bitová pole, 'static' nebo 'const'|
|C3093 chyby kompilátoru|"*typ*': typ není povolený pro člen třídy atributu '*člen*.|
|[Chyba kompilátoru C3094](compiler-error-c3094.md)|"*atribut*': anonymní použití není povolené|
|[Chyba kompilátoru C3095](compiler-error-c3095.md)|"*atribut*': atribut se nemůže opakovat|
|[Chyba kompilátoru C3096](compiler-error-c3096.md)|"*atribut*': atribut je povolený pro datové členy tříd atributů pouze|
|[Chyba kompilátoru C3097](compiler-error-c3097.md)|"*atribut*': obor atributu musí být s" sestavení: "nebo" modul: "|
|C3098 chyby kompilátoru|"*identifikátor*': atribut nemá žádné uživatelem definované konstruktory|
|[Chyba kompilátoru C3099](compiler-error-c3099.md)|"*– klíčové slovo*': použijte [System::AttributeUsageAttribute] / [Windows::Foundation::Metadata::AttributeUsageAttribute] pro atributy spravované/WinRT|
