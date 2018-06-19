---
title: C3000 chyby kompilátoru prostřednictvím C3099 | Microsoft Docs
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
ms.openlocfilehash: d0941b2bd6b998e8beb18fa7e5960aa93beb6a80
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33284716"
---
# <a name="compiler-errors-c3000-through-c3099"></a>C3000 chyby kompilátoru prostřednictvím C3099

Články v této části dokumentace vysvětlují podmnožinu chybové zprávy, které jsou generované kompilátorem.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Chybové zprávy

|Chyba|Zpráva|
|-----------|-------------|
|C3000 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C3001](compiler-error-c3001.md)|'*zpráva*': byl očekáván název direktivy OpenMP|
|[Chyba kompilátoru C3002](compiler-error-c3002.md)|'*name1* *name2*': více názvů direktivy OpenMP|
|[Chyba kompilátoru C3003](compiler-error-c3003.md)|'*– direktiva*': Název direktivy OpenMP není povoleno po direktivy klauzule|
|[Chyba kompilátoru C3004](compiler-error-c3004.md)|'*klauzule*': není platný na OpenMP – klauzule '*– direktiva*' – direktiva|
|[Chyba kompilátoru C3005](compiler-error-c3005.md)|'*zpráva*': Neočekávaný token na OpenMP došlo k '*– direktiva*' – direktiva|
|[Chyba kompilátoru C3006](compiler-error-c3006.md)|'*klauzule*': na OpenMP – klauzule '*– direktiva*' – direktiva chybí očekávaný argument|
|[Chyba kompilátoru C3007](compiler-error-c3007.md)|'*klauzule*': na OpenMP – klauzule '*– direktiva*' – direktiva nevyžaduje argument|
|[Chyba kompilátoru C3008](compiler-error-c3008.md)|*argument*': argument chybí uzavírací ')' na OpenMP '*– direktiva*' – direktiva|
|[Chyba kompilátoru C3009](compiler-error-c3009.md)|'*popisek*': Přejít do OpenMP strukturovaných blok není povoleno|
|[Chyba kompilátoru C3010](compiler-error-c3010.md)|'*popisek*': přejít z OpenMP strukturovaných bloku není povoleno|
|[Chyba kompilátoru C3011](compiler-error-c3011.md)|není povoleno přímo v rámci oblasti paralelní vnořené sestavení|
|[Chyba kompilátoru C3012](compiler-error-c3012.md)|'*funkce*': není povoleno přímo v rámci paralelní oblasti – vnitřní funkce|
|[Chyba kompilátoru C3013](compiler-error-c3013.md)|'*klauzule*': klauzule může být uvedena pouze jednou na OpenMP '*– direktiva*' – direktiva|
|[Chyba kompilátoru C3014](compiler-error-c3014.md)|očekávání pro smyčky následující OpenMP '*– direktiva*' – direktiva|
|[Chyba kompilátoru C3015](compiler-error-c3015.md)|Inicializace v OpenMP pro příkaz má nesprávné formuláře|
|[Chyba kompilátoru C3016](compiler-error-c3016.md)|'*identifikátor*': index proměnné v OpenMP pro příkaz musí mít podepsaný integrální typu|
|[Chyba kompilátoru C3017](compiler-error-c3017.md)|test ukončení v OpenMP pro příkaz má nesprávné formuláře|
|[Chyba kompilátoru C3018](compiler-error-c3018.md)|'*identifikátor*': OpenMP "pro" testovací nebo přírůstek musí používat proměnné index '*proměnná*.|
|[Chyba kompilátoru C3019](compiler-error-c3019.md)|přírůstek v OpenMP pro příkaz má nesprávné formuláře|
|[Chyba kompilátoru C3020](compiler-error-c3020.md)|'*proměnná*': index proměnná OpenMP smyčka for nemůže být upraven do těla smyčky|
|[Chyba kompilátoru C3021](compiler-error-c3021.md)|'*argument*': argument je prázdný na OpenMP '*– direktiva*' – direktiva|
|[Chyba kompilátoru C3022](compiler-error-c3022.md)|'*– direktiva*': Neplatný plán druh z '*– direktiva*'na OpenMP'*– direktiva*' – direktiva|
|[Chyba kompilátoru C3023](compiler-error-c3023.md)|'*argument*': Neočekávaný token v argumentu OpenMP '*– direktiva*' – klauzule|
|[Chyba kompilátoru C3024](compiler-error-c3024.md)|'schedule(runtime)': chunk_size výraz není povolen.|
|[Chyba kompilátoru C3025](compiler-error-c3025.md)|'*klauzule*': byl očekáván výraz integrální|
|[Chyba kompilátoru C3026](compiler-error-c3026.md)|'*klauzule*': konstantní výraz musí být kladná|
|[Chyba kompilátoru C3027](compiler-error-c3027.md)|'*klauzule*': byl očekáván výraz aritmetické nebo ukazatele|
|[Chyba kompilátoru C3028](compiler-error-c3028.md)|'*člen*': pouze členové proměnnou nebo statických dat lze použít v klauzuli sdílení dat|
|[Chyba kompilátoru C3029](compiler-error-c3029.md)|'*symbol*': může být pouze jednou v sdílení dat klauzule v OpenMP – direktiva|
|[Chyba kompilátoru C3030](compiler-error-c3030.md)|'*identifikátor*': proměnné v '*– direktiva*' klauzule/direktiva nemůže mít typ odkazu|
|[Chyba kompilátoru C3031](compiler-error-c3031.md)|'*identifikátor*': proměnné v klauzuli 'snížení' musí být skalární aritmetické typu|
|[Chyba kompilátoru C3032](compiler-error-c3032.md)|'*identifikátor*': proměnné v '*klauzule*'klauzule nemůže být neúplné typu'*typu*.|
|[Chyba kompilátoru C3033](compiler-error-c3033.md)|'*identifikátor*': proměnné v '*klauzule*' klauzule nemůže mít typ kvalifikovaný const|
|[Chyba kompilátoru C3034](compiler-error-c3034.md)|OpenMP '*– direktiva*'– direktiva nelze vnořit přímo v rámci'*– direktiva*' – direktiva|
|[Chyba kompilátoru C3035](compiler-error-c3035.md)|OpenMP 'seřazené' – direktiva musí vázat přímo na a 'pro' nebo 'paralelní pro' direktivy s klauzulí 'objednáno'|
|[Chyba kompilátoru C3036](compiler-error-c3036.md)|'*klauzule*': neplatný operátor token v klauzuli OpenMP snížení|
|[Chyba kompilátoru C3037](compiler-error-c3037.md)|'*identifikátor*': proměnné v '*klauzule*' musí být sdílená klauzule v uzavření do kontextu|
|[Chyba kompilátoru C3038](compiler-error-c3038.md)|'*identifikátor*': Proměnná 'privátní' klauzulí nemůže být redukční proměnnou v uzavření do kontextu|
|[Chyba kompilátoru C3039](compiler-error-c3039.md)|'*identifikátor*': index proměnné v OpenMP pro příkaz nemůže být redukční proměnnou|
|[Chyba kompilátoru C3040](compiler-error-c3040.md)|'*identifikátor*': typ proměnné v klauzuli 'snížení' není kompatibilní s snížení operátor '*operátor*.|
|[Chyba kompilátoru C3041](compiler-error-c3041.md)|'*identifikátor*': proměnné v klauzuli 'copyprivate' musí být privátní v uzavření do kontextu|
|[Chyba kompilátoru C3042](compiler-error-c3042.md)|klauzule 'copyprivate' a 'nowait' nelze v OpenMP objeví spolu se *– direktiva*' – direktiva|
|[Chyba kompilátoru C3043](compiler-error-c3043.md)|OpenMP – direktiva 'kritické' nelze vnořit v direktivě, kritické"se stejným názvem|
|[Chyba kompilátoru C3044](compiler-error-c3044.md)|'sekce': povoleny pouze přímo vnořené v části "části" OpenMP – direktiva|
|[Chyba kompilátoru C3045](compiler-error-c3045.md)|Očekávaný složený příkaz následující direktiva OpenMP oddíly. Chybí ' {'|
|[Chyba kompilátoru C3046](compiler-error-c3046.md)|Chybí strukturovaných blok v oblast OpenMP '#pragma omp – oddíly.|
|[Chyba kompilátoru C3047](compiler-error-c3047.md)|Strukturované blok v OpenMP oblast 'částech' musí předcházet '#pragma omp – část.|
|[Chyba kompilátoru C3048](compiler-error-c3048.md)|Výraz, který následuje, #pragma omp – atomic' má nesprávné formuláře|
|[Chyba kompilátoru C3049](compiler-error-c3049.md)|'*argument*': Neplatný argument v "default" OpenMP – klauzule|
|[Chyba kompilátoru C3050](compiler-error-c3050.md)|'*– třída*': třídu ref nemůže Zdědit z '*identifikátor*.|
|C3051 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C3052](compiler-error-c3052.md)|'*identifikátor*': proměnné se nezobrazí v klauzuli sdílení dat v klauzuli default(none)|
|[Chyba kompilátoru C3053](compiler-error-c3053.md)|'*identifikátor*': "threadprivate" je platná pouze pro globální nebo statické datových položek|
|[Chyba kompilátoru C3054](compiler-error-c3054.md)|'#pragma omp – paralelní' není aktuálně podporováno v obecné třídy nebo funkce|
|[Chyba kompilátoru C3055](compiler-error-c3055.md)|'*identifikátor*': symbol nelze odkazovat, než bude použit v direktivě 'threadprivate.|
|[Chyba kompilátoru C3056](compiler-error-c3056.md)|'*identifikátor*': symbol není ve stejném oboru s 'threadprivate' – direktiva|
|[Chyba kompilátoru C3057](compiler-error-c3057.md)|'*identifikátor*': dynamické inicializace symbolů 'threadprivate' není aktuálně podporováno.|
|[Chyba kompilátoru C3058](compiler-error-c3058.md)|'*identifikátor*': symbol není deklarován jako 'threadprivate, než bude použit v klauzuli 'copyin.|
|[Chyba kompilátoru C3059](compiler-error-c3059.md)|'*identifikátor*': 'threadprivate' symbol nelze použít v '*klauzule*' klauzule|
|[Chyba kompilátoru C3060](compiler-error-c3060.md)|'*identifikátor*': funkce friend nesmí být definován třídy pomocí úplný název (ho lze deklarovat pouze)|
|C3061 chyby kompilátoru|operátor '*operátor*': není povoleno pro výčet '*typ*'se základním typem'*typu*.|
|[Chyba kompilátoru C3062](compiler-error-c3062.md)|'*identifikátor*': enumerátor vyžaduje hodnotu, protože je základní typ '*typu*.|
|[Chyba kompilátoru C3063](compiler-error-c3063.md)|operátor '*operátor*': všechny operandy musí mít stejný typ výčtu|
|C3064 chyby kompilátoru|'*identifikátor*': musí být jednoduchý typ. nebo přeložit na jednu|
|[Chyba kompilátoru C3065](compiler-error-c3065.md)|deklarace vlastnosti v oboru bez třídy není povoleno.|
|[Chyba kompilátoru C3066](compiler-error-c3066.md)|existuje více způsobů, že objekt tohoto typu lze volat s těmito argumenty|
|C3067 chyby kompilátoru|inicializačním seznam nelze použít s integrovanou – operátor]|
|[Chyba kompilátoru C3068](compiler-error-c3068.md)|'*identifikátor*":"holé"funkce nesmí obsahovat objekty, které by vyžadovaly unwinding, pokud došlo k výjimce C++|
|[Chyba kompilátoru C3069](compiler-error-c3069.md)|operátor '*operátor*': není povoleno pro typ výčtu|
|[Chyba kompilátoru C3070](compiler-error-c3070.md)|'*identifikátor*': vlastnost nemá metodu "nastavení"|
|[Chyba kompilátoru C3071](compiler-error-c3071.md)|operátor '*operátor*' lze použít pouze na instanci třídy ref nebo typ hodnoty|
|[Chyba kompilátoru C3072](compiler-error-c3072.md)|operátor '*operátor*' nelze použít pro instance operátor unární % převést instanci ref třídy na typ popisovače používají ref – třída|
|[Chyba kompilátoru C3073](compiler-error-c3073.md)|'*identifikátor*': Třída ref nemá definovaný uživatelem kopírovacího konstruktoru|
|C3074 chyby kompilátoru|pole nemůže být inicializovaný s inicializátoru v závorkách|
|[Chyba kompilátoru C3075](compiler-error-c3075.md)|'*identifikátor*': nelze vložit instanci typu odkazu '*typ*', v typu hodnoty|
|[Chyba kompilátoru C3076](compiler-error-c3076.md)|'*identifikátor*': nelze vložit instanci typu odkazu '*typ*', v nativním typu|
|[Chyba kompilátoru C3077](compiler-error-c3077.md)|'*identifikátor*': finalizační metody lze pouze členem typu odkazu.|
|C3078 chyby kompilátoru|Velikost pole musí být zadány v nových výrazů|
|C3079 chyby kompilátoru|inicializačním seznam nelze použít jako pravý operand operátoru toto přiřazení|
|[Chyba kompilátoru C3080](compiler-error-c3080.md)|'*finalizační metodu*': finalizační metody nemůže mít – specifikátor třídy úložiště-|
|C3081 chyby kompilátoru|Zastaralé.|
|C3082 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C3083](compiler-error-c3083.md)|'*identifikátor*': symbol nalevo od '::' musí být typu|
|[Chyba kompilátoru C3084](compiler-error-c3084.md)|'*identifikátor*': nemůže být destruktor/finalizační metodu '*– klíčové slovo*.|
|[Chyba kompilátoru C3085](compiler-error-c3085.md)|'*identifikátor*': konstruktor nemůže mít '*– klíčové slovo*.|
|C3086 chyby kompilátoru|Nelze najít 'std::initializer_list': je potřeba #include < initializer_list >|
|[Chyba kompilátoru C3087](compiler-error-c3087.md)|'*identifikátor*': volání z '*deklarace*' již inicializuje tento člen|
|C3088 chyby kompilátoru|'*třída*': konstruktoru atributu musí mít název formální argumenty|
|C3089 chyby kompilátoru|'*identifikátor*': název parametru neodpovídá názvu datový člen|
|C3090 chyby kompilátoru|'*třída*': Třída atribut nemůže být šablonu|
|C3091 chyby kompilátoru|'*třída*': Třída atribut nemůže mít základní třídy|
|C3092 chyby kompilátoru|'*třída*': člen třídy atribut nemůže být trochu pole, 'statické' nebo 'const.|
|C3093 chyby kompilátoru|'*typ*': typu není povoleno pro člen třídy atribut '*člen*.|
|[Chyba kompilátoru C3094](compiler-error-c3094.md)|'*atribut*': anonymní využití není povoleno|
|[Chyba kompilátoru C3095](compiler-error-c3095.md)|'*atribut*': atribut nelze opakovat.|
|[Chyba kompilátoru C3096](compiler-error-c3096.md)|'*atribut*': atribut je povoleno v datové členy pouze atribut třídy|
|[Chyba kompilátoru C3097](compiler-error-c3097.md)|'*atribut*': atribut musí být obor s ' sestavení:' nebo ' modulu:.|
|C3098 chyby kompilátoru|'*identifikátor*': atribut nemá žádné uživatelem definované konstruktory|
|[Chyba kompilátoru C3099](compiler-error-c3099.md)|'*– klíčové slovo*': použijte [System::AttributeUsageAttribute] nebo [Windows::Foundation::Metadata::AttributeUsageAttribute] pro spravované nebo WinRT atributy|
