---
title: "C2200 chyby kompilátoru prostřednictvím C2299 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
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
dev_langs: C++
ms.assetid: 9b36d11b-9510-4390-96f1-0c9235124d14
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 07d87f9828bac1a025f9ac2375c79f29d96a89b4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-errors-c2200-through-c2299"></a>C2200 chyby kompilátoru prostřednictvím C2299
Články v této části dokumentace obsahují informace o část chyb kompilátoru Visual C++. Můžete přístup k informacím zde nebo v **výstup** oken v sadě Visual Studio, můžete vybrat číslo chyby a potom vyberte klávesy F1.  
  
> [!NOTE]
>  Ne každý [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] chyba je popsána v MSDN. Diagnostické zprávy v mnoha případech poskytuje všechny informace, které jsou k dispozici. Pokud se domníváte, že chybovou zprávu potřebuje další vysvětlení, můžete dejte nám vědět. Můžete použít formulář zpětné vazby na této stránce, nebo přejít na panelu nabídek v sadě Visual Studio a zvolte **pomoci**, **ohlásit chybu**, nebo můžete odeslat zprávu návrhu nebo chyb na [Microsoft Connect](http://connect.microsoft.com/VisualStudio).  
  
 Chyby a upozornění na veřejných fórech MSDN můžete najít další pomoc. [Jazyka Visual C++](http://go.microsoft.com/fwlink/?LinkId=158195) fórum je pro dotazy a v diskusích o [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] syntaxi a kompilátoru jazyka. [Visual C++ Obecné](http://go.microsoft.com/fwlink/?LinkId=158194) fórum je pro dotazy o [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] které nejsou popsané v dalších fóra. Můžete také zjistit nápovědu k nástroji chyby a upozornění na [Stack Overflow](http://stackoverflow.com/).  
  
|Chyba|Zpráva|  
|-----------|-------------|  
|[C2200 chyby kompilátoru](compiler-error-c2200.md)|'*funkce*': funkce již byl definován.|  
|[C2201 chyby kompilátoru](compiler-error-c2201.md)|'*identifikátor*': Chcete-li být exportovat nebo importovat musí mít externí propojení|  
|C2202 chyby kompilátoru|'*funkce*': Ne všechny cesty řízení vrátit hodnotu|  
|[C2203 chyby kompilátoru](compiler-error-c2203.md)|Odstranit operátor nelze zadat rozsah pro pole|  
|[C2204 chyby kompilátoru](compiler-error-c2204.md)|'*typ*': Zadejte definice nalezena v závorkách|  
|[C2205 chyby kompilátoru](compiler-error-c2205.md)|'*identifikátor*': Nelze inicializovat extern proměnné s rozsahem bloku|  
|[C2206 chyby kompilátoru](compiler-error-c2206.md)|'*funkce*': typedef nelze použít pro definice funkce|  
|[C2207 chyby kompilátoru](compiler-error-c2207.md)|'*člen*': členem třídy šablony nelze získat typ funkce|  
|[C2208 chyby kompilátoru](compiler-error-c2208.md)|'*typ*': žádní členové definovat pomocí tohoto typu|  
|C2209 chyby kompilátoru|'*identifikátor*': aliasy nelze použít v deklaracích – konstruktor|  
|C2210 chyby kompilátoru|'*identifikátor*': pack rozšiřuje nelze použít jako argumenty pro parametry mnoha funkcemi v šablonách alias|  
|C2211 chyby kompilátoru|Bez virtuální destruktor v ref třídy odvozené od třídy ref s veřejné destruktor také musí být veřejné|  
|[C2212 chyby kompilátoru](compiler-error-c2212.md)|'*identifikátor*': __based není k dispozici pro ukazatelé na funkce|  
|[C2213 chyby kompilátoru](compiler-error-c2213.md)|'*identifikátor*': Neplatný argument __based|  
|C2214 chyby kompilátoru|ukazatele podle 'void' vyžadují použití: >|  
|C2215 chyby kompilátoru|'*– klíčové slovo*' nelze použít s ' / architektura: SSE.|  
|[C2216 chyby kompilátoru](compiler-error-c2216.md)|'*keyword1*'nelze použít s'*keyword2*.|  
|[C2217 chyby kompilátoru](compiler-error-c2217.md)|'*atribut1*'vyžaduje'*atribut2*.|  
|[Chyba kompilátoru C2218](compiler-error-c2218.md)|'*typ_volání*' nelze použít s ' / architektura: IA32.|  
|[C2219 chyby kompilátoru](compiler-error-c2219.md)|Chyba syntaxe: kvalifikátor typu musí být po ' *'|  
|[C2220 chyby kompilátoru](compiler-error-c2220.md)|upozornění vyhodnocena jako chyba - ne '*typ souboru*' Soubor byl vytvořen|  
|C2221 chyby kompilátoru|Zastaralé.|  
|[C2222 chyby kompilátoru](compiler-error-c2222.md)|Neočekávaný typ '*typ*': byl očekáván základní třída nebo člen|  
|[C2223 chyby kompilátoru](compiler-error-c2223.md)|nalevo od ' ->*identifikátor*' musí odkazovat na struktura/sjednocení|  
|[C2224 chyby kompilátoru](compiler-error-c2224.md)|nalevo od '. *identifikátor*' musí mít typ struktura/sjednocení|  
|C2225 chyby kompilátoru|Zastaralé.|  
|[C2226 chyby kompilátoru](compiler-error-c2226.md)|Chyba syntaxe: Neočekávaný typ '*typu*.|  
|[C2227 chyby kompilátoru](compiler-error-c2227.md)|nalevo od ' ->*identifikátor*, musíte přejít do třídy nebo struktura/sjednocení nebo obecného typu|  
|[C2228 chyby kompilátoru](compiler-error-c2228.md)|nalevo od '. *identifikátor*' musí mít třída, struktura/sjednocení|  
|[C2229 chyby kompilátoru](compiler-error-c2229.md)|Třída, struktura/sjednocení '*typ*' má neplatné pole nulovou velikostí|  
|C2230 chyby kompilátoru|nebyl nalezen modul se*název*.|  
|[C2231 chyby kompilátoru](compiler-error-c2231.md)|'. *identifikátor*': operand body zleva 'třída nebo struktura/sjednocení', použijte '->.|  
|[C2232 chyby kompilátoru](compiler-error-c2232.md)|' ->*identifikátor*': levý operand má "třída, struktura/sjednocení, typ, použijte"."|  
|[C2233 chyby kompilátoru](compiler-error-c2233.md)|'*identifikátor*': pole objekty, které obsahují nulové velikost pole jsou neplatné|  
|[C2234 chyby kompilátoru](compiler-error-c2234.md)|*identifikátor*': pole odkazy jsou neplatné|  
|C2235 chyby kompilátoru|Zastaralé.|  
|[C2236 chyby kompilátoru](compiler-error-c2236.md)|Neočekávaný token '*tokenu*'. Zapomněli jste ';'?|  
|C2237 chyby kompilátoru|více modul deklarace|  
|[C2238 chyby kompilátoru](compiler-error-c2238.md)|neočekávané tokeny předchozí '*tokenu*.|  
|C2239 chyby kompilátoru|'*funkce*': Probíhá pokus o odstranění funkce __declspec(dllexport)|  
|C2240 chyby kompilátoru|Zastaralé.|  
|[C2241 chyby kompilátoru](compiler-error-c2241.md)|'*identifikátor*': je omezený přístup ke členu|  
|[C2242 chyby kompilátoru](compiler-error-c2242.md)|Název definice typu nelze provést třída, struktura/sjednocení|  
|[C2243 chyby kompilátoru](compiler-error-c2243.md)|'*conversion_type*': převod '*type1*'do'*type2*' existuje, ale je nedostupná|  
|[C2244 chyby kompilátoru](compiler-error-c2244.md)|'*identifikátor*': nelze spárovat definici funkce tak, aby existující deklarace|  
|[C2245 chyby kompilátoru](compiler-error-c2245.md)|neexistující – členská funkce '*funkce*' stanoveno, přítele (podpis funkce člen neodpovídá žádné přetížení)|  
|[C2246 chyby kompilátoru](compiler-error-c2246.md)|'*identifikátor*': Neplatný statických dat člena v místně definované – třída|  
|[C2247 chyby kompilátoru](compiler-error-c2247.md)|'*identifikátor*' není k dispozici protože '*class1*'používá'*specifikátor*' to dědí'*class2*'|  
|[C2248 chyby kompilátoru](compiler-error-c2248.md)|'*identifikátor*': Nelze získat přístup k *usnadnění* *člen* deklarovaná ve třídě*– třída*.|  
|[C2249 chyby kompilátoru](compiler-error-c2249.md)|'*identifikátor*': žádné a přístupnou cestu k *usnadnění* *člen* deklarované v virtuální základní '*– třída*.|  
|[C2250 chyby kompilátoru](compiler-error-c2250.md)|'*identifikátor*': nejednoznačný dědičnosti třídy *– třída*::*člen*.|  
|[C2251 chyby kompilátoru](compiler-error-c2251.md)|obor názvů '*obor názvů*'nemá člena'*identifikátor*'-měli jste na mysli '*člen*'?|  
|[C2252 chyby kompilátoru](compiler-error-c2252.md)|Explicitní vytvoření instance šablony může dojít pouze v oboru názvů|  
|[C2253 chyby kompilátoru](compiler-error-c2253.md)|'*funkce*': pure specifikátor nebo abstraktní override – specifikátor povoleny pouze na virtuální funkce|  
|[C2254 chyby kompilátoru](compiler-error-c2254.md)|'*funkce*': pure specifikátor nebo abstraktní override – specifikátor nejsou povoleny u funkce friend|  
|[C2255 chyby kompilátoru](compiler-error-c2255.md)|'*element*': povolena mimo tyto definice třídy|  
|[C2256 chyby kompilátoru](compiler-error-c2256.md)|Neplatné použití friend specifikátor na '*funkce*.|  
|C2257 chyby kompilátoru|'*specifikátor*': specifikátor není povoleno v koncové návratový typ|  
|[C2258 chyby kompilátoru](compiler-error-c2258.md)|Neplatná syntaxe čistá, musí být '= 0.|  
|[C2259 chyby kompilátoru](compiler-error-c2259.md)|'*třída*': Nelze vytvořit instanci abstraktní třídy|  
|C2260 chyby kompilátoru|'*specifikátor*': Neplatný specifikátor sestavení InternalsVisibleToAttribute friend|  
|[Chyba kompilátoru C2261](compiler-error-c2261.md)|'*řetězec*': odkaz na sestavení je neplatný a nelze jej přeložit|  
|[C2262 chyby kompilátoru](compiler-error-c2262.md)|'*specifikátor*': prohlášeních InternalsVisibleTo nemůže mít procesor, jazykové verze nebo verze architektura zadaný|  
|C2263 chyby kompilátoru|Zastaralé.|  
|[C2264 chyby kompilátoru](compiler-error-c2264.md)|'*funkce*': Chyba v definici funkce nebo deklarace; není volaná funkce|  
|C2265 chyby kompilátoru|Zastaralé.|  
|[C2266 chyby kompilátoru](compiler-error-c2266.md)|'*identifikátor*': referenční dokumentace k poli ohraničené nekonstantní je neplatný|  
|[C2267 chyby kompilátoru](compiler-error-c2267.md)|'*funkce*': statické funkce s oborem bloku jsou neplatné|  
|[C2268 chyby kompilátoru](compiler-error-c2268.md)|'*funkce*' je pomocné rutiny knihovny kompilátoru předdefinované. Pomocné knihovny nepodporuje /GL; kompilace souboru objektu '*filename*' bez /GL.|  
|C2269 chyby kompilátoru|Nelze vytvořit ukazatel nebo odkaz na typ kvalifikovaný – funkce (vyžaduje ukazatele na člena)|  
|[C2270 chyby kompilátoru](compiler-error-c2270.md)|'*funkce*': Modifikátory není povoleno na nečlenský funkce|  
|[C2271 chyby kompilátoru](compiler-error-c2271.md)|'*funkce*': nové nebo odstranění nemůže mít modifikátory formální seznamu|  
|[C2272 chyby kompilátoru](compiler-error-c2272.md)|'*funkce*': Modifikátory není povoleno pro statické členské funkce|  
|[C2273 chyby kompilátoru](compiler-error-c2273.md)|'*typ*': Neplatný jako pravé straně operátoru '->.|  
|[C2274 chyby kompilátoru](compiler-error-c2274.md)|'*typ*': Neplatný jako pravé straně '.' – operátor|  
|[C2275 chyby kompilátoru](compiler-error-c2275.md)|'*typ*': Neplatné použití tohoto typu jako výraz|  
|[C2276 chyby kompilátoru](compiler-error-c2276.md)|'*operátor*': Neplatná operace s výraz vázané členské funkce|  
|[C2277 chyby kompilátoru](compiler-error-c2277.md)|'*funkce*': nelze zpracovat adresu tento – členská funkce|  
|C2278 chyby kompilátoru|Zastaralé.|  
|[C2279 chyby kompilátoru](compiler-error-c2279.md)|specifikace výjimek se nemůže vyskytovat v deklaraci – typedef|  
|[C2280 chyby kompilátoru](compiler-error-c2280.md)|'*– třída*::*funkce*': Při pokusu o odkazu na funkci odstraněné|  
|C2281 chyby kompilátoru|'*třída*::*funkce*': funkce lze odstranit pouze na první deklaraci|  
|C2282 chyby kompilátoru|'*function1*nejde přepsat*funkce2*.|  
|[C2283 chyby kompilátoru](compiler-error-c2283.md)|'*identifikátor*': pure specifikátor nebo abstraktní override – specifikátor není povoleno na nepojmenované třída nebo struktura|  
|C2284 chyby kompilátoru|'*funkce*': Neplatný argument vnitřní funkce parametr *číslo*|  
|[C2285 chyby kompilátoru](compiler-error-c2285.md)|ukazatelé na členy reprezentace již byla určena – Direktiva pragma ignorovat|  
|[C2286 chyby kompilátoru](compiler-error-c2286.md)|ukazatelé na členy '*identifikátor*' reprezentace je již nastaven na *dědičnosti* -deklarace ignorovat|  
|[C2287 chyby kompilátoru](compiler-error-c2287.md)|'*identifikátor*': reprezentace dědičnosti: '*inheritiance*je obecné menší než požadované*dědičnosti*.|  
|C2288 chyby kompilátoru|Zastaralé.|  
|[C2289 chyby kompilátoru](compiler-error-c2289.md)|stejný typ kvalifikátor použít více než jednou.|  
|[C2290 chyby kompilátoru](compiler-error-c2290.md)|Syntaxe 'asm' C++ ignorovány. Použijte __asm.|  
|C2291 chyby kompilátoru|Anonymní obor názvů se nedá exportovat.|  
|[C2292 chyby kompilátoru](compiler-error-c2292.md)|'*identifikátor*': nejlépe případ reprezentace dědičnosti: *inheritance1*' deklarovaný ale '*inheritance2*' požadované|  
|[C2293 chyby kompilátoru](compiler-error-c2293.md)|'*identifikátor*': povolen jako __based specifikátor členské proměnné|  
|C2294 chyby kompilátoru|nelze exportovat symbol '*identifikátor*, protože obsahuje vnitřní propojení|  
|[C2295 chyby kompilátoru](compiler-error-c2295.md)|řídicí sekvencí,*znak*': není povolen v definici makra|  
|[C2296 chyby kompilátoru](compiler-error-c2296.md)|'*operátor*': neplatné, levý operand je typu '*typu*.|  
|[C2297 chyby kompilátoru](compiler-error-c2297.md)|'*operátor*': neplatný, pravý operand je typu '*typu*.|  
|[C2298 chyby kompilátoru](compiler-error-c2298.md)|chybí volání vázané ukazatele na člena – funkce|  
|[C2299 chyby kompilátoru](compiler-error-c2299.md)|'*funkce*': změna v chování: explicitní specializace nemůže být kopírovacího konstruktoru nebo operátor přiřazení kopie|  
