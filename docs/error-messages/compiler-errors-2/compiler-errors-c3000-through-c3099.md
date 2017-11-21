---
title: "C3000 chyby kompilátoru prostřednictvím C3099 | Microsoft Docs"
ms.custom: 
ms.date: 04/21/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
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
dev_langs: C++
ms.assetid: 01b7b9cb-b351-4b5a-8cb0-1fcddb08d2ab
caps.latest.revision: "1"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 59ac61f0ae50f3a6b1d7170ea0b965c3bb8d0fe2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-errors-c3000-through-c3099"></a>C3000 chyby kompilátoru prostřednictvím C3099
Články v této části dokumentace obsahují informace o část chyb kompilátoru Visual C++. Můžete přístup k informacím zde nebo v **výstup** oken v sadě Visual Studio, můžete vybrat číslo chyby a potom vyberte klávesy F1.  
  
> [!NOTE]
>  Ne každý [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] chyba je popsána v MSDN. Diagnostické zprávy v mnoha případech poskytuje všechny informace, které jsou k dispozici. Pokud se domníváte, že chybovou zprávu potřebuje další vysvětlení, můžete dejte nám vědět. Můžete použít formulář zpětné vazby na této stránce, nebo přejít na panelu nabídek v sadě Visual Studio a zvolte **pomoci**, **ohlásit chybu**, nebo můžete odeslat zprávu návrhu nebo chyb na [Microsoft Connect](http://connect.microsoft.com/VisualStudio).  
  
 Chyby a upozornění na veřejných fórech MSDN můžete najít další pomoc. [Jazyka Visual C++](http://go.microsoft.com/fwlink/?LinkId=158195) fórum je pro dotazy a v diskusích o [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] syntaxi a kompilátoru jazyka. [Visual C++ Obecné](http://go.microsoft.com/fwlink/?LinkId=158194) fórum je pro dotazy o [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] které nejsou popsané v dalších fóra. Můžete také zjistit nápovědu k nástroji chyby a upozornění na [Stack Overflow](http://stackoverflow.com/).  
  
|Chyba|Zpráva|  
|-----------|-------------|  
|C3000 chyby kompilátoru|Zastaralé.|  
|[C3001 chyby kompilátoru](compiler-error-c3001.md)|'*zpráva*': byl očekáván název direktivy OpenMP|  
|[C3002 chyby kompilátoru](compiler-error-c3002.md)|'*name1* *name2*': více názvů direktivy OpenMP|  
|[C3003 chyby kompilátoru](compiler-error-c3003.md)|'*– direktiva*': Název direktivy OpenMP není povoleno po direktivy klauzule|  
|[C3004 chyby kompilátoru](compiler-error-c3004.md)|'*klauzule*': není platný na OpenMP – klauzule '*– direktiva*' – direktiva|  
|[C3005 chyby kompilátoru](compiler-error-c3005.md)|'*zpráva*': Neočekávaný token na OpenMP došlo k '*– direktiva*' – direktiva|  
|[C3006 chyby kompilátoru](compiler-error-c3006.md)|'*klauzule*': na OpenMP – klauzule '*– direktiva*' – direktiva chybí očekávaný argument|  
|[C3007 chyby kompilátoru](compiler-error-c3007.md)|'*klauzule*': na OpenMP – klauzule '*– direktiva*' – direktiva nevyžaduje argument|  
|[C3008 chyby kompilátoru](compiler-error-c3008.md)|*argument*': argument chybí uzavírací ')' na OpenMP '*– direktiva*' – direktiva|  
|[C3009 chyby kompilátoru](compiler-error-c3009.md)|'*popisek*': Přejít do OpenMP strukturovaných blok není povoleno|  
|[C3010 chyby kompilátoru](compiler-error-c3010.md)|'*popisek*': přejít z OpenMP strukturovaných bloku není povoleno|  
|[C3011 chyby kompilátoru](compiler-error-c3011.md)|není povoleno přímo v rámci oblasti paralelní vnořené sestavení|  
|[C3012 chyby kompilátoru](compiler-error-c3012.md)|'*funkce*': není povoleno přímo v rámci paralelní oblasti – vnitřní funkce|  
|[C3013 chyby kompilátoru](compiler-error-c3013.md)|'*klauzule*': klauzule může být uvedena pouze jednou na OpenMP '*– direktiva*' – direktiva|  
|[C3014 chyby kompilátoru](compiler-error-c3014.md)|očekávání pro smyčky následující OpenMP '*– direktiva*' – direktiva|  
|[C3015 chyby kompilátoru](compiler-error-c3015.md)|Inicializace v OpenMP pro příkaz má nesprávné formuláře|  
|[C3016 chyby kompilátoru](compiler-error-c3016.md)|'*identifikátor*': index proměnné v OpenMP pro příkaz musí mít podepsaný integrální typu|  
|[C3017 chyby kompilátoru](compiler-error-c3017.md)|test ukončení v OpenMP pro příkaz má nesprávné formuláře|  
|[C3018 chyby kompilátoru](compiler-error-c3018.md)|'*identifikátor*': OpenMP "pro" testovací nebo přírůstek musí používat proměnné index '*proměnná*.|  
|[C3019 chyby kompilátoru](compiler-error-c3019.md)|přírůstek v OpenMP pro příkaz má nesprávné formuláře|  
|[C3020 chyby kompilátoru](compiler-error-c3020.md)|'*proměnná*': index proměnná OpenMP smyčka for nemůže být upraven do těla smyčky|  
|[C3021 chyby kompilátoru](compiler-error-c3021.md)|'*argument*': argument je prázdný na OpenMP '*– direktiva*' – direktiva|  
|[C3022 chyby kompilátoru](compiler-error-c3022.md)|'*– direktiva*': Neplatný plán druh z '*– direktiva*'na OpenMP'*– direktiva*' – direktiva|  
|[C3023 chyby kompilátoru](compiler-error-c3023.md)|'*argument*': Neočekávaný token v argumentu OpenMP '*– direktiva*' – klauzule|  
|[C3024 chyby kompilátoru](compiler-error-c3024.md)|'schedule(runtime)': chunk_size výraz není povolen.|  
|[C3025 chyby kompilátoru](compiler-error-c3025.md)|'*klauzule*': byl očekáván výraz integrální|  
|[C3026 chyby kompilátoru](compiler-error-c3026.md)|'*klauzule*': konstantní výraz musí být kladná|  
|[C3027 chyby kompilátoru](compiler-error-c3027.md)|'*klauzule*': byl očekáván výraz aritmetické nebo ukazatele|  
|[C3028 chyby kompilátoru](compiler-error-c3028.md)|'*člen*': pouze členové proměnnou nebo statických dat lze použít v klauzuli sdílení dat|  
|[C3029 chyby kompilátoru](compiler-error-c3029.md)|'*symbol*': může být pouze jednou v sdílení dat klauzule v OpenMP – direktiva|  
|[C3030 chyby kompilátoru](compiler-error-c3030.md)|'*identifikátor*': proměnné v '*– direktiva*' klauzule/direktiva nemůže mít typ odkazu|  
|[C3031 chyby kompilátoru](compiler-error-c3031.md)|'*identifikátor*': proměnné v klauzuli 'snížení' musí být skalární aritmetické typu|  
|[C3032 chyby kompilátoru](compiler-error-c3032.md)|'*identifikátor*': proměnné v '*klauzule*'klauzule nemůže být neúplné typu'*typu*.|  
|[C3033 chyby kompilátoru](compiler-error-c3033.md)|'*identifikátor*': proměnné v '*klauzule*' klauzule nemůže mít typ kvalifikovaný const|  
|[C3034 chyby kompilátoru](compiler-error-c3034.md)|OpenMP '*– direktiva*'– direktiva nelze vnořit přímo v rámci'*– direktiva*' – direktiva|  
|[C3035 chyby kompilátoru](compiler-error-c3035.md)|OpenMP 'seřazené' – direktiva musí vázat přímo na a 'pro' nebo 'paralelní pro' direktivy s klauzulí 'objednáno'|  
|[C3036 chyby kompilátoru](compiler-error-c3036.md)|'*klauzule*': neplatný operátor token v klauzuli OpenMP snížení|  
|[C3037 chyby kompilátoru](compiler-error-c3037.md)|'*identifikátor*': proměnné v '*klauzule*' musí být sdílená klauzule v uzavření do kontextu|  
|[C3038 chyby kompilátoru](compiler-error-c3038.md)|'*identifikátor*': Proměnná 'privátní' klauzulí nemůže být redukční proměnnou v uzavření do kontextu|  
|[C3039 chyby kompilátoru](compiler-error-c3039.md)|'*identifikátor*': index proměnné v OpenMP pro příkaz nemůže být redukční proměnnou|  
|[C3040 chyby kompilátoru](compiler-error-c3040.md)|'*identifikátor*': typ proměnné v klauzuli 'snížení' není kompatibilní s snížení operátor '*operátor*.|  
|[C3041 chyby kompilátoru](compiler-error-c3041.md)|'*identifikátor*': proměnné v klauzuli 'copyprivate' musí být privátní v uzavření do kontextu|  
|[C3042 chyby kompilátoru](compiler-error-c3042.md)|klauzule 'copyprivate' a 'nowait' nelze v OpenMP objeví spolu se*– direktiva*' – direktiva|  
|[C3043 chyby kompilátoru](compiler-error-c3043.md)|OpenMP – direktiva 'kritické' nelze vnořit v direktivě, kritické"se stejným názvem|  
|[C3044 chyby kompilátoru](compiler-error-c3044.md)|'sekce': povoleny pouze přímo vnořené v části "části" OpenMP – direktiva|  
|[C3045 chyby kompilátoru](compiler-error-c3045.md)|Očekávaný složený příkaz následující direktiva OpenMP oddíly. Chybí ' {'|  
|[C3046 chyby kompilátoru](compiler-error-c3046.md)|Chybí strukturovaných blok v oblast OpenMP '#pragma omp – oddíly.|  
|[C3047 chyby kompilátoru](compiler-error-c3047.md)|Strukturované blok v OpenMP oblast 'částech' musí předcházet '#pragma omp – část.|  
|[C3048 chyby kompilátoru](compiler-error-c3048.md)|Výraz, který následuje, #pragma omp – atomic' má nesprávné formuláře|  
|[C3049 chyby kompilátoru](compiler-error-c3049.md)|'*argument*': Neplatný argument v "default" OpenMP – klauzule|  
|[C3050 chyby kompilátoru](compiler-error-c3050.md)|'*– třída*': třídu ref nemůže Zdědit z '*identifikátor*.|  
|C3051 chyby kompilátoru|Zastaralé.|  
|[C3052 chyby kompilátoru](compiler-error-c3052.md)|'*identifikátor*': proměnné se nezobrazí v klauzuli sdílení dat v klauzuli default(none)|  
|[C3053 chyby kompilátoru](compiler-error-c3053.md)|'*identifikátor*': "threadprivate" je platná pouze pro globální nebo statické datových položek|  
|[C3054 chyby kompilátoru](compiler-error-c3054.md)|'#pragma omp – paralelní' není aktuálně podporováno v obecné třídy nebo funkce|  
|[C3055 chyby kompilátoru](compiler-error-c3055.md)|'*identifikátor*': symbol nelze odkazovat, než bude použit v direktivě 'threadprivate.|  
|[C3056 chyby kompilátoru](compiler-error-c3056.md)|'*identifikátor*': symbol není ve stejném oboru s 'threadprivate' – direktiva|  
|[C3057 chyby kompilátoru](compiler-error-c3057.md)|'*identifikátor*': dynamické inicializace symbolů 'threadprivate' není aktuálně podporováno.|  
|[C3058 chyby kompilátoru](compiler-error-c3058.md)|'*identifikátor*': symbol není deklarován jako 'threadprivate, než bude použit v klauzuli 'copyin.|  
|[C3059 chyby kompilátoru](compiler-error-c3059.md)|'*identifikátor*': 'threadprivate' symbol nelze použít v '*klauzule*' klauzule|  
|[C3060 chyby kompilátoru](compiler-error-c3060.md)|'*identifikátor*': funkce friend nesmí být definován třídy pomocí úplný název (ho lze deklarovat pouze)|  
|C3061 chyby kompilátoru|operátor '*operátor*': není povoleno pro výčet '*typ*'se základním typem'*typu*.|  
|[C3062 chyby kompilátoru](compiler-error-c3062.md)|'*identifikátor*': enumerátor vyžaduje hodnotu, protože je základní typ '*typu*.|  
|[C3063 chyby kompilátoru](compiler-error-c3063.md)|operátor '*operátor*': všechny operandy musí mít stejný typ výčtu|  
|C3064 chyby kompilátoru|'*identifikátor*': musí být jednoduchý typ. nebo přeložit na jednu|  
|[C3065 chyby kompilátoru](compiler-error-c3065.md)|deklarace vlastnosti v oboru bez třídy není povoleno.|  
|[C3066 chyby kompilátoru](compiler-error-c3066.md)|existuje více způsobů, že objekt tohoto typu lze volat s těmito argumenty|  
|C3067 chyby kompilátoru|inicializačním seznam nelze použít s integrovanou – operátor]|  
|[C3068 chyby kompilátoru](compiler-error-c3068.md)|'*identifikátor*":"holé"funkce nesmí obsahovat objekty, které by vyžadovaly unwinding, pokud došlo k výjimce C++|  
|[C3069 chyby kompilátoru](compiler-error-c3069.md)|operátor '*operátor*': není povoleno pro typ výčtu|  
|[C3070 chyby kompilátoru](compiler-error-c3070.md)|'*identifikátor*': vlastnost nemá metodu "nastavení"|  
|[C3071 chyby kompilátoru](compiler-error-c3071.md)|operátor '*operátor*' lze použít pouze na instanci třídy ref nebo typ hodnoty|  
|[C3072 chyby kompilátoru](compiler-error-c3072.md)|operátor '*operátor*' nelze použít pro instance operátor unární % převést instanci ref třídy na typ popisovače používají ref – třída|  
|[C3073 chyby kompilátoru](compiler-error-c3073.md)|'*identifikátor*': Třída ref nemá definovaný uživatelem kopírovacího konstruktoru|  
|C3074 chyby kompilátoru|pole nemůže být inicializovaný s inicializátoru v závorkách|  
|[C3075 chyby kompilátoru](compiler-error-c3075.md)|'*identifikátor*': nelze vložit instanci typu odkazu '*typ*', v typu hodnoty|  
|[C3076 chyby kompilátoru](compiler-error-c3076.md)|'*identifikátor*': nelze vložit instanci typu odkazu '*typ*', v nativním typu|  
|[C3077 chyby kompilátoru](compiler-error-c3077.md)|'*identifikátor*': finalizační metody lze pouze členem typu odkazu.|  
|C3078 chyby kompilátoru|Velikost pole musí být zadány v nových výrazů|  
|C3079 chyby kompilátoru|inicializačním seznam nelze použít jako pravý operand operátoru toto přiřazení|  
|[C3080 chyby kompilátoru](compiler-error-c3080.md)|'*finalizační metodu*': finalizační metody nemůže mít – specifikátor třídy úložiště-|  
|C3081 chyby kompilátoru|Zastaralé.|  
|C3082 chyby kompilátoru|Zastaralé.|  
|[C3083 chyby kompilátoru](compiler-error-c3083.md)|'*identifikátor*': symbol nalevo od '::' musí být typu|  
|[C3084 chyby kompilátoru](compiler-error-c3084.md)|'*identifikátor*': nemůže být destruktor/finalizační metodu '*– klíčové slovo*.|  
|[C3085 chyby kompilátoru](compiler-error-c3085.md)|'*identifikátor*': konstruktor nemůže mít '*– klíčové slovo*.|  
|C3086 chyby kompilátoru|Nelze najít 'std::initializer_list': je potřeba #include < initializer_list >|  
|[C3087 chyby kompilátoru](compiler-error-c3087.md)|'*identifikátor*': volání z '*deklarace*' již inicializuje tento člen|  
|C3088 chyby kompilátoru|'*třída*': konstruktoru atributu musí mít název formální argumenty|  
|C3089 chyby kompilátoru|'*identifikátor*': název parametru neodpovídá názvu datový člen|  
|C3090 chyby kompilátoru|'*třída*': Třída atribut nemůže být šablonu|  
|C3091 chyby kompilátoru|'*třída*': Třída atribut nemůže mít základní třídy|  
|C3092 chyby kompilátoru|'*třída*': člen třídy atribut nemůže být trochu pole, 'statické' nebo 'const.|  
|C3093 chyby kompilátoru|'*typ*': typu není povoleno pro člen třídy atribut '*člen*.|  
|[C3094 chyby kompilátoru](compiler-error-c3094.md)|'*atribut*': anonymní využití není povoleno|  
|[C3095 chyby kompilátoru](compiler-error-c3095.md)|'*atribut*': atribut nelze opakovat.|  
|[C3096 chyby kompilátoru](compiler-error-c3096.md)|'*atribut*': atribut je povoleno v datové členy pouze atribut třídy|  
|[C3097 chyby kompilátoru](compiler-error-c3097.md)|'*atribut*': atribut musí být obor s ' sestavení:' nebo ' modulu:.|  
|C3098 chyby kompilátoru|'*identifikátor*': atribut nemá žádné uživatelem definované konstruktory|  
|[C3099 chyby kompilátoru](compiler-error-c3099.md)|'*– klíčové slovo*': použijte [System::AttributeUsageAttribute] nebo [Windows::Foundation::Metadata::AttributeUsageAttribute] pro spravované nebo WinRT atributy|  
