---
title: "Chyby kompilátoru C2300 až C2399 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2303
- C2304
- C2305
- C2306
- C2314
- C2321
- C2323
- C2328
- C2329
- C2330
- C2331
- C2335
- C2336
- C2339
- C2340
- C2342
- C2343
- C2347
- C2354
- C2358
- C2359
- C2363
- C2366
- C2367
- C2398
- C2399
helpviewer_keywords:
- C2303
- C2304
- C2305
- C2306
- C2314
- C2321
- C2323
- C2328
- C2329
- C2330
- C2331
- C2335
- C2336
- C2339
- C2340
- C2342
- C2343
- C2347
- C2354
- C2358
- C2359
- C2363
- C2366
- C2367
- C2398
- C2399
dev_langs: C++
ms.assetid: 07ca45b5-b2f0-4049-837b-40a7a3caed88
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f8e1dcf350c974f5be96b971d3d70e69b95ebc9e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-errors-c2300-through-c2399"></a>Chyby kompilátoru C2300 až C2399
Články v této části dokumentace obsahují informace o část chyb kompilátoru Visual C++. Můžete přístup k informacím zde nebo v **výstup** oken v sadě Visual Studio, můžete vybrat číslo chyby a potom vyberte klávesy F1.  
  
> [!NOTE]
>  Ne každý [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] chyba je popsána v MSDN. Diagnostické zprávy v mnoha případech poskytuje všechny informace, které jsou k dispozici. Pokud se domníváte, že chybovou zprávu potřebuje další vysvětlení, můžete dejte nám vědět. Můžete použít formulář zpětné vazby na této stránce, nebo přejít na panelu nabídek v sadě Visual Studio a zvolte **pomoci**, **ohlásit chybu**, nebo můžete odeslat zprávu návrhu nebo chyb na [Microsoft Connect](http://connect.microsoft.com/VisualStudio).  
  
 Chyby a upozornění na veřejných fórech MSDN můžete najít další pomoc. [Jazyka Visual C++](http://go.microsoft.com/fwlink/?LinkId=158195) fórum je pro dotazy a v diskusích o [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] syntaxi a kompilátoru jazyka. [Visual C++ Obecné](http://go.microsoft.com/fwlink/?LinkId=158194) fórum je pro dotazy o [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] které nejsou popsané v dalších fóra. Můžete také zjistit nápovědu k nástroji chyby a upozornění na [Stack Overflow](http://stackoverflow.com/).  
  
|Chyba|Zpráva|  
|-----------|-------------|  
|[C2300 chyby kompilátoru](compiler-error-c2300.md)|'*– třída*': Třída nemá destruktor volat. ~*– třída*.|  
|[C2301 chyby kompilátoru](compiler-error-c2301.md)|nalevo od ' -> ~*identifikátor*' musí odkazovat na třída, struktura/sjednocení|  
|[C2302 chyby kompilátoru](compiler-error-c2302.md)|nalevo od '. ~*identifikátor*' musí mít typ třída, struktura/sjednocení|  
|C2303 chyby kompilátoru|Strukturované zpracování výjimek nelze použít v coroutine|  
|C2304 chyby kompilátoru|'*– klíčové slovo*, nejde použít uvnitř bloku catch|  
|C2305 chyby kompilátoru|'*souboru*' neobsahuje informace o ladění pro tento modul|  
|C2306 chyby kompilátoru|'*souboru*' neobsahuje nejnovější informace o ladění pro tento modul|  
|[C2307 chyby kompilátoru](compiler-error-c2307.md)|Direktiva pragma *– direktiva* je třeba přesunout mimo funkci, pokud je povoleno přírůstkové kompilace|  
|[C2308 chyby kompilátoru](compiler-error-c2308.md)|zřetězení řetězců neodpovídající|  
|[C2309 chyby kompilátoru](compiler-error-c2309.md)|catch – obslužná rutina očekává deklaraci výjimka v závorkách|  
|[C2310 chyby kompilátoru](compiler-error-c2310.md)|obslužné rutiny catch musíte zadat jeden typ|  
|[C2311 chyby kompilátoru](compiler-error-c2311.md)|'*typ*': je zachytila "..." na řádku *číslo*|  
|[C2312 chyby kompilátoru](compiler-error-c2312.md)|'*type1*': je zachytila se*type2*"na řádku *číslo*|  
|[C2313 chyby kompilátoru](compiler-error-c2313.md)|'*type1*': je zachytila odkaz ('*type2*") na řádku *číslo*|  
|C2314 chyby kompilátoru|– klíčové slovo '*keyword1*' je zastaralý: použijte '*keyword2*' místo toho|  
|[C2315 chyby kompilátoru](compiler-error-c2315.md)|'*type1*': odkaz je zachytila se*type2*"na řádku *číslo*|  
|[C2316 chyby kompilátoru](compiler-error-c2316.md)|'*typ*': nemůže být zachycena destruktor nebo kopírovacího konstruktoru jsou nedostupné nebo odstraněné|  
|[C2317 chyby kompilátoru](compiler-error-c2317.md)|Zkuste blokovat spuštění na řádku '*číslo*' nemá žádný catch obslužné rutiny|  
|[C2318 chyby kompilátoru](compiler-error-c2318.md)|žádné bloku try přidružené k této obslužné rutiny catch|  
|[C2319 chyby kompilátoru](compiler-error-c2319.md)|' try/catch' musí být následováno složený příkaz. Chybí ' {'|  
|[C2320 chyby kompilátoru](compiler-error-c2320.md)|Očekává se:' podle specifikátor přístupu '*specifikátor*.|  
|C2321 chyby kompilátoru|'*identifikátor*' je klíčové slovo a nesmí být v tomto kontextu použít.|  
|[C2322 chyby kompilátoru](compiler-error-c2322.md)|'*identifikátor*': adresa dllimport '*identifikátor*' nejsou statické|  
|C2323 chyby kompilátoru|'*identifikátor*': new – operátor třetí či odstranění funkce nemusí deklarovat statickou nebo v oboru názvů než globální obor názvů|  
|[C2324 chyby kompilátoru](compiler-error-c2324.md)|'*identifikátor*': neočekávané napravo od ':: ~.|  
|[C2325 chyby kompilátoru](compiler-error-c2325.md)|'*type1*': Neočekávaný typ napravo od ' -> ~': Očekává se*type2*.|  
|[C2326 chyby kompilátoru](compiler-error-c2326.md)|'*deklarátor*': funkce nemůže získat přístup k '*identifikátor*.|  
|[C2327 chyby kompilátoru](compiler-error-c2327.md)|'*identifikátor*': není název typu, statické nebo enumerátor|  
|C2328 chyby kompilátoru|'*– klíčové slovo*': klíčové slovo není dosud podporováno.|  
|C2329 chyby kompilátoru|'*identifikátor*': __ptr64 není k dispozici pro ukazatelé na funkce|  
|C2330 chyby kompilátoru|"() implementation_key" je platná pouze v oblasti ohraničené #pragma start_map_region/stop_map_region|  
|C2331 chyby kompilátoru|přístup k '*identifikátor*'nyní definována jako'*accessibility1*', dříve byl definován jako'*accessibility2*.|  
|[C2332 chyby kompilátoru](compiler-error-c2332.md)|'*typedef*': chybí název značky|  
|[C2333 chyby kompilátoru](compiler-error-c2333.md)|'*funkce*': Chyba v deklaraci funkce; přeskočení tělo funkce|  
|[C2334 chyby kompilátoru](compiler-error-c2334.md)|neočekávané tokeny předchozí '*tokenu*'; přeskočení tělo zřejmá funkce|  
|C2335 chyby kompilátoru|'*identifikátor*': typ nelze zavedená v seznamu parametrů funkce|  
|C2336 chyby kompilátoru|'*typ*': Neplatný typ|  
|[C2337 chyby kompilátoru](compiler-error-c2337.md)|'*atribut*': atribut nebyl nalezen|  
|[C2338 chyby kompilátoru](compiler-error-c2338.md)|*(chybová zpráva z externího poskytovatele)*|  
|C2339 chyby kompilátoru|'*identifikátor*': Neplatný typ v vložených IDL|  
|C2340 chyby kompilátoru|'*identifikátor*': 'statické' lze použít pouze v rámci definice třídy|  
|[C2341 chyby kompilátoru](compiler-error-c2341.md)|'*části*': segment musí být definován pomocí #pragma data_seg, code_seg nebo předchozí část použít|  
|C2342 chyby kompilátoru|Chyba syntaxe: konfliktní kvalifikátory typu|  
|C2343 chyby kompilátoru|'*části*': konfliktní atributy oddílu|  
|[C2344 chyby kompilátoru](compiler-error-c2344.md)|Zarovnat (*číslo*): zarovnání musí být násobek dvou|  
|[C2345 chyby kompilátoru](compiler-error-c2345.md)|Zarovnat (*číslo*): zarovnání neplatnou hodnotu|  
|[C2346 chyby kompilátoru](compiler-error-c2346.md)|'*funkce*' nelze kompilovat, jako nativní: '*vysvětlení*.|  
|C2347 chyby kompilátoru|Zastaralé.|  
|[C2348 chyby kompilátoru](compiler-error-c2348.md)|'*typ*': není stylu jazyka C agregace, nemůže být exportován ve vložených IDL|  
|[C2349 chyby kompilátoru](compiler-error-c2349.md)|'*funkce*' nelze kompilovat, jako spravované: '*vysvětlení*'; použít #pragma nespravované|  
|[C2350 chyby kompilátoru](compiler-error-c2350.md)|'*identifikátor*' není statický člen|  
|[C2351 chyby kompilátoru](compiler-error-c2351.md)|zastaralé syntaxe inicializace konstruktoru C++|  
|[C2352 chyby kompilátoru](compiler-error-c2352.md)|'*identifikátor*': Neplatné volání nestatické členské funkce|  
|[C2353 chyby kompilátoru](compiler-error-c2353.md)|specifikace výjimek není povolen.|  
|C2354 chyby kompilátoru|Zastaralé.|  
|[C2355 chyby kompilátoru](compiler-error-c2355.md)|'this': může být odkazováno pouze uvnitř nestatické členské funkce nebo data nestatické členské inicializátory|  
|[C2356 chyby kompilátoru](compiler-error-c2356.md)|Inicializace segment nesmí změnit během jednotky překladu|  
|[C2357 chyby kompilátoru](compiler-error-c2357.md)|'*identifikátor*': musí být funkce typu '*typu*.|  
|C2358 chyby kompilátoru|'*identifikátor*': pomocí statické vlastnosti nemůže být definovaný mimo definice třídy|  
|C2359 chyby kompilátoru|Zastaralé.|  
|[C2360 chyby kompilátoru](compiler-error-c2360.md)|Inicializace se*identifikátor*' bylo přeskočeno 'case' popiskem|  
|[C2361 chyby kompilátoru](compiler-error-c2361.md)|Inicializace se*identifikátor*' bylo přeskočeno popiskem "default"|  
|[C2362 chyby kompilátoru](compiler-error-c2362.md)|Inicializace se*identifikátor*' je vynecháno, goto *popisek*.|  
|C2363 chyby kompilátoru|vnitřní limit číselné – funkce kompilátoru vyžaduje argument literálu řetězce|  
|[C2364 chyby kompilátoru](compiler-error-c2364.md)|'*typ*': Neplatný typ pro vlastní atribut|  
|[C2365 chyby kompilátoru](compiler-error-c2365.md)|'*člen1*': předefinování; předchozí definice byl '*člen2*.|  
|C2366 chyby kompilátoru|'*identifikátor*': předefinování; různých implementation_key specifikátory|  
|C2367 chyby kompilátoru|Zastaralé.|  
|[C2368 chyby kompilátoru](compiler-error-c2368.md)|'*identifikátor*': předefinování; specifikátory různých přidělení|  
|[C2369 chyby kompilátoru](compiler-error-c2369.md)|'*identifikátor*': předefinování; různých dolní indexy|  
|[C2370 chyby kompilátoru](compiler-error-c2370.md)|'*identifikátor*': předefinování; jiného úložiště – třída|  
|[C2371 chyby kompilátoru](compiler-error-c2371.md)|'*identifikátor*': předefinování; různé základní typy|  
|[C2372 chyby kompilátoru](compiler-error-c2372.md)|'*identifikátor*': předefinování; různé typy dereference|  
|[C2373 chyby kompilátoru](compiler-error-c2373.md)|'*identifikátor*': předefinování; modifikátory jiný typ|  
|[C2374 chyby kompilátoru](compiler-error-c2374.md)|'*identifikátor*': předefinování; více inicializace|  
|[C2375 chyby kompilátoru](compiler-error-c2375.md)|'*identifikátor*': předefinování; různých propojení|  
|[C2376 chyby kompilátoru](compiler-error-c2376.md)|'*identifikátor*': předefinování; jiné na základě přidělení|  
|[C2377 chyby kompilátoru](compiler-error-c2377.md)|'*identifikátor*': předefinování; ostatní symbolem nemohou být přetíženy – typedef|  
|[C2378 chyby kompilátoru](compiler-error-c2378.md)|'*identifikátor*': předefinování; symbol nemohou být přetíženy s definice typu|  
|[C2379 chyby kompilátoru](compiler-error-c2379.md)|formální parametr *číslo* je jiného typu povýšení|  
|[C2380 chyby kompilátoru](compiler-error-c2380.md)|typu (typů) předcházející '*identifikátor*' (konstruktor s návratový typ nebo neplatné předefinování aktuální název třídy?)|  
|[C2381 chyby kompilátoru](compiler-error-c2381.md)|'*identifikátor*': předefinování; se liší, __declspec(noreturn)"nebo"[[noreturn]].|  
|[C2382 chyby kompilátoru](compiler-error-c2382.md)|'*identifikátor*': předefinování; specifikace různých výjimek|  
|[C2383 chyby kompilátoru](compiler-error-c2383.md)|'*identifikátor*': výchozí argumenty nejsou povoleny na tento symbol|  
|[C2384 chyby kompilátoru](compiler-error-c2384.md)|'*člen*': nelze použít thread_local nebo __declspec(thread) u člena třídy spravované nebo WinRT|  
|[C2385 chyby kompilátoru](compiler-error-c2385.md)|nejednoznačný přístup '*člen*.|  
|[C2386 chyby kompilátoru](compiler-error-c2386.md)|'*identifikátor*': symbol s tímto názvem již existuje v aktuálním oboru|  
|[C2387 chyby kompilátoru](compiler-error-c2387.md)|'*identifikátor*': nejednoznačný základní třída|  
|[C2388 chyby kompilátoru](compiler-error-c2388.md)|'*identifikátor*': symbol nelze deklarovat s __declspec(appdomain) a __declspec(process)|  
|[C2389 chyby kompilátoru](compiler-error-c2389.md)|'*operátor*': Neplatný operand 'nullptr.|  
|[C2390 chyby kompilátoru](compiler-error-c2390.md)|'*identifikátor*': Třída nesprávné úložiště*specifikátor*.|  
|[C2391 chyby kompilátoru](compiler-error-c2391.md)|'*identifikátor*': při definici typu nelze použít, přítele.|  
|[C2392 chyby kompilátoru](compiler-error-c2392.md)|'*člen1*': typy nejsou podporovány v typech spravované nebo WinRT, jinak vrátí kovariantní '*člen2*' by být potlačena|  
|[C2393 chyby kompilátoru](compiler-error-c2393.md)|'*symbol*': symbol na appdomain nelze přidělit do segmentu '*segment*.|  
|[C2394 chyby kompilátoru](compiler-error-c2394.md)|'*typ*:: operátor *operátor*': CLR nebo WinRT operátor není platný. Minimálně jeden parametr musí být z následujících typů: 'T ^', se ^ %', se ^ &', kde T = '*typu*.|  
|[C2395 chyby kompilátoru](compiler-error-c2395.md)|'*typ*:: operátor *operátor*': CLR nebo WinRT operátor není platný. Minimálně jeden parametr musí být z následujících typů: 'T', se %', se &', se ^', se ^ %', se ^ &', kde T = '*typ*.|  
|[C2396 chyby kompilátoru](compiler-error-c2396.md)|'*type1*:: operátor *type2*': CLR nebo WinRT převod uživatelem definované funkce není platná. Musíte převést nebo převést na: 'T ^', se ^ %', se ^ & ", kde T = '*type1*'|  
|[C2397 chyby kompilátoru](compiler-error-c2397.md)|Převod z '*type1*'do'*type2*se vyžaduje zužující převod|  
|C2398 chyby kompilátoru|Element '*číslo*': převod '*type1*'do'*type2*se vyžaduje zužující převod|  
|C2399 chyby kompilátoru|Zastaralé.|  
