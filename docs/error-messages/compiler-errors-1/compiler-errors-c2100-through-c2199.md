---
title: Chyby kompilátoru C2100 až C2199
ms.date: 11/17/2017
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
ms.assetid: 1ccab076-0954-4386-b959-d3112a6793ae
ms.openlocfilehash: 98e804b7c53eddf239e752f120854439cc3a0b01
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50546551"
---
# <a name="compiler-errors-c2100-through-c2199"></a>Chyby kompilátoru C2100 až C2199

Články v této části dokumentace vysvětlují podmnožinu chybové zprávy, které jsou generovány kompilátorem.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Chybové zprávy

|Chyba|Zpráva|
|-----------|-------------|
|[Chyba kompilátoru C2100](compiler-error-c2100.md)|Neplatná indirekce|
|[Chyba kompilátoru C2101](compiler-error-c2101.md)|' &' na – konstanta|
|[Chyba kompilátoru C2102](compiler-error-c2102.md)|"&" vyžaduje l-value.|
|[Chyba kompilátoru C2103](compiler-error-c2103.md)|' &' pro proměnnou registru|
|[Chyba kompilátoru C2104](compiler-error-c2104.md)|' &' na bitové pole se ignoruje.|
|[Chyba kompilátoru C2105](compiler-error-c2105.md)|"*operátor*" potřebuje l-value|
|[Chyba kompilátoru C2106](compiler-error-c2106.md)|"*operátor*': levý operand musí být l-value.|
|[Chyba kompilátoru C2107](compiler-error-c2107.md)|Neplatný index. není povolená indirekce.|
|[Chyba kompilátoru C2108](compiler-error-c2108.md)|dolní index není celočíselný typ|
|[Chyba kompilátoru C2109](compiler-error-c2109.md)|Subscript vyžaduje typ pole nebo ukazatel|
|[Chyba kompilátoru C2110](compiler-error-c2110.md)|"+": nejde přidat dva ukazatele|
|[Chyba kompilátoru C2111](compiler-error-c2111.md)|"+": Přidání ukazatele vyžaduje celočíselný operand|
|[Chyba kompilátoru C2112](compiler-error-c2112.md)|'-': operace odečtení ukazatele vyžaduje operand integral nebo pointer|
|[Chyba kompilátoru C2113](compiler-error-c2113.md)|'-': ukazatel se dá odečíst jedině od jiného ukazatele|
|[Chyba kompilátoru C2114](compiler-error-c2114.md)|"*operátor*': ukazatel nalevo; musí být celočíselná hodnota vpravo|
|[Chyba kompilátoru C2115](compiler-error-c2115.md)|"*operátor*': Nekompatibilní typy|
|[Chyba kompilátoru C2116](compiler-error-c2116.md)|seznamy parametrů funkcí se lišily|
|[Chyba kompilátoru C2117](compiler-error-c2117.md)|"*identifikátor*': přetečení hranic pole|
|[Chyba kompilátoru C2118](compiler-error-c2118.md)|záporný subscript|
|C2119 chyby kompilátoru|"*identifikátor*': typ pro"*typ*' nelze odvodit z prázdného inicializátoru|
|[Chyba kompilátoru C2120](compiler-error-c2120.md)|void neplatná se všemi typy|
|[Chyba kompilátoru C2121](compiler-error-c2121.md)|'#': neplatný znak: může být výsledkem rozšíření makra|
|[Chyba kompilátoru C2122](compiler-error-c2122.md)|"*identifikátor*': Parametr prototype v seznamu názvů je neplatný|
|C2123 chyby kompilátoru|"*identifikátor*': šablony aliasů nesmí být explicitně ani částečně serializovat|
|[Chyba kompilátoru C2124](compiler-error-c2124.md)|dělení nulou nebo dělení nulou se zbytkem|
|C2125 chyby kompilátoru|'constexpr' není kompatibilní s "*token*.|
|C2126 chyby kompilátoru|"*identifikátor*' nemůže deklarovat se specifikátorem constexpr.|
|C2127 chyby kompilátoru|"*identifikátor*': Neplatná inicializace entity 'constexpr' se nekonstantní výraz|
|[Chyba kompilátoru C2128](compiler-error-c2128.md)|"*funkce*': alloc_text/same_seg se dá jenom pro funkce s C-linkage|
|[Chyba kompilátoru C2129](compiler-error-c2129.md)|statická funkce "*identifikátor*" deklarovány, ale není definovaný.|
|[Chyba kompilátoru C2130](compiler-error-c2130.md)|#line se očekával řetězec obsahující název souboru, našlo se:*token*.|
|C2131 chyby kompilátoru|Výraz se nevyhodnotil na konstantu|
|[Chyba kompilátoru C2132](compiler-error-c2132.md)|Chyba syntaxe: neočekávaný identifikátor|
|[Chyba kompilátoru C2133](compiler-error-c2133.md)|"*identifikátor*': Neznámá velikost|
|[Chyba kompilátoru C2134](compiler-error-c2134.md)|"*funkce*': volání nemá za následek konstantní výraz|
|[Chyba kompilátoru C2135](compiler-error-c2135.md)|"*operátor*': Neplatná operace bitového pole|
|C2136 chyby kompilátoru|vytváření kontraktů rozhraní API není povolené|
|[Chyba kompilátoru C2137](compiler-error-c2137.md)|prázdná Znaková konstanta|
|[Chyba kompilátoru C2138](compiler-error-c2138.md)|definování výčtu bez členů není platné.|
|[Chyba kompilátoru C2139](compiler-error-c2139.md)|"*třídy*': Nedefinovaná třída není povolená jako argument vlastnosti kompilátoru vnitřního typu"*vlastností*.|
|[Chyba kompilátoru C2140](compiler-error-c2140.md)|"*typ*': typ, který je závislý na parametru obecného typu není povolený jako argument vlastnosti kompilátoru vnitřního typu"*vlastností*.|
|[Chyba kompilátoru C2141](compiler-error-c2141.md)|přetečení velikosti pole|
|[Chyba kompilátoru C2142](compiler-error-c2142.md)|deklarace funkce se liší, parametry proměnné jsou zadané jenom v jednom z nich|
|[Chyba kompilátoru C2143](compiler-error-c2143.md)|Chyba syntaxe: chybí "*token1*"před"*token2*.|
|[Chyba kompilátoru C2144](compiler-error-c2144.md)|Chyba syntaxe: "*typ*"musí předcházet párový příkaz"*token2*.|
|[Chyba kompilátoru C2145](compiler-error-c2145.md)|Chyba syntaxe: chybí "*token*" před identifikátorem|
|[Chyba kompilátoru C2146](compiler-error-c2146.md)|Chyba syntaxe: chybí "*token*'before identifier'*identifikátor*.|
|[Chyba kompilátoru C2147](compiler-error-c2147.md)|Chyba syntaxe: "*token*" je nové klíčové slovo|
|[Chyba kompilátoru C2148](compiler-error-c2148.md)|Celková velikost pole nesmí být delší než 0 x*hodnotu* bajtů|
|[Chyba kompilátoru C2149](compiler-error-c2149.md)|"*identifikátor*': pojmenované bitové pole nemůže mít nulovou šířku|
|[Chyba kompilátoru C2150](compiler-error-c2150.md)|"*identifikátor*': bitové pole musí mít typ int,"signed int"nebo"int bez znaménka.|
|[Chyba kompilátoru C2151](compiler-error-c2151.md)|více než jeden atribut language|
|[Chyba kompilátoru C2152](compiler-error-c2152.md)|"*identifikátor*': ukazatele na funkce s rozdílnými atributy|
|[Chyba kompilátoru C2153](compiler-error-c2153.md)|literály celých čísel musí mít alespoň jednu číslici|
|[Chyba kompilátoru C2154](compiler-error-c2154.md)|"*typ*': jako argument vlastnosti kompilátoru vnitřního typu je povolený jedině typ výčtu '*vlastností*.|
|[Chyba kompilátoru C2155](compiler-error-c2155.md)|'?': Neplatný levý operand. očekával aritmetický typ nebo typ ukazatele|
|[Chyba kompilátoru C2156](compiler-error-c2156.md)|Direktiva pragma musí být mimo funkci.|
|[Chyba kompilátoru C2157](compiler-error-c2157.md)|"*identifikátor*': musí být deklarované před použitím v seznamu direktiv pragma|
|[Chyba kompilátoru C2158](compiler-error-c2158.md)|"*typ*': #pragma make_public directive je momentálně podporována pro pouze nativní nešablonové typy|
|[Chyba kompilátoru C2159](compiler-error-c2159.md)|zadat více než jedna třída úložiště|
|[Chyba kompilátoru C2160](compiler-error-c2160.md)|"##" nemůže být na začátku definice makra|
|[Chyba kompilátoru C2161](compiler-error-c2161.md)|"##" nemůže být na konci definice makra|
|[Chyba kompilátoru C2162](compiler-error-c2162.md)|formální parametr očekávané – makro|
|[Chyba kompilátoru C2163](compiler-error-c2163.md)|"*funkce*': není dostupné jako vnitřní funkce|
|[Chyba kompilátoru C2164](compiler-error-c2164.md)|"*funkce*': není deklarovaná vnitřní funkce|
|[Chyba kompilátoru C2165](compiler-error-c2165.md)|"*modifikátor*': nejdou upravovat ukazatele na data|
|[Chyba kompilátoru C2166](compiler-error-c2166.md)|l-value specifikuje objekt const|
|[Chyba kompilátoru C2167](compiler-error-c2167.md)|"*funkce*': moc velký počet skutečných parametrů pro vnitřní funkci|
|[Chyba kompilátoru C2168](compiler-error-c2168.md)|"*funkce*': moc malý počet skutečných parametrů pro vnitřní funkci|
|[Chyba kompilátoru C2169](compiler-error-c2169.md)|"*funkce*': nelze definovat vnitřní funkci.|
|[Chyba kompilátoru C2170](compiler-error-c2170.md)|"*identifikátor*': není deklarované jako funkce, nemůže jít o vnitřní typ.|
|[Chyba kompilátoru C2171](compiler-error-c2171.md)|"*operátor*': neplatné pro operandy typu '*typ*.|
|[Chyba kompilátoru C2172](compiler-error-c2172.md)|"*funkce*': skutečný parametr není ukazatel: Parametr *číslo*|
|[Chyba kompilátoru C2173](compiler-error-c2173.md)|"*funkce*': skutečný parametr není ukazatel: Parametr *číslo*, seznam parametrů *číslo*|
|[Chyba kompilátoru C2174](compiler-error-c2174.md)|"*funkce*': skutečný parametr má typ void: Parametr *číslo*, seznam parametrů *číslo*|
|[Chyba kompilátoru C2175](compiler-error-c2175.md)|"*národní prostředí*': Neplatné národní prostředí|
|C2176 chyby kompilátoru|příkaz return se nemůže vyskytovat v obslužné rutině – blok try funkce – přidružené ke konstruktoru|
|[Chyba kompilátoru C2177](compiler-error-c2177.md)|Konstanta je moc velká|
|[Chyba kompilátoru C2178](compiler-error-c2178.md)|"*identifikátor*"se nedá deklarovat pomocí"*specifikátor*" specifikátor|
|[Chyba kompilátoru C2179](compiler-error-c2179.md)|"*typ*': argument atributu nemůže používat parametry typu|
|[Chyba kompilátoru C2180](compiler-error-c2180.md)|řídicí výraz má typ "*typ*.|
|[Chyba kompilátoru C2181](compiler-error-c2181.md)|Neplatné else bez odpovídajícího if|
|[Chyba kompilátoru C2182](compiler-error-c2182.md)|"*identifikátor*': Neplatné použití typ void.|
|[Chyba kompilátoru C2183](compiler-error-c2183.md)|Chyba syntaxe: Překladová jednotka je prázdná|
|[Chyba kompilátoru C2184](compiler-error-c2184.md)|"*typ*': Neplatný typ pro výraz __except|
|[Chyba kompilátoru C2185](compiler-error-c2185.md)|"*identifikátor*': neplatné přidělování based|
|[Chyba kompilátoru C2186](compiler-error-c2186.md)|"*operátor*': Neplatný operand typ void.|
|C2187 chyby kompilátoru|Chyba syntaxe: "*token*' se tady neočekávalo.|
|[Chyba kompilátoru C2188](compiler-error-c2188.md)|"*číslo*': moc velké pro široký znak|
|C2189 chyby kompilátoru|atribut 'alignas' nejde použít u bitové pole, parametr funkce, deklaraci výjimky nebo proměnnou deklarovanou s třídou úložiště "register.|
|[Chyba kompilátoru C2190](compiler-error-c2190.md)|první seznam parametrů je delší než druhý.|
|[Chyba kompilátoru C2191](compiler-error-c2191.md)|druhý seznam parametrů je delší než první.|
|[Chyba kompilátoru C2192](compiler-error-c2192.md)|Parametr '*číslo*"deklarace jinou|
|[Chyba kompilátoru C2193](compiler-error-c2193.md)|"*identifikátor*': už je v segmentu|
|[Chyba kompilátoru C2194](compiler-error-c2194.md)|"*identifikátor*": je textový segment|
|[Chyba kompilátoru C2195](compiler-error-c2195.md)|"*identifikátor*": je datový segment|
|[Chyba kompilátoru C2196](compiler-error-c2196.md)|hodnota Case "*hodnotu*' již používá.|
|[Chyba kompilátoru C2197](compiler-error-c2197.md)|"*funkce*': příliš mnoho argumentů pro volání|
|[Chyba kompilátoru C2198](compiler-error-c2198.md)|"*funkce*': moc malý počet argumentů pro volání|
|[Chyba kompilátoru C2199](compiler-error-c2199.md)|Chyba syntaxe: nalezeno '*identifikátor* ("u globálního rozsahu (byla deklarace úmyslná?)|