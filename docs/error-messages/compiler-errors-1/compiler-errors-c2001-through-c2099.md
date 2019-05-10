---
title: Chyby kompilátoru C2000 až C2099
ms.date: 04/21/2019
f1_keywords:
- C2000
- C2016
- C2023
- C2024
- C2025
- C2029
- C2031
- C2035
- C2037
- C2038
- C2049
- C2068
- C2076
- C2080
- C2096
- C2098
helpviewer_keywords:
- C2000
- C2016
- C2023
- C2024
- C2025
- C2029
- C2031
- C2035
- C2037
- C2038
- C2049
- C2068
- C2076
- C2080
- C2096
- C2098
ms.assetid: d99a19eb-eeeb-4181-9b33-9cbe4459767b
ms.openlocfilehash: cf1d2f647c13b589463624749e29dc277f6f1d3e
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64857143"
---
# <a name="compiler-errors-c2000-through-c2099"></a>Chyby kompilátoru C2000 až C2099

Články v této části dokumentace vysvětlují podmnožinu chybové zprávy, které jsou generovány kompilátorem.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Chybové zprávy

|Chyba|Message|
|-----------|-------------|
|Chyba kompilátoru C2000|Neznámá chyba Zvolte prosím příkaz technická podpora v nabídce Nápověda pro Visual C++, nebo otevřete soubor nápovědy technické podpory pro další informace|
|[Chyba kompilátoru C2001](compiler-error-c2001.md)|Obsahuje znak nového řádku – konstanta|
|[Chyba kompilátoru C2002](compiler-error-c2002.md)|Neplatná konstanta širokých znaků|
|[Chyba kompilátoru C2003](compiler-error-c2003.md)|očekávané: defined id.|
|[Chyba kompilátoru C2004](compiler-error-c2004.md)|Očekávalo se: defined(id).|
|[Chyba kompilátoru C2005](compiler-error-c2005.md)|#line se očekávalo číslo řádku, nalezeno '*token*.|
|[Chyba kompilátoru C2006](compiler-error-c2006.md)|"*– direktiva*": byl očekáván název souboru, našlo se:*token*"|
|[Chyba kompilátoru C2007](compiler-error-c2007.md)|#define – syntaxe|
|[Chyba kompilátoru C2008](compiler-error-c2008.md)|"*znak*': neočekávalo se v definici makra|
|[Chyba kompilátoru C2009](compiler-error-c2009.md)|opakované použití formálního – makro "*identifikátor*.|
|[Chyba kompilátoru C2010](compiler-error-c2010.md)|"*znak*': neočekávalo se v seznamu formálních parametrů makra|
|[Chyba kompilátoru C2011](compiler-error-c2011.md)|"*identifikátor*": "*typ*" předefinování typu|
|[Chyba kompilátoru C2012](compiler-error-c2012.md)|Chybí název ' <'|
|[Chyba kompilátoru C2013](compiler-error-c2013.md)|Chybí ">"|
|[Chyba kompilátoru C2014](compiler-error-c2014.md)|příkaz preprocesoru musí spustit jako první neprázdný|
|[Chyba kompilátoru C2015](compiler-error-c2015.md)|příliš mnoho znaků – konstanta|
|Chyba kompilátoru C2016|Jazyk C vyžaduje, aby struktura nebo sjednocení měly minimálně jednoho člena|
|[Chyba kompilátoru C2017](compiler-error-c2017.md)|Neplatná řídicí sekvence|
|[Chyba kompilátoru C2018](compiler-error-c2018.md)|Neznámý znak 0 x*hodnota*.|
|[Chyba kompilátoru C2019](compiler-error-c2019.md)|Očekávaná direktiva preprocesoru, nalezeno '*znak*.|
|[Chyba kompilátoru C2020](compiler-error-c2020.md)|"*člen*": "*třídy*: předefinování členu|
|[Chyba kompilátoru C2021](compiler-error-c2021.md)|očekávala se hodnota exponent, ne "*znak*.|
|[Chyba kompilátoru C2022](compiler-error-c2022.md)|"*číslo*': moc velké pro znak|
|Chyba kompilátoru C2023|"*identifikátor*": Zarovnání (*Číslo1*) liší od předchozí deklarace (*číslo2*)|
|Chyba kompilátoru C2024|atribut "alignas" se vztahuje na proměnné, datové členy a pouze typy značek|
|Chyba kompilátoru C2025|soubor rozhraní binárního modulu neplatný nebo poškozený: "*filename*.|
|[Chyba kompilátoru C2026](compiler-error-c2026.md)|řetězec je moc velký, koncové znaky se oříznou|
|[Chyba kompilátoru C2027](compiler-error-c2027.md)|použití nedefinovaného typu "*typ*.|
|[Chyba kompilátoru C2028](compiler-error-c2028.md)|Člen struktury/sjednocení musí být uvnitř struktury/sjednocení.|
|Chyba kompilátoru C2029|Levá strana "*token*"Určuje nedefinované třídu/strukturu/rozhraní"*identifikátor*.|
|[Chyba kompilátoru C2030](compiler-error-c2030.md)|destruktor s přístupností protected private nemůže být členem třídy deklarované jako sealed.|
|Chyba kompilátoru C2031|virtuální destruktor s "*usnadnění*" pro tento typ není povolený pro usnadnění|
|[Chyba kompilátoru C2032](compiler-error-c2032.md)|"*identifikátor*': funkce nemůže být členem struktury nebo sjednocení"*typ*.|
|[Chyba kompilátoru C2033](compiler-error-c2033.md)|"*identifikátor*': bitové pole nemůže mít indirekci|
|[Chyba kompilátoru C2034](compiler-error-c2034.md)|"*identifikátor*': typ bitového pole je příliš malý počet bitů|
|Chyba kompilátoru C2035|nevirtuální destruktor s "*usnadnění*" pro tento typ není povolený pro usnadnění|
|[Chyba kompilátoru C2036](compiler-error-c2036.md)|"*identifikátor*': Neznámá velikost|
|Chyba kompilátoru C2037|Levá strana "*identifikátor*"Určuje nedefinovanou strukturu/sjednocení"*typ*.|
|Chyba kompilátoru C2038|obor názvů std nemůže být vložený.|
|[Chyba kompilátoru C2039](compiler-error-c2039.md)|"*identifier1*': není členem"*identifier2*.|
|[Chyba kompilátoru C2040](compiler-error-c2040.md)|"*operátor*": "*identifier1*"se liší úrovněmi indirekce z"*identifier2*.|
|[Chyba kompilátoru C2041](compiler-error-c2041.md)|Neplatná číslice "*znak*"pro base"*číslo*.|
|[Chyba kompilátoru C2042](compiler-error-c2042.md)|podepsané nebo nepodepsané klíčová slova vzájemně se vylučuje|
|[Chyba kompilátoru C2043](compiler-error-c2043.md)|Neplatné přerušení|
|[Chyba kompilátoru C2044](compiler-error-c2044.md)|Neplatné pokračování|
|[Chyba kompilátoru C2045](compiler-error-c2045.md)|"*identifikátor*': Předefinovaná jmenovka|
|[Chyba kompilátoru C2046](compiler-error-c2046.md)|Neplatný případ|
|[Chyba kompilátoru C2047](compiler-error-c2047.md)|Neplatné výchozí|
|[Chyba kompilátoru C2048](compiler-error-c2048.md)|více než jeden výchozí|
|Chyba kompilátoru C2049|"*identifikátor*': obor názvů nevložená nejde znovu otevřít jako vložené|
|[Chyba kompilátoru C2050](compiler-error-c2050.md)|výraz Switch není celočíselný|
|[Chyba kompilátoru C2051](compiler-error-c2051.md)|výraz Case není konstanta.|
|[Chyba kompilátoru C2052](compiler-error-c2052.md)|"*typ*': Neplatný typ pro výraz case|
|[Chyba kompilátoru C2053](compiler-error-c2053.md)|"*identifikátor*': Neshoda širokého řetězce|
|[Chyba kompilátoru C2054](compiler-error-c2054.md)|byl očekáván "(" sledovat "*identifikátor*"|
|[Chyba kompilátoru C2055](compiler-error-c2055.md)|Očekával se seznam formálních parametrů, ne seznam typů|
|[Chyba kompilátoru C2056](compiler-error-c2056.md)|Neplatný výraz|
|[Chyba kompilátoru C2057](compiler-error-c2057.md)|Očekával se konstantní výraz.|
|[Chyba kompilátoru C2058](compiler-error-c2058.md)|konstantní výraz není celočíselný|
|[Chyba kompilátoru C2059](compiler-error-c2059.md)|Chyba syntaxe: "*token*.|
|[Chyba kompilátoru C2060](compiler-error-c2060.md)|Chyba syntaxe: našel se konce souboru|
|[Chyba kompilátoru C2061](compiler-error-c2061.md)|Chyba syntaxe: identifikátor '*identifikátor*.|
|[Chyba kompilátoru C2062](compiler-error-c2062.md)|Typ '*typ*"neočekávaný|
|[Chyba kompilátoru C2063](compiler-error-c2063.md)|"*identifikátor*': není funkce|
|[Chyba kompilátoru C2064](compiler-error-c2064.md)|Termín se nevyhodnocuje na funkci pořízení *číslo* argumenty|
|[Chyba kompilátoru C2065](compiler-error-c2065.md)|"*identifikátor*': nedeklarovaný identifikátor|
|[Chyba kompilátoru C2066](compiler-error-c2066.md)|přetypování na typ funkce je neplatné.|
|[Chyba kompilátoru C2067](compiler-error-c2067.md)|přetypování na typ pole je neplatné.|
|Chyba kompilátoru C2068|Neplatné použití funkce přetížení. Chybí seznam argumentů?|
|[Chyba kompilátoru C2069](compiler-error-c2069.md)|přetypování "void" období na jinou hodnotu než 'zrušit'|
|[Chyba kompilátoru C2070](compiler-error-c2070.md)|"*typ*': Neplatný operand sizeof|
|[Chyba kompilátoru C2071](compiler-error-c2071.md)|"*identifikátor*': Neplatná třída úložiště|
|[Chyba kompilátoru C2072](compiler-error-c2072.md)|"*identifikátor*': Inicializace funkce|
|[Chyba kompilátoru C2073](compiler-error-c2073.md)|"*identifikátor*': elementy částečně inicializovaného pole musí mít výchozí konstruktor|
|[Chyba kompilátoru C2074](compiler-error-c2074.md)|"*identifikátor*": "*typ*" Inicializace vyžaduje seznam inicializátorů v závorkách|
|[Chyba kompilátoru C2075](compiler-error-c2075.md)|"*identifikátor*': inicializace pole vyžaduje seznam inicializátorů v závorkách|
|Chyba kompilátoru C2076|seznam inicializátorů v závorkách nejde používat v novém výrazu, jehož typ obsahuje "*typ*.|
|[Chyba kompilátoru C2077](compiler-error-c2077.md)|Inicializátor neskalárního pole "*identifikátor*.|
|[Chyba kompilátoru C2078](compiler-error-c2078.md)|moc velký počet inicializátorů|
|[Chyba kompilátoru C2079](compiler-error-c2079.md)|"*identifikátor*"používá nedefinovanou strukturu/třídy/sjednocení"*typ*.|
|Chyba kompilátoru C2080|"*identifikátor*': typ pro"*typ*"dá odvodit jenom z výrazu s jedním inicializátorem|
|[Chyba kompilátoru C2081](compiler-error-c2081.md)|"*identifikátor*': název v seznamu formálních parametrů je neplatný|
|[Chyba kompilátoru C2082](compiler-error-c2082.md)|Předefinování formálního parametru '*identifikátor*.|
|[Chyba kompilátoru C2083](compiler-error-c2083.md)|Neplatné porovnání struktury nebo sjednocení.|
|[Chyba kompilátoru C2084](compiler-error-c2084.md)|funkce "*identifikátor*" už má tělo.|
|[Chyba kompilátoru C2085](compiler-error-c2085.md)|"*identifikátor*': není v seznamu formálních parametrů.|
|[Chyba kompilátoru C2086](compiler-error-c2086.md)|"*identifikátor*': předefinování|
|[Chyba kompilátoru C2087](compiler-error-c2087.md)|"*identifikátor*': chybí subscript|
|[Chyba kompilátoru C2088](compiler-error-c2088.md)|"*operátor*': neplatné pro třídu/strukturu/sjednocení|
|[Chyba kompilátoru C2089](compiler-error-c2089.md)|"*identifikátor*": "*typ*" moc velká|
|[Chyba kompilátoru C2090](compiler-error-c2090.md)|funkce vrací pole.|
|[Chyba kompilátoru C2091](compiler-error-c2091.md)|funkce vrací funkci.|
|[Chyba kompilátoru C2092](compiler-error-c2092.md)|"*identifikátor*" typ elementu pole nemůže být – funkce|
|[Chyba kompilátoru C2093](compiler-error-c2093.md)|"*identifier1*': Nelze inicializovat pomocí adresy automatické proměnné '*identifier2*.|
|[Chyba kompilátoru C2094](compiler-error-c2094.md)|Popisek "*identifikátor*' nebyla definovaná|
|[Chyba kompilátoru C2095](compiler-error-c2095.md)|"*funkce*': skutečný parametr má typ void: Parametr *číslo*|
|Chyba kompilátoru C2096|"*identifikátor*": Datový člen se nedá inicializovat pomocí inicializátoru v závorkách.|
|[Chyba kompilátoru C2097](compiler-error-c2097.md)|Neplatná inicializace|
|Chyba kompilátoru C2098|Neočekávaný token po datovém členu '*identifikátor*.|
|[Chyba kompilátoru C2099](compiler-error-c2099.md)|Inicializátor není konstantní|

## <a name="see-also"></a>Viz také:

[C /C++ nástroje chyby a upozornění kompilátoru a sestavení](../compiler-errors-1/c-cpp-build-errors.md) \
[Chyby kompilátoru C2000 - C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
