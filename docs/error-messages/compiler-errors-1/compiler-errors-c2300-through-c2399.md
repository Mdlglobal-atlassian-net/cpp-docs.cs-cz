---
title: Chyby kompilátoru C2300 až C2399
ms.date: 04/21/2019
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
ms.assetid: 07ca45b5-b2f0-4049-837b-40a7a3caed88
ms.openlocfilehash: 28ab73857b46fed29e2ba8d7bc051ffb81b54bb3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62360447"
---
# <a name="compiler-errors-c2300-through-c2399"></a>Chyby kompilátoru C2300 až C2399

Články v této části dokumentace vysvětlují podmnožinu chybové zprávy, které jsou generovány kompilátorem.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Chybové zprávy

|Chyba|Zpráva|
|-----------|-------------|
|[Chyba kompilátoru C2300](compiler-error-c2300.md)|"*třídy*': Třída nemá destruktor volá ' ~*třídy*.|
|[Chyba kompilátoru C2301](compiler-error-c2301.md)|Levá strana "-> ~*identifikátor*" musí odkazovat na třídu/strukturu/sjednocení|
|[Chyba kompilátoru C2302](compiler-error-c2302.md)|Levá strana ". ~*identifikátor*' musí být typu Třída/struktura/sjednocení|
|Chyba kompilátoru C2303|Strukturované zpracování výjimek nejde používat v korutině.|
|Chyba kompilátoru C2304|"*– klíčové slovo*' nelze použít uvnitř bloku catch.|
|Chyba kompilátoru C2305|"*souboru*' neobsahuje ladicí informace pro tento modul.|
|Chyba kompilátoru C2306|"*souboru*' neobsahuje nejaktuálnější ladicí informace pro tento modul.|
|[Chyba kompilátoru C2307](compiler-error-c2307.md)|direktivy pragma *směrnice* musí přesunout mimo funkci, pokud je povolená přírůstková kompilace|
|[Chyba kompilátoru C2308](compiler-error-c2308.md)|řetězení neodpovídajících řetězců|
|[Chyba kompilátoru C2309](compiler-error-c2309.md)|obslužné rutiny catch očekává deklaraci výjimky v závorkách|
|[Chyba kompilátoru C2310](compiler-error-c2310.md)|obslužné rutiny catch musí specifikovat jeden typ.|
|[Chyba kompilátoru C2311](compiler-error-c2311.md)|"*typ*': zachycuje se prostřednictvím '...' na řádku *číslo*|
|[Chyba kompilátoru C2312](compiler-error-c2312.md)|"*type1*': se zachycuje prostřednictvím"*type2*' na řádku *číslo*|
|[Chyba kompilátoru C2313](compiler-error-c2313.md)|"*type1*': se zachycuje prostřednictvím odkazu ("*type2*") na řádku *číslo*|
|Chyba kompilátoru C2314|– klíčové slovo '*keyword1*' se již nepoužívá: použijte "*keyword2*" místo toho|
|[Chyba kompilátoru C2315](compiler-error-c2315.md)|"*type1*': odkaz se zachycuje prostřednictvím"*type2*' na řádku *číslo*|
|[Chyba kompilátoru C2316](compiler-error-c2316.md)|"*typ*': nejde zachytit, protože destruktor nebo kopírovací konstuktor jsou nedostupné nebo odstraněné|
|[Chyba kompilátoru C2317](compiler-error-c2317.md)|Zkuste bloku začínající na řádku "*číslo*' nemá žádné obslužné rutiny catch|
|[Chyba kompilátoru C2318](compiler-error-c2318.md)|žádný přidružený k této obslužné rutiny catch blok try.|
|[Chyba kompilátoru C2319](compiler-error-c2319.md)|bloku try/catch musí následovat složený příkaz. Chybí "{"|
|[Chyba kompilátoru C2320](compiler-error-c2320.md)|byl očekáván ':' použít specifikátor přístupu "*specifikátor*"|
|Chyba kompilátoru C2321|"*identifikátor*' je klíčové slovo a v tomto kontextu nelze použít|
|[Chyba kompilátoru C2322](compiler-error-c2322.md)|"*identifikátor*': adresa dllimport"*identifikátor*"není statická.|
|Chyba kompilátoru C2323|"*identifikátor*': bez operátoru new nebo delete funkce nemůže být deklarovaný jako static nebo v oboru názvů, než globální obor názvů|
|[Chyba kompilátoru C2324](compiler-error-c2324.md)|"*identifikátor*': neočekávalo se napravo z ':: ~"|
|[Chyba kompilátoru C2325](compiler-error-c2325.md)|"*type1*': Neočekávaný typ napravo od ' -> ~": byl očekáván '*type2*"|
|[Chyba kompilátoru C2326](compiler-error-c2326.md)|"*deklarátor*': Nelze získat přístup k funkci"*identifikátor*"|
|[Chyba kompilátoru C2327](compiler-error-c2327.md)|"*identifikátor*': není název typu, statický člen ani enumerátor|
|Chyba kompilátoru C2328|"*– klíčové slovo*': klíčové slovo se ještě nepodporuje.|
|Chyba kompilátoru C2329|"*identifikátor*': možnost __ptr64 není dostupná pro ukazatele na funkce|
|Chyba kompilátoru C2330|zadání implementation_key () je platná pouze v oblasti ohraničené #pragma start_map_region/stop_map_region.|
|Chyba kompilátoru C2331|přístup k '*identifikátor*"teď definovaný jako"*accessibility1*", dřív byl definovaný jako"*accessibility2*.|
|[Chyba kompilátoru C2332](compiler-error-c2332.md)|"*typedef*': chybí název značky|
|[Chyba kompilátoru C2333](compiler-error-c2333.md)|"*funkce*": Chyba v deklaraci funkce; tělo funkce se přeskočí|
|[Chyba kompilátoru C2334](compiler-error-c2334.md)|neočekávané tokeny předchozí "*token*"; tělo funkce pozná se přeskočí|
|Chyba kompilátoru C2335|"*identifikátor*': typ nemůže být zavedený seznamem parametrů funkcí|
|Chyba kompilátoru C2336|"*typ*': Neplatný typ|
|[Chyba kompilátoru C2337](compiler-error-c2337.md)|"*atribut*': atribut nebyl nalezen|
|[Chyba kompilátoru C2338](compiler-error-c2338.md)|*(chybová zpráva z externího poskytovatele)*|
|Chyba kompilátoru C2339|"*identifikátor*': Neplatný typ ve vloženém IDL|
|Chyba kompilátoru C2340|"*identifikátor*': 'static' jde použít jenom uvnitř definice třídy|
|[Chyba kompilátoru C2341](compiler-error-c2341.md)|"*části*': segment musí být definován pomocí #pragma data_seg, code_seg nebo section použít|
|Chyba kompilátoru C2342|Chyba syntaxe: konfliktní kvalifikátory typu|
|Chyba kompilátoru C2343|"*části*': konfliktní atributy section|
|[Chyba kompilátoru C2344](compiler-error-c2344.md)|zarovnání (*číslo*): zarovnání musí být mocninou čísla 2|
|[Chyba kompilátoru C2345](compiler-error-c2345.md)|zarovnání (*číslo*): Neplatná hodnota zarovnání|
|[Chyba kompilátoru C2346](compiler-error-c2346.md)|"*funkce*" se nedá zkompilovat jako nativní: "*vysvětlení*.|
|Chyba kompilátoru C2347|Zastaralé.|
|[Chyba kompilátoru C2348](compiler-error-c2348.md)|"*typ*': není agregací C-style, nejde exportovat ve vloženém IDL|
|[Chyba kompilátoru C2349](compiler-error-c2349.md)|"*funkce*" nelze zkompilovat jako spravovaný: "*vysvětlení*"; použijte #pragma unmanaged|
|[Chyba kompilátoru C2350](compiler-error-c2350.md)|"*identifikátor*" není statický člen.|
|[Chyba kompilátoru C2351](compiler-error-c2351.md)|zastaralá syntaxe inicializace konstruktoru C++|
|[Chyba kompilátoru C2352](compiler-error-c2352.md)|"*identifikátor*': Neplatné volání funkce nestatického člena|
|[Chyba kompilátoru C2353](compiler-error-c2353.md)|Specifikace výjimky není povolená.|
|Chyba kompilátoru C2354|Zastaralé.|
|[Chyba kompilátoru C2355](compiler-error-c2355.md)|'this': může být odkazováno pouze uvnitř nestatické členské funkce nebo inicializátory členů nestatických dat|
|[Chyba kompilátoru C2356](compiler-error-c2356.md)|segment inicializace nesmí změnit průběhu překladové jednotky.|
|[Chyba kompilátoru C2357](compiler-error-c2357.md)|"*identifikátor*': musí být funkce typu"*typ*.|
|Chyba kompilátoru C2358|"*identifikátor*': statická vlastnost nemůže být definovaná mimo definici třídy|
|Chyba kompilátoru C2359|Zastaralé.|
|[Chyba kompilátoru C2360](compiler-error-c2360.md)|Inicializace "*identifikátor*' je na základě jmenovky 'case' přeskočila|
|[Chyba kompilátoru C2361](compiler-error-c2361.md)|Inicializace "*identifikátor*" je přeskočených popisek "default"|
|[Chyba kompilátoru C2362](compiler-error-c2362.md)|Inicializace "*identifikátor*" je přeskočených ' goto *popisek*.|
|Chyba kompilátoru C2363|funkce vnitřního číselného limitu kompilátoru vyžaduje jako argument řetězcový literál|
|[Chyba kompilátoru C2364](compiler-error-c2364.md)|"*typ*': Neplatný typ pro vlastní atribut|
|[Chyba kompilátoru C2365](compiler-error-c2365.md)|"*member1*': předefinování; předchozí definice byla"*člen2*.|
|Chyba kompilátoru C2366|"*identifikátor*': předefinování; odlišné specifikátory implementation_key|
|Chyba kompilátoru C2367|Zastaralé.|
|[Chyba kompilátoru C2368](compiler-error-c2368.md)|"*identifikátor*': předefinování; specifikátory různých přidělení|
|[Chyba kompilátoru C2369](compiler-error-c2369.md)|"*identifikátor*': předefinování; odlišné subscripty|
|[Chyba kompilátoru C2370](compiler-error-c2370.md)|"*identifikátor*': předefinování; odlišná třída úložiště|
|[Chyba kompilátoru C2371](compiler-error-c2371.md)|"*identifikátor*': předefinování; odlišné základní typy|
|[Chyba kompilátoru C2372](compiler-error-c2372.md)|"*identifikátor*': předefinování; odlišné typy indirekce|
|[Chyba kompilátoru C2373](compiler-error-c2373.md)|"*identifikátor*': předefinování; odlišné modifikátory typu|
|[Chyba kompilátoru C2374](compiler-error-c2374.md)|"*identifikátor*': předefinování; vícenásobná inicializace|
|[Chyba kompilátoru C2375](compiler-error-c2375.md)|"*identifikátor*': předefinování; rozdílné propojení|
|[Chyba kompilátoru C2376](compiler-error-c2376.md)|"*identifikátor*': předefinování; odlišné přidělení based|
|[Chyba kompilátoru C2377](compiler-error-c2377.md)|"*identifikátor*': předefinování; typedef nemůže být přetížená s žádným jiným symbolem|
|[Chyba kompilátoru C2378](compiler-error-c2378.md)|"*identifikátor*': předefinování; symbol nemůže být přetížený s typedef|
|[Chyba kompilátoru C2379](compiler-error-c2379.md)|formální parametr *číslo* má jiný typ, pokud se zobrazí výzva|
|[Chyba kompilátoru C2380](compiler-error-c2380.md)|typy předcházející "*identifikátor*" (konstruktor s návratovým typem nebo neplatné předefinování aktuálního názvu třídy?)|
|[Chyba kompilátoru C2381](compiler-error-c2381.md)|"*identifikátor*': předefinování; "__declspec(noreturn)" nebo "[[noreturn]] se liší|
|[Chyba kompilátoru C2382](compiler-error-c2382.md)|"*identifikátor*': předefinování; odlišné specifikace výjimek|
|[Chyba kompilátoru C2383](compiler-error-c2383.md)|"*identifikátor*': výchozí argumenty nejsou povolené pro tento symbol|
|[Chyba kompilátoru C2384](compiler-error-c2384.md)|"*člen*': nejde aplikovat thread_local nebo __declspec(thread) na člen třídy spravované/WinRT|
|[Chyba kompilátoru C2385](compiler-error-c2385.md)|nejednoznačný přístup "*člen*.|
|[Chyba kompilátoru C2386](compiler-error-c2386.md)|"*identifikátor*': symbol s tímto názvem již existuje v aktuálním rozsahu.|
|[Chyba kompilátoru C2387](compiler-error-c2387.md)|"*identifikátor*': nejednoznačná základní třída|
|[Chyba kompilátoru C2388](compiler-error-c2388.md)|"*identifikátor*': symbol nejde deklarovat s __declspec(appdomain) tak s __declspec(process)|
|[Chyba kompilátoru C2389](compiler-error-c2389.md)|"*operátor*': Neplatný operand"nullptr"|
|[Chyba kompilátoru C2390](compiler-error-c2390.md)|"*identifikátor*': Třída nesprávného*specifikátor*"|
|[Chyba kompilátoru C2391](compiler-error-c2391.md)|"*identifikátor*": 'typu friend' nelze použít při definici typu|
|[Chyba kompilátoru C2392](compiler-error-c2392.md)|"*member1*': typy nejsou podporované v typech spravované/WinRT, v opačném případě vrátí kovariantní"*člen2*"by být potlačena za|
|[Chyba kompilátoru C2393](compiler-error-c2393.md)|"*symbol*': symbol na úrovni appdomain nemůže být alokovaný v segmentu"*segmentu*.|
|[Chyba kompilátoru C2394](compiler-error-c2394.md)|"*typ*:: operator *operátor*": CLR/WinRT operátor není platný. Nejméně jeden parametr musí být z následujících typů:  T ^ ", nejde ^ %', 'T ^ &", kde T = "*typ*"|
|[Chyba kompilátoru C2395](compiler-error-c2395.md)|"*typ*:: operator *operátor*": CLR/WinRT operátor není platný. Nejméně jeden parametr musí být z následujících typů: Nejde ", nejde %', 'T &", nejde ^ ", nejde ^ %", nejde ^ & ", kde T ="*typ*"|
|[Chyba kompilátoru C2396](compiler-error-c2396.md)|"*type1*:: operator *type2*": CLR/WinRT uživatelsky definovaný převod funkce není platný. Musíte převést nebo převést na: T ^ ", nejde ^ %', 'T ^ &", kde T = "*type1*"|
|[Chyba kompilátoru C2397](compiler-error-c2397.md)|Převod z '*type1*"do"*type2*' vyžaduje zúžení převodu|
|Chyba kompilátoru C2398|Element '*číslo*': převod z '*type1*"do"*type2*' vyžaduje zúžení převodu|
|Chyba kompilátoru C2399|Zastaralé.|

## <a name="see-also"></a>Viz také:

[C /C++ nástroje chyby a upozornění kompilátoru a sestavení](../compiler-errors-1/c-cpp-build-errors.md) \
[Chyby kompilátoru C2000 - C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
