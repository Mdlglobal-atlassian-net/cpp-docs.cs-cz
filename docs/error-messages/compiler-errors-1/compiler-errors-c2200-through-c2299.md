---
title: Chyby kompilátoru C2200 až C2299
ms.date: 04/21/2019
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
ms.assetid: 9b36d11b-9510-4390-96f1-0c9235124d14
ms.openlocfilehash: 5af97ab46a97d3019abcc937cc0a74c5f865a9ff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62360512"
---
# <a name="compiler-errors-c2200-through-c2299"></a>Chyby kompilátoru C2200 až C2299

Články v této části dokumentace vysvětlují podmnožinu chybové zprávy, které jsou generovány kompilátorem.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Chybové zprávy

|Chyba|Zpráva|
|-----------|-------------|
|[Chyba kompilátoru C2200](compiler-error-c2200.md)|"*funkce*': funkce už je definovaná.|
|[Chyba kompilátoru C2201](compiler-error-c2201.md)|"*identifikátor*': musí mít externí propojení dalo Importovat/exportovat|
|Chyba kompilátoru C2202|"*funkce*': Ne všechny cesty ovládacích prvků vracet hodnotu|
|[Chyba kompilátoru C2203](compiler-error-c2203.md)|delete – operátor nemůže určovat hranice pro pole|
|[Chyba kompilátoru C2204](compiler-error-c2204.md)|"*typ*': v závorkách se našla definice typu|
|[Chyba kompilátoru C2205](compiler-error-c2205.md)|"*identifikátor*': Nelze inicializovat proměnné extern s oborem bloku|
|[Chyba kompilátoru C2206](compiler-error-c2206.md)|"*funkce*': typedef nejde používat pro definici funkce|
|[Chyba kompilátoru C2207](compiler-error-c2207.md)|"*člen*': člen šablony třídy nemůže získat typ funkce.|
|[Chyba kompilátoru C2208](compiler-error-c2208.md)|"*typ*': neexistují žádné členy definované pomocí tohoto typu|
|Chyba kompilátoru C2209|"*identifikátor*': v deklaracích konstruktorů se nemůžou používat aliasy|
|Chyba kompilátoru C2210|"*identifikátor*': rozšíření balíčků nelze použít jako argumenty nezabalených parametrů v šablonách aliasů|
|Chyba kompilátoru C2211|Nevirtuální destruktor v referenční třídě derivované z referenční třídy s veřejným destruktorem musí být také public|
|[Chyba kompilátoru C2212](compiler-error-c2212.md)|"*identifikátor*': možnost __based není dostupná pro ukazatele na funkce|
|[Chyba kompilátoru C2213](compiler-error-c2213.md)|"*identifikátor*': Neplatný argument __based|
|Chyba kompilátoru C2214|ukazatele založené na "void" vyžadují použití: >|
|Chyba kompilátoru C2215|"*– klíčové slovo*' nelze použít s" / arch: SSE.|
|[Chyba kompilátoru C2216](compiler-error-c2216.md)|"*keyword1*"nelze použít s"*keyword2*.|
|[Chyba kompilátoru C2217](compiler-error-c2217.md)|"*atribut1*'vyžaduje'*atribut2*.|
|[Chyba kompilátoru C2218](compiler-error-c2218.md)|"*calltype*' nelze použít s" / arch: IA32.|
|[Chyba kompilátoru C2219](compiler-error-c2219.md)|Chyba syntaxe: kvalifikátor typu musí následovat po "*"|
|[Chyba kompilátoru C2220](compiler-error-c2220.md)|upozornění je považováno za chybu – ne "*filetype*" souboru generován|
|Chyba kompilátoru C2221|Zastaralé.|
|[Chyba kompilátoru C2222](compiler-error-c2222.md)|Neočekávaný typ "*typ*": byl očekáván základní třídu nebo člen|
|[Chyba kompilátoru C2223](compiler-error-c2223.md)|Levá strana "->*identifikátor*" musí ukazovat na strukturu/sjednocení|
|[Chyba kompilátoru C2224](compiler-error-c2224.md)|Levá strana ". *identifikátor*"musí mít typ struktury nebo sjednocení.|
|Chyba kompilátoru C2225|Zastaralé.|
|[Chyba kompilátoru C2226](compiler-error-c2226.md)|Chyba syntaxe: Neočekávaný typ "*typ*.|
|[Chyba kompilátoru C2227](compiler-error-c2227.md)|Levá strana "->*identifikátor*" musí odkazovat na třídu/strukturu/sjednocení/obecný typ.|
|[Chyba kompilátoru C2228](compiler-error-c2228.md)|Levá strana ". *identifikátor*"musí mít třídu/strukturu/sjednocení|
|[Chyba kompilátoru C2229](compiler-error-c2229.md)|Třída/struktura/sjednocení "*typ*' má neplatné pole nulové velikosti|
|Chyba kompilátoru C2230|nepovedlo se najít modul "*název*.|
|[Chyba kompilátoru C2231](compiler-error-c2231.md)|'. *identifikátor*': levý operand ukazuje na "class/struct/union", použijte "->"|
|[Chyba kompilátoru C2232](compiler-error-c2232.md)|"->*identifikátor*': levý operand má" class/struct/union ' typ, použijte"."|
|[Chyba kompilátoru C2233](compiler-error-c2233.md)|"*identifikátor*': pole objektů obsahující pole nulové velikosti jsou neplatná|
|[Chyba kompilátoru C2234](compiler-error-c2234.md)|*identifikátor*': pole odkazů jsou neplatná|
|Chyba kompilátoru C2235|Zastaralé.|
|[Chyba kompilátoru C2236](compiler-error-c2236.md)|Neočekávaný token '*token*". Nezapomněli jste středník (;)?|
|Chyba kompilátoru C2237|Vícenásobná deklarace modulu|
|[Chyba kompilátoru C2238](compiler-error-c2238.md)|neočekávané tokeny předchozí "*token*.|
|Chyba kompilátoru C2239|"*funkce*': Při pokusu o odstranění funkce __declspec(dllexport)|
|Chyba kompilátoru C2240|Zastaralé.|
|[Chyba kompilátoru C2241](compiler-error-c2241.md)|"*identifikátor*': člen má omezený přístup|
|[Chyba kompilátoru C2242](compiler-error-c2242.md)|Název TypeDef nemůže následovat za třídu/strukturu/sjednocení|
|[Chyba kompilátoru C2243](compiler-error-c2243.md)|"*conversion_type*': převod z '*type1*"do"*type2*' existuje, ale je nedostupný|
|[Chyba kompilátoru C2244](compiler-error-c2244.md)|"*identifikátor*': nejde namapovat definici funkce na existující deklaraci|
|[Chyba kompilátoru C2245](compiler-error-c2245.md)|neexistující členská funkce "*funkce*" zadaná jako deklarace friend (signatura členské funkce se neshoduje s žádným přetížením)|
|[Chyba kompilátoru C2246](compiler-error-c2246.md)|"*identifikátor*': Neplatný statický datový člen v lokálně definované třídě|
|[Chyba kompilátoru C2247](compiler-error-c2247.md)|"*identifikátor*" není přístupný. protože "*class1*'používá'*specifikátor*" pro dědění z"*class2*"|
|[Chyba kompilátoru C2248](compiler-error-c2248.md)|"*identifikátor*': Nelze získat přístup k *usnadnění* *člen* deklarovaný ve třídě*třídy*"|
|[Chyba kompilátoru C2249](compiler-error-c2249.md)|"*identifikátor*': není dostupná žádná cesta k *usnadnění* *člen* deklarované v virtuální base '*třídy*"|
|[Chyba kompilátoru C2250](compiler-error-c2250.md)|"*identifikátor*': nejednoznačné dědění *třídy*::*člen*.|
|[Chyba kompilátoru C2251](compiler-error-c2251.md)|obor názvů '*obor názvů*'nemá člena'*identifikátor*"-měli jste na mysli '*člen*"?|
|[Chyba kompilátoru C2252](compiler-error-c2252.md)|explicitní vytváření instancí šablony může probíhat jedině v oboru názvů|
|[Chyba kompilátoru C2253](compiler-error-c2253.md)|"*funkce*': specifikátor pure nebo abstract override povolený jenom pro virtuální funkce|
|[Chyba kompilátoru C2254](compiler-error-c2254.md)|"*funkce*': specifikátor pure nebo abstract override není povolený pro funkci friend|
|[Chyba kompilátoru C2255](compiler-error-c2255.md)|"*element*': není povolené mimo definici třídy|
|[Chyba kompilátoru C2256](compiler-error-c2256.md)|Neplatné použití specifikátoru friend pro "*funkce*.|
|Chyba kompilátoru C2257|"*specifikátor*': není povolený v koncovém typu vrácení|
|[Chyba kompilátoru C2258](compiler-error-c2258.md)|Neplatná syntaxe pure, musí být "= 0"|
|[Chyba kompilátoru C2259](compiler-error-c2259.md)|"*třídy*': Nelze vytvořit instanci abstraktní třídy|
|Chyba kompilátoru C2260|"*specifikátor*': Neplatný specifikátor sestavení friend InternalsVisibleToAttribute|
|[Chyba kompilátoru C2261](compiler-error-c2261.md)|"*řetězec*': odkaz na sestavení je neplatný a nelze rozpoznat|
|[Chyba kompilátoru C2262](compiler-error-c2262.md)|"*specifikátor*": Deklarace InternalsVisibleTo nemůžou mít verze, jazykovou verzi či procesorovou architekturu zadaný|
|Chyba kompilátoru C2263|Zastaralé.|
|[Chyba kompilátoru C2264](compiler-error-c2264.md)|"*funkce*": Chyba v deklaraci nebo definici funkce; funkce se nevolala|
|Chyba kompilátoru C2265|Zastaralé.|
|[Chyba kompilátoru C2266](compiler-error-c2266.md)|"*identifikátor*': odkaz na nekonstantní vázané pole je neplatné|
|[Chyba kompilátoru C2267](compiler-error-c2267.md)|"*funkce*': statické funkce s oborem bloku jsou neplatné|
|[Chyba kompilátoru C2268](compiler-error-c2268.md)|"*funkce*" je pomocné knihovny kompilátoru předdefinované. Pomocné rutiny knihovny nejsou podporované s /GL; Zkompilujte soubor objektu "*filename*" bez/GL.|
|Chyba kompilátoru C2269|Nelze vytvořit ukazatel nebo odkaz na kvalifikovaný typ funkce (vyžaduje pointer-to-member)|
|[Chyba kompilátoru C2270](compiler-error-c2270.md)|"*funkce*': Modifikátory není povolený u nečlenské funkce|
|[Chyba kompilátoru C2271](compiler-error-c2271.md)|"*funkce*': nový/delete nemůžou mít modifikátory formálního seznamu|
|[Chyba kompilátoru C2272](compiler-error-c2272.md)|"*funkce*': Modifikátory není povolený u statických členských funkcí|
|[Chyba kompilátoru C2273](compiler-error-c2273.md)|"*typ*': neplatné jako pravá strana operátoru ->"|
|[Chyba kompilátoru C2274](compiler-error-c2274.md)|"*typ*': neplatné jako pravá strana". "– operátor|
|[Chyba kompilátoru C2275](compiler-error-c2275.md)|"*typ*': Neplatné použití tohoto typu jako výrazu|
|[Chyba kompilátoru C2276](compiler-error-c2276.md)|"*operátor*': Neplatná operace pro vázaný výraz členské funkce|
|[Chyba kompilátoru C2277](compiler-error-c2277.md)|"*funkce*': nejde adresovat tato členská funkce|
|Chyba kompilátoru C2278|Zastaralé.|
|[Chyba kompilátoru C2279](compiler-error-c2279.md)|Specifikace výjimky se nemůže vyskytovat v deklaraci typedef.|
|[Chyba kompilátoru C2280](compiler-error-c2280.md)|"*třídy*::*funkce*': Pokus o odkazování na odstraněnou funkci|
|Chyba kompilátoru C2281|"*třídy*::*funkce*': funkci jde odstranit jenom pro první deklaraci|
|Chyba kompilátoru C2282|"*function1*nemůže přepsat*function2*.|
|[Chyba kompilátoru C2283](compiler-error-c2283.md)|"*identifikátor*': specifikátor pure nebo abstract override není povolený pro Nepojmenovaná třída/struktura|
|Chyba kompilátoru C2284|"*funkce*': Neplatný argument vnitřní funkce, parametr *číslo*|
|[Chyba kompilátoru C2285](compiler-error-c2285.md)|reprezentace ukazatelů na členy už je určená – pragma se ignoruje|
|[Chyba kompilátoru C2286](compiler-error-c2286.md)|ukazatelé na členy třídy "*identifikátor*" reprezentace je už nastavená na *dědičnosti* – deklarace se ignoruje.|
|[Chyba kompilátoru C2287](compiler-error-c2287.md)|"*identifikátor*': reprezentace dědění:"*inheritiance*je míň obecná než požadované*dědičnosti*.|
|Chyba kompilátoru C2288|Zastaralé.|
|[Chyba kompilátoru C2289](compiler-error-c2289.md)|stejný typ kvalifikátor použít víc než jednou|
|[Chyba kompilátoru C2290](compiler-error-c2290.md)|Syntaxe C++ "asm" ignorována. Použijte: __asm.|
|Chyba kompilátoru C2291|Anonymní obor názvů nejde exportovat.|
|[Chyba kompilátoru C2292](compiler-error-c2292.md)|"*identifikátor*': reprezentace dědění pro nejlepší případ: *inheritance1*" deklarovány, ale "*inheritance2*" požadované|
|[Chyba kompilátoru C2293](compiler-error-c2293.md)|"*identifikátor*': neplatné mít členské proměnné jako specifikátor __based.|
|Chyba kompilátoru C2294|není možné exportovat symbol "*identifikátor*' protože má vnitřní propojení|
|[Chyba kompilátoru C2295](compiler-error-c2295.md)|uvozeny řídicími znaky "*znak*": je neplatné v definici makra|
|[Chyba kompilátoru C2296](compiler-error-c2296.md)|"*operátor*': Neplatný levý operand má typ"*typ*"|
|[Chyba kompilátoru C2297](compiler-error-c2297.md)|"*operátor*': neplatné. pravý operand má typ"*typ*.|
|[Chyba kompilátoru C2298](compiler-error-c2298.md)|chybí volání pro vazbu ukazatele na členskou funkci.|
|[Chyba kompilátoru C2299](compiler-error-c2299.md)|"*funkce*': Změna chování: explicitní specializace nemůže být kopírovací konstuktor ani operátor copy assignment|

## <a name="see-also"></a>Viz také:

[C /C++ nástroje chyby a upozornění kompilátoru a sestavení](../compiler-errors-1/c-cpp-build-errors.md) \
[Chyby kompilátoru C2000 - C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
