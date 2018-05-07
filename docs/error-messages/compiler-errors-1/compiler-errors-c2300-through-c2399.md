---
title: Chyby kompilátoru C2300 až C2399 | Microsoft Docs
ms.custom: ''
ms.date: 11/17/2017
ms.technology:
- cpp-diagnostics
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
dev_langs:
- C++
ms.assetid: 07ca45b5-b2f0-4049-837b-40a7a3caed88
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d8b758ce26897d5c2ad8baa176c8a83b2c9954df
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-errors-c2300-through-c2399"></a>Chyby kompilátoru C2300 až C2399

Články v této části dokumentace vysvětlují podmnožinu chybové zprávy, které jsou generované kompilátorem.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Chybové zprávy

|Chyba|Zpráva|
|-----------|-------------|
|[Chyba kompilátoru C2300](compiler-error-c2300.md)|'*– třída*': Třída nemá destruktor volat. ~*– třída*.|
|[Chyba kompilátoru C2301](compiler-error-c2301.md)|nalevo od ' -> ~*identifikátor*' musí odkazovat na třída, struktura/sjednocení|
|[Chyba kompilátoru C2302](compiler-error-c2302.md)|nalevo od '. ~*identifikátor*' musí mít typ třída, struktura/sjednocení|
|C2303 chyby kompilátoru|Strukturované zpracování výjimek nelze použít v coroutine|
|C2304 chyby kompilátoru|'*– klíčové slovo*, nejde použít uvnitř bloku catch|
|C2305 chyby kompilátoru|'*souboru*' neobsahuje informace o ladění pro tento modul|
|C2306 chyby kompilátoru|'*souboru*' neobsahuje nejnovější informace o ladění pro tento modul|
|[Chyba kompilátoru C2307](compiler-error-c2307.md)|Direktiva pragma *– direktiva* je třeba přesunout mimo funkci, pokud je povoleno přírůstkové kompilace|
|[Chyba kompilátoru C2308](compiler-error-c2308.md)|zřetězení řetězců neodpovídající|
|[Chyba kompilátoru C2309](compiler-error-c2309.md)|catch – obslužná rutina očekává deklaraci výjimka v závorkách|
|[Chyba kompilátoru C2310](compiler-error-c2310.md)|obslužné rutiny catch musíte zadat jeden typ|
|[Chyba kompilátoru C2311](compiler-error-c2311.md)|'*typ*': je zachytila "..." na řádku *číslo*|
|[Chyba kompilátoru C2312](compiler-error-c2312.md)|'*type1*': je zachytila se*type2*"na řádku *číslo*|
|[Chyba kompilátoru C2313](compiler-error-c2313.md)|'*type1*': je zachytila odkaz ('*type2*") na řádku *číslo*|
|C2314 chyby kompilátoru|– klíčové slovo '*keyword1*' je zastaralý: použijte '*keyword2*' místo toho|
|[Chyba kompilátoru C2315](compiler-error-c2315.md)|'*type1*': odkaz je zachytila se*type2*"na řádku *číslo*|
|[Chyba kompilátoru C2316](compiler-error-c2316.md)|'*typ*': nemůže být zachycena destruktor nebo kopírovacího konstruktoru jsou nedostupné nebo odstraněné|
|[Chyba kompilátoru C2317](compiler-error-c2317.md)|Zkuste blokovat spuštění na řádku '*číslo*' nemá žádný catch obslužné rutiny|
|[Chyba kompilátoru C2318](compiler-error-c2318.md)|žádné bloku try přidružené k této obslužné rutiny catch|
|[Chyba kompilátoru C2319](compiler-error-c2319.md)|' try/catch' musí být následováno složený příkaz. Chybí ' {'|
|[Chyba kompilátoru C2320](compiler-error-c2320.md)|Očekává se:' podle specifikátor přístupu '*specifikátor*.|
|C2321 chyby kompilátoru|'*identifikátor*' je klíčové slovo a nesmí být v tomto kontextu použít.|
|[Chyba kompilátoru C2322](compiler-error-c2322.md)|'*identifikátor*': adresa dllimport '*identifikátor*' nejsou statické|
|C2323 chyby kompilátoru|'*identifikátor*': new – operátor třetí či odstranění funkce nemusí deklarovat statickou nebo v oboru názvů než globální obor názvů|
|[Chyba kompilátoru C2324](compiler-error-c2324.md)|'*identifikátor*': neočekávané napravo od ':: ~.|
|[Chyba kompilátoru C2325](compiler-error-c2325.md)|'*type1*': Neočekávaný typ napravo od ' -> ~': Očekává se*type2*.|
|[Chyba kompilátoru C2326](compiler-error-c2326.md)|'*deklarátor*': funkce nemůže získat přístup k '*identifikátor*.|
|[Chyba kompilátoru C2327](compiler-error-c2327.md)|'*identifikátor*': není název typu, statické nebo enumerátor|
|C2328 chyby kompilátoru|'*– klíčové slovo*': klíčové slovo není dosud podporováno.|
|C2329 chyby kompilátoru|'*identifikátor*': __ptr64 není k dispozici pro ukazatelé na funkce|
|C2330 chyby kompilátoru|"() implementation_key" je platná pouze v oblasti ohraničené #pragma start_map_region/stop_map_region|
|C2331 chyby kompilátoru|přístup k '*identifikátor*'nyní definována jako'*accessibility1*', dříve byl definován jako'*accessibility2*.|
|[Chyba kompilátoru C2332](compiler-error-c2332.md)|'*typedef*': chybí název značky|
|[Chyba kompilátoru C2333](compiler-error-c2333.md)|'*funkce*': Chyba v deklaraci funkce; přeskočení tělo funkce|
|[Chyba kompilátoru C2334](compiler-error-c2334.md)|neočekávané tokeny předchozí '*tokenu*'; přeskočení tělo zřejmá funkce|
|C2335 chyby kompilátoru|'*identifikátor*': typ nelze zavedená v seznamu parametrů funkce|
|C2336 chyby kompilátoru|'*typ*': Neplatný typ|
|[Chyba kompilátoru C2337](compiler-error-c2337.md)|'*atribut*': atribut nebyl nalezen|
|[Chyba kompilátoru C2338](compiler-error-c2338.md)|*(chybová zpráva z externího poskytovatele)*|
|C2339 chyby kompilátoru|'*identifikátor*': Neplatný typ v vložených IDL|
|C2340 chyby kompilátoru|'*identifikátor*': 'statické' lze použít pouze v rámci definice třídy|
|[Chyba kompilátoru C2341](compiler-error-c2341.md)|'*části*': segment musí být definován pomocí #pragma data_seg, code_seg nebo předchozí část použít|
|C2342 chyby kompilátoru|Chyba syntaxe: konfliktní kvalifikátory typu|
|C2343 chyby kompilátoru|'*části*': konfliktní atributy oddílu|
|[Chyba kompilátoru C2344](compiler-error-c2344.md)|Zarovnat (*číslo*): zarovnání musí být násobek dvou|
|[Chyba kompilátoru C2345](compiler-error-c2345.md)|Zarovnat (*číslo*): zarovnání neplatnou hodnotu|
|[Chyba kompilátoru C2346](compiler-error-c2346.md)|'*funkce*' nelze kompilovat, jako nativní: '*vysvětlení*.|
|C2347 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C2348](compiler-error-c2348.md)|'*typ*': není stylu jazyka C agregace, nemůže být exportován ve vložených IDL|
|[Chyba kompilátoru C2349](compiler-error-c2349.md)|'*funkce*' nelze kompilovat, jako spravované: '*vysvětlení*'; použít #pragma nespravované|
|[Chyba kompilátoru C2350](compiler-error-c2350.md)|'*identifikátor*' není statický člen|
|[Chyba kompilátoru C2351](compiler-error-c2351.md)|zastaralé syntaxe inicializace konstruktoru C++|
|[Chyba kompilátoru C2352](compiler-error-c2352.md)|'*identifikátor*': Neplatné volání nestatické členské funkce|
|[Chyba kompilátoru C2353](compiler-error-c2353.md)|specifikace výjimek není povolen.|
|C2354 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C2355](compiler-error-c2355.md)|'this': může být odkazováno pouze uvnitř nestatické členské funkce nebo data nestatické členské inicializátory|
|[Chyba kompilátoru C2356](compiler-error-c2356.md)|Inicializace segment nesmí změnit během jednotky překladu|
|[Chyba kompilátoru C2357](compiler-error-c2357.md)|'*identifikátor*': musí být funkce typu '*typu*.|
|C2358 chyby kompilátoru|'*identifikátor*': pomocí statické vlastnosti nemůže být definovaný mimo definice třídy|
|C2359 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C2360](compiler-error-c2360.md)|Inicializace se*identifikátor*' bylo přeskočeno 'case' popiskem|
|[Chyba kompilátoru C2361](compiler-error-c2361.md)|Inicializace se*identifikátor*' bylo přeskočeno popiskem "default"|
|[Chyba kompilátoru C2362](compiler-error-c2362.md)|Inicializace se*identifikátor*' je vynecháno, goto *popisek*.|
|C2363 chyby kompilátoru|vnitřní limit číselné – funkce kompilátoru vyžaduje argument literálu řetězce|
|[Chyba kompilátoru C2364](compiler-error-c2364.md)|'*typ*': Neplatný typ pro vlastní atribut|
|[Chyba kompilátoru C2365](compiler-error-c2365.md)|'*člen1*': předefinování; předchozí definice byl '*člen2*.|
|C2366 chyby kompilátoru|'*identifikátor*': předefinování; různých implementation_key specifikátory|
|C2367 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C2368](compiler-error-c2368.md)|'*identifikátor*': předefinování; specifikátory různých přidělení|
|[Chyba kompilátoru C2369](compiler-error-c2369.md)|'*identifikátor*': předefinování; různých dolní indexy|
|[Chyba kompilátoru C2370](compiler-error-c2370.md)|'*identifikátor*': předefinování; jiného úložiště – třída|
|[Chyba kompilátoru C2371](compiler-error-c2371.md)|'*identifikátor*': předefinování; různé základní typy|
|[Chyba kompilátoru C2372](compiler-error-c2372.md)|'*identifikátor*': předefinování; různé typy dereference|
|[Chyba kompilátoru C2373](compiler-error-c2373.md)|'*identifikátor*': předefinování; modifikátory jiný typ|
|[Chyba kompilátoru C2374](compiler-error-c2374.md)|'*identifikátor*': předefinování; více inicializace|
|[Chyba kompilátoru C2375](compiler-error-c2375.md)|'*identifikátor*': předefinování; různých propojení|
|[Chyba kompilátoru C2376](compiler-error-c2376.md)|'*identifikátor*': předefinování; jiné na základě přidělení|
|[Chyba kompilátoru C2377](compiler-error-c2377.md)|'*identifikátor*': předefinování; ostatní symbolem nemohou být přetíženy – typedef|
|[Chyba kompilátoru C2378](compiler-error-c2378.md)|'*identifikátor*': předefinování; symbol nemohou být přetíženy s definice typu|
|[Chyba kompilátoru C2379](compiler-error-c2379.md)|formální parametr *číslo* je jiného typu povýšení|
|[Chyba kompilátoru C2380](compiler-error-c2380.md)|typu (typů) předcházející '*identifikátor*' (konstruktor s návratový typ nebo neplatné předefinování aktuální název třídy?)|
|[Chyba kompilátoru C2381](compiler-error-c2381.md)|'*identifikátor*': předefinování; se liší, __declspec(noreturn)"nebo"[[noreturn]].|
|[Chyba kompilátoru C2382](compiler-error-c2382.md)|'*identifikátor*': předefinování; specifikace různých výjimek|
|[Chyba kompilátoru C2383](compiler-error-c2383.md)|'*identifikátor*': výchozí argumenty nejsou povoleny na tento symbol|
|[Chyba kompilátoru C2384](compiler-error-c2384.md)|'*člen*': nelze použít thread_local nebo __declspec(thread) u člena třídy spravované nebo WinRT|
|[Chyba kompilátoru C2385](compiler-error-c2385.md)|nejednoznačný přístup '*člen*.|
|[Chyba kompilátoru C2386](compiler-error-c2386.md)|'*identifikátor*': symbol s tímto názvem již existuje v aktuálním oboru|
|[Chyba kompilátoru C2387](compiler-error-c2387.md)|'*identifikátor*': nejednoznačný základní třída|
|[Chyba kompilátoru C2388](compiler-error-c2388.md)|'*identifikátor*': symbol nelze deklarovat s __declspec(appdomain) a __declspec(process)|
|[Chyba kompilátoru C2389](compiler-error-c2389.md)|'*operátor*': Neplatný operand 'nullptr.|
|[Chyba kompilátoru C2390](compiler-error-c2390.md)|'*identifikátor*': Třída nesprávné úložiště*specifikátor*.|
|[Chyba kompilátoru C2391](compiler-error-c2391.md)|'*identifikátor*': při definici typu nelze použít, přítele.|
|[Chyba kompilátoru C2392](compiler-error-c2392.md)|'*člen1*': typy nejsou podporovány v typech spravované nebo WinRT, jinak vrátí kovariantní '*člen2*' by být potlačena|
|[Chyba kompilátoru C2393](compiler-error-c2393.md)|'*symbol*': symbol na appdomain nelze přidělit do segmentu '*segment*.|
|[Chyba kompilátoru C2394](compiler-error-c2394.md)|'*typ*:: operátor *operátor*': CLR nebo WinRT operátor není platný. Minimálně jeden parametr musí být z následujících typů: 'T ^', se ^ %', se ^ &', kde T = '*typu*.|
|[Chyba kompilátoru C2395](compiler-error-c2395.md)|'*typ*:: operátor *operátor*': CLR nebo WinRT operátor není platný. Minimálně jeden parametr musí být z následujících typů: 'T', se %', se &', se ^', se ^ %', se ^ &', kde T = '*typ*.|
|[Chyba kompilátoru C2396](compiler-error-c2396.md)|'*type1*:: operátor *type2*': CLR nebo WinRT převod uživatelem definované funkce není platná. Musíte převést nebo převést na: 'T ^', se ^ %', se ^ & ", kde T = '*type1*'|
|[Chyba kompilátoru C2397](compiler-error-c2397.md)|Převod z '*type1*'do'*type2*se vyžaduje zužující převod|
|C2398 chyby kompilátoru|Element '*číslo*': převod '*type1*'do'*type2*se vyžaduje zužující převod|
|C2399 chyby kompilátoru|Zastaralé.|
