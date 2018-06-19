---
title: C2200 chyby kompilátoru prostřednictvím C2299 | Microsoft Docs
ms.custom: ''
ms.date: 11/17/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2202
- C2209
- C2210
- C2211
- C2214
- C2215
- C2221
- C2225
- C2230
- C2235
- C2237
- C2239
- C2240
- C2257
- C2260
- C2263
- C2265
- C2269
- C2278
- C2281
- C2282
- C2288
- C2291
- C2294
helpviewer_keywords:
- C2202
- C2209
- C2210
- C2211
- C2214
- C2215
- C2221
- C2225
- C2230
- C2235
- C2237
- C2239
- C2240
- C2257
- C2260
- C2263
- C2265
- C2269
- C2278
- C2281
- C2282
- C2288
- C2291
- C2294
dev_langs:
- C++
ms.assetid: 9b36d11b-9510-4390-96f1-0c9235124d14
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 567cd6a9cbb042027b13056fe50330b31f326529
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33236858"
---
# <a name="compiler-errors-c2200-through-c2299"></a>C2200 chyby kompilátoru prostřednictvím C2299

Články v této části dokumentace vysvětlují podmnožinu chybové zprávy, které jsou generované kompilátorem.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Chybové zprávy

|Chyba|Zpráva|
|-----------|-------------|
|[Chyba kompilátoru C2200](compiler-error-c2200.md)|'*funkce*': funkce již byl definován.|
|[Chyba kompilátoru C2201](compiler-error-c2201.md)|'*identifikátor*': Chcete-li být exportovat nebo importovat musí mít externí propojení|
|C2202 chyby kompilátoru|'*funkce*': Ne všechny cesty řízení vrátit hodnotu|
|[Chyba kompilátoru C2203](compiler-error-c2203.md)|Odstranit operátor nelze zadat rozsah pro pole|
|[Chyba kompilátoru C2204](compiler-error-c2204.md)|'*typ*': Zadejte definice nalezena v závorkách|
|[Chyba kompilátoru C2205](compiler-error-c2205.md)|'*identifikátor*': Nelze inicializovat extern proměnné s rozsahem bloku|
|[Chyba kompilátoru C2206](compiler-error-c2206.md)|'*funkce*': typedef nelze použít pro definice funkce|
|[Chyba kompilátoru C2207](compiler-error-c2207.md)|'*člen*': členem třídy šablony nelze získat typ funkce|
|[Chyba kompilátoru C2208](compiler-error-c2208.md)|'*typ*': žádní členové definovat pomocí tohoto typu|
|C2209 chyby kompilátoru|'*identifikátor*': aliasy nelze použít v deklaracích – konstruktor|
|C2210 chyby kompilátoru|'*identifikátor*': pack rozšiřuje nelze použít jako argumenty pro parametry mnoha funkcemi v šablonách alias|
|C2211 chyby kompilátoru|Bez virtuální destruktor v ref třídy odvozené od třídy ref s veřejné destruktor také musí být veřejné|
|[Chyba kompilátoru C2212](compiler-error-c2212.md)|'*identifikátor*': __based není k dispozici pro ukazatelé na funkce|
|[Chyba kompilátoru C2213](compiler-error-c2213.md)|'*identifikátor*': Neplatný argument __based|
|C2214 chyby kompilátoru|ukazatele podle 'void' vyžadují použití: >|
|C2215 chyby kompilátoru|'*– klíčové slovo*' nelze použít s ' / architektura: SSE.|
|[Chyba kompilátoru C2216](compiler-error-c2216.md)|'*keyword1*'nelze použít s'*keyword2*.|
|[Chyba kompilátoru C2217](compiler-error-c2217.md)|'*atribut1*'vyžaduje'*atribut2*.|
|[Chyba kompilátoru C2218](compiler-error-c2218.md)|'*typ_volání*' nelze použít s ' / architektura: IA32.|
|[Chyba kompilátoru C2219](compiler-error-c2219.md)|Chyba syntaxe: kvalifikátor typu musí být po ' *'|
|[Chyba kompilátoru C2220](compiler-error-c2220.md)|upozornění vyhodnocena jako chyba - ne '*typ souboru*' Soubor byl vytvořen|
|C2221 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C2222](compiler-error-c2222.md)|Neočekávaný typ '*typ*': byl očekáván základní třída nebo člen|
|[Chyba kompilátoru C2223](compiler-error-c2223.md)|nalevo od ' ->*identifikátor*' musí odkazovat na struktura/sjednocení|
|[Chyba kompilátoru C2224](compiler-error-c2224.md)|nalevo od '. *identifikátor*' musí mít typ struktura/sjednocení|
|C2225 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C2226](compiler-error-c2226.md)|Chyba syntaxe: Neočekávaný typ '*typu*.|
|[Chyba kompilátoru C2227](compiler-error-c2227.md)|nalevo od ' ->*identifikátor*, musíte přejít do třídy nebo struktura/sjednocení nebo obecného typu|
|[Chyba kompilátoru C2228](compiler-error-c2228.md)|nalevo od '. *identifikátor*' musí mít třída, struktura/sjednocení|
|[Chyba kompilátoru C2229](compiler-error-c2229.md)|Třída, struktura/sjednocení '*typ*' má neplatné pole nulovou velikostí|
|C2230 chyby kompilátoru|nebyl nalezen modul se*název*.|
|[Chyba kompilátoru C2231](compiler-error-c2231.md)|'. *identifikátor*': operand body zleva 'třída nebo struktura/sjednocení', použijte '->.|
|[Chyba kompilátoru C2232](compiler-error-c2232.md)|' ->*identifikátor*': levý operand má "třída, struktura/sjednocení, typ, použijte"."|
|[Chyba kompilátoru C2233](compiler-error-c2233.md)|'*identifikátor*': pole objekty, které obsahují nulové velikost pole jsou neplatné|
|[Chyba kompilátoru C2234](compiler-error-c2234.md)|*identifikátor*': pole odkazy jsou neplatné|
|C2235 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C2236](compiler-error-c2236.md)|Neočekávaný token '*tokenu*'. Zapomněli jste ';'?|
|C2237 chyby kompilátoru|více modul deklarace|
|[Chyba kompilátoru C2238](compiler-error-c2238.md)|neočekávané tokeny předchozí '*tokenu*.|
|C2239 chyby kompilátoru|'*funkce*': Probíhá pokus o odstranění funkce __declspec(dllexport)|
|C2240 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C2241](compiler-error-c2241.md)|'*identifikátor*': je omezený přístup ke členu|
|[Chyba kompilátoru C2242](compiler-error-c2242.md)|Název definice typu nelze provést třída, struktura/sjednocení|
|[Chyba kompilátoru C2243](compiler-error-c2243.md)|'*conversion_type*': převod '*type1*'do'*type2*' existuje, ale je nedostupná|
|[Chyba kompilátoru C2244](compiler-error-c2244.md)|'*identifikátor*': nelze spárovat definici funkce tak, aby existující deklarace|
|[Chyba kompilátoru C2245](compiler-error-c2245.md)|neexistující – členská funkce '*funkce*' stanoveno, přítele (podpis funkce člen neodpovídá žádné přetížení)|
|[Chyba kompilátoru C2246](compiler-error-c2246.md)|'*identifikátor*': Neplatný statických dat člena v místně definované – třída|
|[Chyba kompilátoru C2247](compiler-error-c2247.md)|'*identifikátor*' není k dispozici protože '*class1*'používá'*specifikátor*' to dědí'*class2*'|
|[Chyba kompilátoru C2248](compiler-error-c2248.md)|'*identifikátor*': Nelze získat přístup k *usnadnění* *člen* deklarovaná ve třídě *– třída*.|
|[Chyba kompilátoru C2249](compiler-error-c2249.md)|'*identifikátor*': žádné a přístupnou cestu k *usnadnění* *člen* deklarované v virtuální základní '*– třída*.|
|[Chyba kompilátoru C2250](compiler-error-c2250.md)|'*identifikátor*': nejednoznačný dědičnosti třídy *– třída*::*člen*.|
|[Chyba kompilátoru C2251](compiler-error-c2251.md)|obor názvů '*obor názvů*'nemá člena'*identifikátor*'-měli jste na mysli '*člen*'?|
|[Chyba kompilátoru C2252](compiler-error-c2252.md)|Explicitní vytvoření instance šablony může dojít pouze v oboru názvů|
|[Chyba kompilátoru C2253](compiler-error-c2253.md)|'*funkce*': pure specifikátor nebo abstraktní override – specifikátor povoleny pouze na virtuální funkce|
|[Chyba kompilátoru C2254](compiler-error-c2254.md)|'*funkce*': pure specifikátor nebo abstraktní override – specifikátor nejsou povoleny u funkce friend|
|[Chyba kompilátoru C2255](compiler-error-c2255.md)|'*element*': povolena mimo tyto definice třídy|
|[Chyba kompilátoru C2256](compiler-error-c2256.md)|Neplatné použití friend specifikátor na '*funkce*.|
|C2257 chyby kompilátoru|'*specifikátor*': specifikátor není povoleno v koncové návratový typ|
|[Chyba kompilátoru C2258](compiler-error-c2258.md)|Neplatná syntaxe čistá, musí být '= 0.|
|[Chyba kompilátoru C2259](compiler-error-c2259.md)|'*třída*': Nelze vytvořit instanci abstraktní třídy|
|C2260 chyby kompilátoru|'*specifikátor*': Neplatný specifikátor sestavení InternalsVisibleToAttribute friend|
|[Chyba kompilátoru C2261](compiler-error-c2261.md)|'*řetězec*': odkaz na sestavení je neplatný a nelze jej přeložit|
|[Chyba kompilátoru C2262](compiler-error-c2262.md)|'*specifikátor*': prohlášeních InternalsVisibleTo nemůže mít procesor, jazykové verze nebo verze architektura zadaný|
|C2263 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C2264](compiler-error-c2264.md)|'*funkce*': Chyba v definici funkce nebo deklarace; není volaná funkce|
|C2265 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C2266](compiler-error-c2266.md)|'*identifikátor*': referenční dokumentace k poli ohraničené nekonstantní je neplatný|
|[Chyba kompilátoru C2267](compiler-error-c2267.md)|'*funkce*': statické funkce s oborem bloku jsou neplatné|
|[Chyba kompilátoru C2268](compiler-error-c2268.md)|'*funkce*' je pomocné rutiny knihovny kompilátoru předdefinované. Pomocné knihovny nepodporuje /GL; kompilace souboru objektu '*filename*' bez /GL.|
|C2269 chyby kompilátoru|Nelze vytvořit ukazatel nebo odkaz na typ kvalifikovaný – funkce (vyžaduje ukazatele na člena)|
|[Chyba kompilátoru C2270](compiler-error-c2270.md)|'*funkce*': Modifikátory není povoleno na nečlenský funkce|
|[Chyba kompilátoru C2271](compiler-error-c2271.md)|'*funkce*': nové nebo odstranění nemůže mít modifikátory formální seznamu|
|[Chyba kompilátoru C2272](compiler-error-c2272.md)|'*funkce*': Modifikátory není povoleno pro statické členské funkce|
|[Chyba kompilátoru C2273](compiler-error-c2273.md)|'*typ*': Neplatný jako pravé straně operátoru '->.|
|[Chyba kompilátoru C2274](compiler-error-c2274.md)|'*typ*': Neplatný jako pravé straně '.' – operátor|
|[Chyba kompilátoru C2275](compiler-error-c2275.md)|'*typ*': Neplatné použití tohoto typu jako výraz|
|[Chyba kompilátoru C2276](compiler-error-c2276.md)|'*operátor*': Neplatná operace s výraz vázané členské funkce|
|[Chyba kompilátoru C2277](compiler-error-c2277.md)|'*funkce*': nelze zpracovat adresu tento – členská funkce|
|C2278 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C2279](compiler-error-c2279.md)|specifikace výjimek se nemůže vyskytovat v deklaraci – typedef|
|[Chyba kompilátoru C2280](compiler-error-c2280.md)|'*– třída*::*funkce*': Při pokusu o odkazu na funkci odstraněné|
|C2281 chyby kompilátoru|'*třída*::*funkce*': funkce lze odstranit pouze na první deklaraci|
|C2282 chyby kompilátoru|'*function1*nejde přepsat*funkce2*.|
|[Chyba kompilátoru C2283](compiler-error-c2283.md)|'*identifikátor*': pure specifikátor nebo abstraktní override – specifikátor není povoleno na nepojmenované třída nebo struktura|
|C2284 chyby kompilátoru|'*funkce*': Neplatný argument vnitřní funkce parametr *číslo*|
|[Chyba kompilátoru C2285](compiler-error-c2285.md)|ukazatelé na členy reprezentace již byla určena – Direktiva pragma ignorovat|
|[Chyba kompilátoru C2286](compiler-error-c2286.md)|ukazatelé na členy '*identifikátor*' reprezentace je již nastaven na *dědičnosti* -deklarace ignorovat|
|[Chyba kompilátoru C2287](compiler-error-c2287.md)|'*identifikátor*': reprezentace dědičnosti: '*inheritiance*je obecné menší než požadované*dědičnosti*.|
|C2288 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C2289](compiler-error-c2289.md)|stejný typ kvalifikátor použít více než jednou.|
|[Chyba kompilátoru C2290](compiler-error-c2290.md)|Syntaxe 'asm' C++ ignorovány. Použijte __asm.|
|C2291 chyby kompilátoru|Anonymní obor názvů se nedá exportovat.|
|[Chyba kompilátoru C2292](compiler-error-c2292.md)|'*identifikátor*': nejlépe případ reprezentace dědičnosti: *inheritance1*' deklarovaný ale '*inheritance2*' požadované|
|[Chyba kompilátoru C2293](compiler-error-c2293.md)|'*identifikátor*': povolen jako __based specifikátor členské proměnné|
|C2294 chyby kompilátoru|nelze exportovat symbol '*identifikátor*, protože obsahuje vnitřní propojení|
|[Chyba kompilátoru C2295](compiler-error-c2295.md)|řídicí sekvencí,*znak*': není povolen v definici makra|
|[Chyba kompilátoru C2296](compiler-error-c2296.md)|'*operátor*': neplatné, levý operand je typu '*typu*.|
|[Chyba kompilátoru C2297](compiler-error-c2297.md)|'*operátor*': neplatný, pravý operand je typu '*typu*.|
|[Chyba kompilátoru C2298](compiler-error-c2298.md)|chybí volání vázané ukazatele na člena – funkce|
|[Chyba kompilátoru C2299](compiler-error-c2299.md)|'*funkce*': změna v chování: explicitní specializace nemůže být kopírovacího konstruktoru nebo operátor přiřazení kopie|
