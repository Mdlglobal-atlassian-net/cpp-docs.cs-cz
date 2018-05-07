---
title: Chyby kompilátoru C2100 až C2199 | Microsoft Docs
ms.custom: ''
ms.date: 11/17/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2119
- C2123
- C2125
- C2126
- C2127
- C2131
- C2136
- C2176
- C2187
- C2189
helpviewer_keywords:
- C2119
- C2123
- C2125
- C2126
- C2127
- C2131
- C2136
- C2176
- C2187
- C2189
dev_langs:
- C++
ms.assetid: 1ccab076-0954-4386-b959-d3112a6793ae
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f276776028fde88e4ef1e4559f0dd4db08abfe03
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-errors-c2100-through-c2199"></a>Chyby kompilátoru C2100 až C2199

Články v této části dokumentace vysvětlují podmnožinu chybové zprávy, které jsou generované kompilátorem.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Chybové zprávy

|Chyba|Zpráva|
|-----------|-------------|
|[Chyba kompilátoru C2100](compiler-error-c2100.md)|Neplatný indirection|
|[Chyba kompilátoru C2101](compiler-error-c2101.md)|' &' na konstanta|
|[Chyba kompilátoru C2102](compiler-error-c2102.md)|' &' vyžaduje hodnotu l|
|[Chyba kompilátoru C2103](compiler-error-c2103.md)|' &' na registrovat proměnné|
|[Chyba kompilátoru C2104](compiler-error-c2104.md)|' & se na poli bit ignorovat|
|[Chyba kompilátoru C2105](compiler-error-c2105.md)|'*operátor*, musí hodnota l|
|[Chyba kompilátoru C2106](compiler-error-c2106.md)|'*operátor*': levý operand musí být hodnota l|
|[Chyba kompilátoru C2107](compiler-error-c2107.md)|Neplatný index, indirection není povoleno|
|[Chyba kompilátoru C2108](compiler-error-c2108.md)|dolní index není celočíselný typ|
|[Chyba kompilátoru C2109](compiler-error-c2109.md)|dolní index vyžaduje typ pole nebo ukazatele|
|[Chyba kompilátoru C2110](compiler-error-c2110.md)|sčítání (+): nelze přidat dva ukazatele|
|[Chyba kompilátoru C2111](compiler-error-c2111.md)|sčítání (+): Přidání ukazatel vyžaduje integrální operand|
|[Chyba kompilátoru C2112](compiler-error-c2112.md)|'-': odečtení ukazatele vyžaduje operand celočíselný nebo ukazatele|
|[Chyba kompilátoru C2113](compiler-error-c2113.md)|'-': ukazatel lze odčítat pouze z jiné ukazatele|
|[Chyba kompilátoru C2114](compiler-error-c2114.md)|'*operátor*': ukazatel na levé straně; potřebám integrální hodnota vpravo|
|[Chyba kompilátoru C2115](compiler-error-c2115.md)|'*operátor*': nekompatibilních typů|
|[Chyba kompilátoru C2116](compiler-error-c2116.md)|seznamy parametrů funkce lišil|
|[Chyba kompilátoru C2117](compiler-error-c2117.md)|'*identifikátor*': pole hranice přetečení|
|[Chyba kompilátoru C2118](compiler-error-c2118.md)|záporné dolní index|
|C2119 chyby kompilátoru|'*identifikátor*': typ '*typ*' nelze odvodit z inicializátoru prázdný|
|[Chyba kompilátoru C2120](compiler-error-c2120.md)|void neplatná ve všech typech|
|[Chyba kompilátoru C2121](compiler-error-c2121.md)|'#': neplatný znak: pravděpodobně výsledkem rozšíření – makro|
|[Chyba kompilátoru C2122](compiler-error-c2122.md)|'*identifikátor*': Parametr prototypu v seznamu neplatný název|
|C2123 chyby kompilátoru|'*identifikátor*': alias šablony nemůže být explicitně nebo částečně specializuje|
|[Chyba kompilátoru C2124](compiler-error-c2124.md)|dělení nebo mod nulou|
|C2125 chyby kompilátoru|'constexpr' není kompatibilní s '*tokenu*.|
|C2126 chyby kompilátoru|'*identifikátor*' nelze deklarovat s specifikátor 'constexpr.|
|C2127 chyby kompilátoru|'*identifikátor*': Neplatný inicializace entity 'constexpr' pomocí výrazu není konstantní.|
|[Chyba kompilátoru C2128](compiler-error-c2128.md)|'*funkce*': alloc_text – / same_seg platí pouze pro funkce C propojení|
|[Chyba kompilátoru C2129](compiler-error-c2129.md)|statické funkce '*identifikátor*' deklarován, ale není definován|
|[Chyba kompilátoru C2130](compiler-error-c2130.md)|#line očekáván řetězec obsahující název souboru, nalezen '*tokenu*.|
|C2131 chyby kompilátoru|neprovedl vyhodnocení výrazu konstanta|
|[Chyba kompilátoru C2132](compiler-error-c2132.md)|Chyba syntaxe: neočekávaný identifikátor|
|[Chyba kompilátoru C2133](compiler-error-c2133.md)|'*identifikátor*': Neznámý velikost|
|[Chyba kompilátoru C2134](compiler-error-c2134.md)|'*funkce*': volání nevede konstantní výraz|
|[Chyba kompilátoru C2135](compiler-error-c2135.md)|'*operátor*': operace neplatná bitová pole|
|C2136 chyby kompilátoru|vytváření kontrakt rozhraní API není povolené|
|[Chyba kompilátoru C2137](compiler-error-c2137.md)|Konstanta prázdný znak|
|[Chyba kompilátoru C2138](compiler-error-c2138.md)|Neplatná k definování výčet bez žádné členy|
|[Chyba kompilátoru C2139](compiler-error-c2139.md)|'*– třída*': Nedefinovaná třída není povolen jako argumentu kompilátoru vnitřního typu znak '*znak*.|
|[Chyba kompilátoru C2140](compiler-error-c2140.md)|'*typ*': typ, který je závislý na parametr obecného typu není povolen jako argument pro kompilátoru vnitřního typu znak '*znak*.|
|[Chyba kompilátoru C2141](compiler-error-c2141.md)|přetečení velikost pole|
|[Chyba kompilátoru C2142](compiler-error-c2142.md)|deklarace funkcí liší, proměnné parametry zadat pouze jednu z nich.|
|[Chyba kompilátoru C2143](compiler-error-c2143.md)|Chyba syntaxe: chybějící '*token1*'než'*token2*.|
|[Chyba kompilátoru C2144](compiler-error-c2144.md)|Chyba syntaxe: '*typ*'musí předcházet'*token2*.|
|[Chyba kompilátoru C2145](compiler-error-c2145.md)|Chyba syntaxe: chybějící '*tokenu*se před identifikátor|
|[Chyba kompilátoru C2146](compiler-error-c2146.md)|Chyba syntaxe: chybějící '*tokenu*'before identifikátor"*identifikátor*.|
|[Chyba kompilátoru C2147](compiler-error-c2147.md)|Chyba syntaxe: '*tokenu*' je new – klíčové slovo|
|[Chyba kompilátoru C2148](compiler-error-c2148.md)|Celková velikost pole nesmí být delší než 0 x*hodnotu* bajtů|
|[Chyba kompilátoru C2149](compiler-error-c2149.md)|'*identifikátor*': pole s názvem bit nemůže mít nulovou šířkou|
|[Chyba kompilátoru C2150](compiler-error-c2150.md)|'*identifikátor*': bit pole musí mít typ int, 'podepsaný int' nebo 'unsigned int.|
|[Chyba kompilátoru C2151](compiler-error-c2151.md)|více než jeden atribut language|
|[Chyba kompilátoru C2152](compiler-error-c2152.md)|'*identifikátor*': ukazatelé na funkce s různé atributy|
|[Chyba kompilátoru C2153](compiler-error-c2153.md)|literály celé číslo musí mít nejméně jednu číslici|
|[Chyba kompilátoru C2154](compiler-error-c2154.md)|'*typ*': výčet je povolen pouze typ jako argument pro kompilátoru vnitřního typu znak '*znak*.|
|[Chyba kompilátoru C2155](compiler-error-c2155.md)|'?': Neplatný levý operand, očekává aritmetické nebo ukazatel typu|
|[Chyba kompilátoru C2156](compiler-error-c2156.md)|Direktiva pragma musí být mimo – funkce|
|[Chyba kompilátoru C2157](compiler-error-c2157.md)|'*identifikátor*': musí být deklarován před použitím v seznamu – Direktiva pragma|
|[Chyba kompilátoru C2158](compiler-error-c2158.md)|'*typ*': #pragma make_public – direktiva v současné době podporuje nativní bez šablony pouze pro typy|
|[Chyba kompilátoru C2159](compiler-error-c2159.md)|zadat více než jeden třídy úložiště|
|[Chyba kompilátoru C2160](compiler-error-c2160.md)|' ##' nelze provést na začátku definice makra|
|[Chyba kompilátoru C2161](compiler-error-c2161.md)|' ##' nelze provést na konci definici – makro|
|[Chyba kompilátoru C2162](compiler-error-c2162.md)|formální parametr očekávané – makro|
|[Chyba kompilátoru C2163](compiler-error-c2163.md)|'*funkce*': není k dispozici jako vnitřní funkce|
|[Chyba kompilátoru C2164](compiler-error-c2164.md)|'*funkce*': není deklarován – vnitřní funkce|
|[Chyba kompilátoru C2165](compiler-error-c2165.md)|'*modifikátor*': ukazatele na data nelze upravit.|
|[Chyba kompilátoru C2166](compiler-error-c2166.md)|l – hodnota určuje const objektu|
|[Chyba kompilátoru C2167](compiler-error-c2167.md)|'*funkce*': příliš mnoho parametrů Skutečná vnitřní funkce|
|[Chyba kompilátoru C2168](compiler-error-c2168.md)|'*funkce*': moc málo skutečné parametry pro vnitřní funkce|
|[Chyba kompilátoru C2169](compiler-error-c2169.md)|'*funkce*': vnitřní funkce, nemůže být definovaný.|
|[Chyba kompilátoru C2170](compiler-error-c2170.md)|'*identifikátor*': není deklarován jako funkce, nemůže být vnitřní funkce|
|[Chyba kompilátoru C2171](compiler-error-c2171.md)|'*operátor*': Neplatný u operandů typu '*typu*.|
|[Chyba kompilátoru C2172](compiler-error-c2172.md)|'*funkce*': skutečný parametr není ukazatel: Parametr *číslo*|
|[Chyba kompilátoru C2173](compiler-error-c2173.md)|'*funkce*': skutečný parametr není ukazatel: Parametr *číslo*, seznam parametrů *číslo*|
|[Chyba kompilátoru C2174](compiler-error-c2174.md)|'*funkce*': skutečný parametr obsahuje typ void: Parametr *číslo*, seznam parametrů *číslo*|
|[Chyba kompilátoru C2175](compiler-error-c2175.md)|'*národního prostředí*': Neplatný národní prostředí|
|C2176 chyby kompilátoru|příkaz return se nemůže vyskytovat v obslužné rutině funkce--bloku try přidružené konstruktor|
|[Chyba kompilátoru C2177](compiler-error-c2177.md)|Konstanta příliš velký.|
|[Chyba kompilátoru C2178](compiler-error-c2178.md)|'*identifikátor*'nelze deklarovat s'*specifikátor*' – specifikátor|
|[Chyba kompilátoru C2179](compiler-error-c2179.md)|'*typ*': argument atributu nelze použít parametry typu|
|[Chyba kompilátoru C2180](compiler-error-c2180.md)|řízení výraz má typ '*typu*.|
|[Chyba kompilátoru C2181](compiler-error-c2181.md)|Neplatná else bez odpovídající Pokud|
|[Chyba kompilátoru C2182](compiler-error-c2182.md)|'*identifikátor*': Neplatné použití typu 'void.|
|[Chyba kompilátoru C2183](compiler-error-c2183.md)|Chyba syntaxe: překlad jednotka je prázdná|
|[Chyba kompilátoru C2184](compiler-error-c2184.md)|'*typ*': Neplatný typ pro __except výraz|
|[Chyba kompilátoru C2185](compiler-error-c2185.md)|'*identifikátor*': Neplatná na základě přidělení|
|[Chyba kompilátoru C2186](compiler-error-c2186.md)|'*operátor*': Neplatný operand typu 'void.|
|C2187 chyby kompilátoru|Chyba syntaxe: '*tokenu*' se zde|
|[Chyba kompilátoru C2188](compiler-error-c2188.md)|'*číslo*': pro široká znaková příliš velká.|
|C2189 chyby kompilátoru|atribut 'alignas' nelze použít pro bitové pole, parametr funkce, deklarace výjimky nebo proměnné deklarovat s registrovat třídu úložiště|
|[Chyba kompilátoru C2190](compiler-error-c2190.md)|první delší než druhý seznam parametrů|
|[Chyba kompilátoru C2191](compiler-error-c2191.md)|druhý parametr seznamu delší než první|
|[Chyba kompilátoru C2192](compiler-error-c2192.md)|Parametr '*číslo*' různé deklarace|
|[Chyba kompilátoru C2193](compiler-error-c2193.md)|'*identifikátor*': již v segmentu|
|[Chyba kompilátoru C2194](compiler-error-c2194.md)|'*identifikátor*': je segment textu|
|[Chyba kompilátoru C2195](compiler-error-c2195.md)|'*identifikátor*': je datový segment|
|[Chyba kompilátoru C2196](compiler-error-c2196.md)|případ hodnotu '*hodnotu*se již používá.|
|[Chyba kompilátoru C2197](compiler-error-c2197.md)|'*funkce*': příliš mnoho argumentů pro volání|
|[Chyba kompilátoru C2198](compiler-error-c2198.md)|'*funkce*': moc málo argumenty pro volání|
|[Chyba kompilátoru C2199](compiler-error-c2199.md)|Chyba syntaxe: nalezen '*identifikátor* (' v globálním oboru (byl deklaraci určený?)|  