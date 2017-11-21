---
title: "Chyby kompilátoru C2100 až C2199 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
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
dev_langs: C++
ms.assetid: 1ccab076-0954-4386-b959-d3112a6793ae
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9f03dc203c34e5389eb153288ccdc92e77473686
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-errors-c2100-through-c2199"></a>Chyby kompilátoru C2100 až C2199
Články v této části dokumentace obsahují informace o část chyb kompilátoru Visual C++. Můžete přístup k informacím zde nebo v **výstup** oken v sadě Visual Studio, můžete vybrat číslo chyby a potom vyberte klávesy F1.  
  
> [!NOTE]
>  Ne každý [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] chyba je popsána v MSDN. Diagnostické zprávy v mnoha případech poskytuje všechny informace, které jsou k dispozici. Pokud se domníváte, že chybovou zprávu potřebuje další vysvětlení, můžete dejte nám vědět. Můžete použít formulář zpětné vazby na této stránce, nebo přejít na panelu nabídek v sadě Visual Studio a zvolte **pomoci**, **ohlásit chybu**, nebo můžete odeslat zprávu návrhu nebo chyb na [Microsoft Connect](http://connect.microsoft.com/VisualStudio).  
  
 Chyby a upozornění na veřejných fórech MSDN můžete najít další pomoc. [Jazyka Visual C++](http://go.microsoft.com/fwlink/?LinkId=158195) fórum je pro dotazy a v diskusích o [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] syntaxi a kompilátoru jazyka. [Visual C++ Obecné](http://go.microsoft.com/fwlink/?LinkId=158194) fórum je pro dotazy o [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] které nejsou popsané v dalších fóra. Můžete také zjistit nápovědu k nástroji chyby a upozornění na [Stack Overflow](http://stackoverflow.com/).  
  
|Chyba|Zpráva|  
|-----------|-------------|  
|[C2100 chyby kompilátoru](compiler-error-c2100.md)|Neplatný indirection|  
|[C2101 chyby kompilátoru](compiler-error-c2101.md)|' &' na konstanta|  
|[C2102 chyby kompilátoru](compiler-error-c2102.md)|' &' vyžaduje hodnotu l|  
|[C2103 chyby kompilátoru](compiler-error-c2103.md)|' &' na registrovat proměnné|  
|[C2104 chyby kompilátoru](compiler-error-c2104.md)|' & se na poli bit ignorovat|  
|[C2105 chyby kompilátoru](compiler-error-c2105.md)|'*operátor*, musí hodnota l|  
|[C2106 chyby kompilátoru](compiler-error-c2106.md)|'*operátor*': levý operand musí být hodnota l|  
|[C2107 chyby kompilátoru](compiler-error-c2107.md)|Neplatný index, indirection není povoleno|  
|[C2108 chyby kompilátoru](compiler-error-c2108.md)|dolní index není celočíselný typ|  
|[C2109 chyby kompilátoru](compiler-error-c2109.md)|dolní index vyžaduje typ pole nebo ukazatele|  
|[C2110 chyby kompilátoru](compiler-error-c2110.md)|sčítání (+): nelze přidat dva ukazatele|  
|[C2111 chyby kompilátoru](compiler-error-c2111.md)|sčítání (+): Přidání ukazatel vyžaduje integrální operand|  
|[C2112 chyby kompilátoru](compiler-error-c2112.md)|'-': odečtení ukazatele vyžaduje operand celočíselný nebo ukazatele|  
|[C2113 chyby kompilátoru](compiler-error-c2113.md)|'-': ukazatel lze odčítat pouze z jiné ukazatele|  
|[C2114 chyby kompilátoru](compiler-error-c2114.md)|'*operátor*': ukazatel na levé straně; potřebám integrální hodnota vpravo|  
|[C2115 chyby kompilátoru](compiler-error-c2115.md)|'*operátor*': nekompatibilních typů|  
|[C2116 chyby kompilátoru](compiler-error-c2116.md)|seznamy parametrů funkce lišil|  
|[C2117 chyby kompilátoru](compiler-error-c2117.md)|'*identifikátor*': pole hranice přetečení|  
|[C2118 chyby kompilátoru](compiler-error-c2118.md)|záporné dolní index|  
|C2119 chyby kompilátoru|'*identifikátor*': typ '*typ*' nelze odvodit z inicializátoru prázdný|  
|[C2120 chyby kompilátoru](compiler-error-c2120.md)|void neplatná ve všech typech|  
|[C2121 chyby kompilátoru](compiler-error-c2121.md)|'#': neplatný znak: pravděpodobně výsledkem rozšíření – makro|  
|[C2122 chyby kompilátoru](compiler-error-c2122.md)|'*identifikátor*': Parametr prototypu v seznamu neplatný název|  
|C2123 chyby kompilátoru|'*identifikátor*': alias šablony nemůže být explicitně nebo částečně specializuje|  
|[C2124 chyby kompilátoru](compiler-error-c2124.md)|dělení nebo mod nulou|  
|C2125 chyby kompilátoru|'constexpr' není kompatibilní s '*tokenu*.|  
|C2126 chyby kompilátoru|'*identifikátor*' nelze deklarovat s specifikátor 'constexpr.|  
|C2127 chyby kompilátoru|'*identifikátor*': Neplatný inicializace entity 'constexpr' pomocí výrazu není konstantní.|  
|[C2128 chyby kompilátoru](compiler-error-c2128.md)|'*funkce*': alloc_text – / same_seg platí pouze pro funkce C propojení|  
|[C2129 chyby kompilátoru](compiler-error-c2129.md)|statické funkce '*identifikátor*' deklarován, ale není definován|  
|[C2130 chyby kompilátoru](compiler-error-c2130.md)|#line očekáván řetězec obsahující název souboru, nalezen '*tokenu*.|  
|C2131 chyby kompilátoru|neprovedl vyhodnocení výrazu konstanta|  
|[C2132 chyby kompilátoru](compiler-error-c2132.md)|Chyba syntaxe: neočekávaný identifikátor|  
|[C2133 chyby kompilátoru](compiler-error-c2133.md)|'*identifikátor*': Neznámý velikost|  
|[C2134 chyby kompilátoru](compiler-error-c2134.md)|'*funkce*': volání nevede konstantní výraz|  
|[C2135 chyby kompilátoru](compiler-error-c2135.md)|'*operátor*': operace neplatná bitová pole|  
|C2136 chyby kompilátoru|vytváření kontrakt rozhraní API není povolené|  
|[C2137 chyby kompilátoru](compiler-error-c2137.md)|Konstanta prázdný znak|  
|[C2138 chyby kompilátoru](compiler-error-c2138.md)|Neplatná k definování výčet bez žádné členy|  
|[C2139 chyby kompilátoru](compiler-error-c2139.md)|'*– třída*': Nedefinovaná třída není povolen jako argumentu kompilátoru vnitřního typu znak '*znak*.|  
|[C2140 chyby kompilátoru](compiler-error-c2140.md)|'*typ*': typ, který je závislý na parametr obecného typu není povolen jako argument pro kompilátoru vnitřního typu znak '*znak*.|  
|[C2141 chyby kompilátoru](compiler-error-c2141.md)|přetečení velikost pole|  
|[C2142 chyby kompilátoru](compiler-error-c2142.md)|deklarace funkcí liší, proměnné parametry zadat pouze jednu z nich.|  
|[C2143 chyby kompilátoru](compiler-error-c2143.md)|Chyba syntaxe: chybějící '*token1*'než'*token2*.|  
|[C2144 chyby kompilátoru](compiler-error-c2144.md)|Chyba syntaxe: '*typ*'musí předcházet'*token2*.|  
|[C2145 chyby kompilátoru](compiler-error-c2145.md)|Chyba syntaxe: chybějící '*tokenu*se před identifikátor|  
|[C2146 chyby kompilátoru](compiler-error-c2146.md)|Chyba syntaxe: chybějící '*tokenu*'before identifikátor"*identifikátor*.|  
|[C2147 chyby kompilátoru](compiler-error-c2147.md)|Chyba syntaxe: '*tokenu*' je new – klíčové slovo|  
|[C2148 chyby kompilátoru](compiler-error-c2148.md)|Celková velikost pole nesmí být delší než 0 x*hodnotu* bajtů|  
|[C2149 chyby kompilátoru](compiler-error-c2149.md)|'*identifikátor*': pole s názvem bit nemůže mít nulovou šířkou|  
|[C2150 chyby kompilátoru](compiler-error-c2150.md)|'*identifikátor*': bit pole musí mít typ int, 'podepsaný int' nebo 'unsigned int.|  
|[C2151 chyby kompilátoru](compiler-error-c2151.md)|více než jeden atribut language|  
|[C2152 chyby kompilátoru](compiler-error-c2152.md)|'*identifikátor*': ukazatelé na funkce s různé atributy|  
|[C2153 chyby kompilátoru](compiler-error-c2153.md)|literály celé číslo musí mít nejméně jednu číslici|  
|[C2154 chyby kompilátoru](compiler-error-c2154.md)|'*typ*': výčet je povolen pouze typ jako argument pro kompilátoru vnitřního typu znak '*znak*.|  
|[C2155 chyby kompilátoru](compiler-error-c2155.md)|'?': Neplatný levý operand, očekává aritmetické nebo ukazatel typu|  
|[C2156 chyby kompilátoru](compiler-error-c2156.md)|Direktiva pragma musí být mimo – funkce|  
|[C2157 chyby kompilátoru](compiler-error-c2157.md)|'*identifikátor*': musí být deklarován před použitím v seznamu – Direktiva pragma|  
|[C2158 chyby kompilátoru](compiler-error-c2158.md)|'*typ*': #pragma make_public – direktiva v současné době podporuje nativní bez šablony pouze pro typy|  
|[C2159 chyby kompilátoru](compiler-error-c2159.md)|zadat více než jeden třídy úložiště|  
|[C2160 chyby kompilátoru](compiler-error-c2160.md)|' ##' nelze provést na začátku definice makra|  
|[C2161 chyby kompilátoru](compiler-error-c2161.md)|' ##' nelze provést na konci definici – makro|  
|[C2162 chyby kompilátoru](compiler-error-c2162.md)|formální parametr očekávané – makro|  
|[C2163 chyby kompilátoru](compiler-error-c2163.md)|'*funkce*': není k dispozici jako vnitřní funkce|  
|[C2164 chyby kompilátoru](compiler-error-c2164.md)|'*funkce*': není deklarován – vnitřní funkce|  
|[C2165 chyby kompilátoru](compiler-error-c2165.md)|'*modifikátor*': ukazatele na data nelze upravit.|  
|[C2166 chyby kompilátoru](compiler-error-c2166.md)|l – hodnota určuje const objektu|  
|[C2167 chyby kompilátoru](compiler-error-c2167.md)|'*funkce*': příliš mnoho parametrů Skutečná vnitřní funkce|  
|[C2168 chyby kompilátoru](compiler-error-c2168.md)|'*funkce*': moc málo skutečné parametry pro vnitřní funkce|  
|[C2169 chyby kompilátoru](compiler-error-c2169.md)|'*funkce*': vnitřní funkce, nemůže být definovaný.|  
|[C2170 chyby kompilátoru](compiler-error-c2170.md)|'*identifikátor*': není deklarován jako funkce, nemůže být vnitřní funkce|  
|[C2171 chyby kompilátoru](compiler-error-c2171.md)|'*operátor*': Neplatný u operandů typu '*typu*.|  
|[C2172 chyby kompilátoru](compiler-error-c2172.md)|'*funkce*': skutečný parametr není ukazatel: Parametr *číslo*|  
|[C2173 chyby kompilátoru](compiler-error-c2173.md)|'*funkce*': skutečný parametr není ukazatel: Parametr *číslo*, seznam parametrů *číslo*|  
|[C2174 chyby kompilátoru](compiler-error-c2174.md)|'*funkce*': skutečný parametr obsahuje typ void: Parametr *číslo*, seznam parametrů *číslo*|  
|[C2175 chyby kompilátoru](compiler-error-c2175.md)|'*národního prostředí*': Neplatný národní prostředí|  
|C2176 chyby kompilátoru|příkaz return se nemůže vyskytovat v obslužné rutině funkce--bloku try přidružené konstruktor|  
|[C2177 chyby kompilátoru](compiler-error-c2177.md)|Konstanta příliš velký.|  
|[C2178 chyby kompilátoru](compiler-error-c2178.md)|'*identifikátor*'nelze deklarovat s'*specifikátor*' – specifikátor|  
|[C2179 chyby kompilátoru](compiler-error-c2179.md)|'*typ*': argument atributu nelze použít parametry typu|  
|[C2180 chyby kompilátoru](compiler-error-c2180.md)|řízení výraz má typ '*typu*.|  
|[C2181 chyby kompilátoru](compiler-error-c2181.md)|Neplatná else bez odpovídající Pokud|  
|[C2182 chyby kompilátoru](compiler-error-c2182.md)|'*identifikátor*': Neplatné použití typu 'void.|  
|[C2183 chyby kompilátoru](compiler-error-c2183.md)|Chyba syntaxe: překlad jednotka je prázdná|  
|[C2184 chyby kompilátoru](compiler-error-c2184.md)|'*typ*': Neplatný typ pro __except výraz|  
|[C2185 chyby kompilátoru](compiler-error-c2185.md)|'*identifikátor*': Neplatná na základě přidělení|  
|[C2186 chyby kompilátoru](compiler-error-c2186.md)|'*operátor*': Neplatný operand typu 'void.|  
|C2187 chyby kompilátoru|Chyba syntaxe: '*tokenu*' se zde|  
|[C2188 chyby kompilátoru](compiler-error-c2188.md)|'*číslo*': pro široká znaková příliš velká.|  
|C2189 chyby kompilátoru|atribut 'alignas' nelze použít pro bitové pole, parametr funkce, deklarace výjimky nebo proměnné deklarovat s registrovat třídu úložiště|  
|[C2190 chyby kompilátoru](compiler-error-c2190.md)|první delší než druhý seznam parametrů|  
|[C2191 chyby kompilátoru](compiler-error-c2191.md)|druhý parametr seznamu delší než první|  
|[C2192 chyby kompilátoru](compiler-error-c2192.md)|Parametr '*číslo*' různé deklarace|  
|[C2193 chyby kompilátoru](compiler-error-c2193.md)|'*identifikátor*': již v segmentu|  
|[C2194 chyby kompilátoru](compiler-error-c2194.md)|'*identifikátor*': je segment textu|  
|[C2195 chyby kompilátoru](compiler-error-c2195.md)|'*identifikátor*': je datový segment|  
|[C2196 chyby kompilátoru](compiler-error-c2196.md)|případ hodnotu '*hodnotu*se již používá.|  
|[C2197 chyby kompilátoru](compiler-error-c2197.md)|'*funkce*': příliš mnoho argumentů pro volání|  
|[C2198 chyby kompilátoru](compiler-error-c2198.md)|'*funkce*': moc málo argumenty pro volání|  
|[C2199 chyby kompilátoru](compiler-error-c2199.md)|Chyba syntaxe: nalezen '*identifikátor* (' v globálním oboru (byl deklaraci určený?)|  