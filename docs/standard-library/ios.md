---
title: '&lt;IOS&gt;'
ms.date: 11/04/2016
f1_keywords:
- <ios>
- ios/std::<ios>
helpviewer_keywords:
- ios header
ms.assetid: d3d4c161-2f37-4f04-93cc-0a2a89984a9c
ms.openlocfilehash: 1566f9105a61b1c037e86fd2e4b280ed6dd2020e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385216"
---
# <a name="ltiosgt"></a>&lt;IOS&gt;

Definuje několik typů a základní funkce pro operace iostreams. Tato hlavička se obvykle zahrnuté pro vás pomocí jiné záhlaví iostream –; zřídka zahrnete ji přímo.

## <a name="syntax"></a>Syntaxe

```cpp
#include <ios>
```

## <a name="remarks"></a>Poznámky

Velká skupina funkcí jsou manipulátory. Manipulátor deklarované v \<ios > změní hodnoty uložené v její argument objekt třídy [ios_base –](../standard-library/ios-base-class.md). Jiné manipulátory provádění akcí u streamů řídí objekty typu odvozeného z této třídy, jako je například specializace jednu z tříd šablon [basic_istream](../standard-library/basic-istream-class.md) nebo [basic_ostream –](../standard-library/basic-ostream-class.md). Například [noskipws](../standard-library/ios-functions.md#noskipws)(**str**) příznak formátu `ios_base::skipws` v objektu `str`, což může být jedna z těchto typů.

Můžete také volat manipulátor vložením do výstupní datový proud nebo extrahování ze vstupního datového proudu, protože speciální operace vložení a extrakci zadaný pro třídy odvozené z `ios_base`. Příklad:

```cpp
istr>> noskipws;
```

volání [noskipws](../standard-library/ios-functions.md#noskipws)(**istr**).

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[IOS](../standard-library/ios-typedefs.md#ios)|Podporuje ios třídy z původní Knihovna iostream.|
|[streamoff](../standard-library/ios-typedefs.md#streamoff)|Podporuje vnitřní operace.|
|[streampos](../standard-library/ios-typedefs.md#streampos)|Obsahuje aktuální pozici ukazatele vyrovnávací paměti nebo ukazatel na soubor.|
|[streamsize](../standard-library/ios-typedefs.md#streamsize)|Určuje velikost datového proudu.|
|[wios](../standard-library/ios-typedefs.md#wios)|Podporuje wios třídy z původní Knihovna iostream.|
|[wstreampos](../standard-library/ios-typedefs.md#wstreampos)|Obsahuje aktuální pozici ukazatele vyrovnávací paměti nebo ukazatel na soubor.|

### <a name="manipulators"></a>Manipulátory

|||
|-|-|
|[boolalpha](../standard-library/ios-functions.md#boolalpha)|Určuje proměnné tohoto typu [bool](../cpp/bool-cpp.md) zobrazí jako **true** nebo **false** v datovém proudu.|
|[DEC](../standard-library/ios-functions.md#dec)|Určuje, že celočíselné proměnné zobrazí v základní 10 zápisu.|
|[defaultfloat](../standard-library/ios-functions.md#ios_defaultfloat)|Nakonfiguruje příznaky ze `ios_base` objektu, který chcete použít výchozí zobrazovací formát pro hodnoty typu float.|
|[Oprava](../standard-library/ios-functions.md#fixed)|Určuje, že číslo s plovoucí desetinnou čárkou se zobrazí v oprava desítkovém zápisu.|
|[Hex](../standard-library/ios-functions.md#hex)|Určuje, že celočíselné proměnné zobrazí v základní 16 zápisu.|
|[internal](../standard-library/ios-functions.md#internal)|Způsobí, že se znaménkem číslo vlevo oprávněné a číslo, které má být zarovnané vpravo.|
|[doleva](../standard-library/ios-functions.md#left)|Způsobí, že text, který není stejně široká jako šířka výstupu se zobrazí v stream vyprázdnění se na levém okraji.|
|[noboolalpha](../standard-library/ios-functions.md#noboolalpha)|Určuje, že proměnné typu [bool](../cpp/bool-cpp.md) jako 1 nebo 0 v datovém proudu.|
|[noshowbase](../standard-library/ios-functions.md#noshowbase)|Vypne označující konvenční základní třídy, ve kterém se zobrazí číslo.|
|[noshowpoint](../standard-library/ios-functions.md#noshowpoint)|Zobrazí pouze část celého čísla s plovoucí desetinnou čárkou čísel, jehož zlomkové části je nula.|
|[noshowpos](../standard-library/ios-functions.md#noshowpos)|Způsobí, že kladná čísla nesmí být explicitně přihlášení.|
|[noskipws](../standard-library/ios-functions.md#noskipws)|Způsobit prostory přečtou vstupní datový proud.|
|[nounitbuf](../standard-library/ios-functions.md#nounitbuf)|Způsobí, že výstupní vyrovnávací paměť a zpracovávaná vyrovnávací paměť je plná.|
|[nouppercase](../standard-library/ios-functions.md#nouppercase)|Určuje, že šestnáctkových číslic a exponent za použití vědeckého zápisu se zobrazí na malá písmena.|
|[Říjen](../standard-library/ios-functions.md#oct)|Určuje, že celočíselné proměnné zobrazí v základní 8 zápisu.|
|[doprava](../standard-library/ios-functions.md#right)|Způsobí, že text, který není stejně široká jako šířka výstupu se zobrazí v vyprázdnění datový proud s na pravém okraji.|
|[scientific](../standard-library/ios-functions.md#scientific)|Způsobí, že plovoucí desetinnou čárkou zobrazeného pomocí vědeckého zápisu.|
|[showbase](../standard-library/ios-functions.md#showbase)|Označuje konvenční základní třídy, ve kterém se zobrazí číslo.|
|[showpoint](../standard-library/ios-functions.md#showpoint)|Zobrazuje část celého čísla číslo s plovoucí desetinnou čárkou a číslic vpravo od desetinné čárky, i v případě, že zlomkové části je nula.|
|[showpos](../standard-library/ios-functions.md#showpos)|Způsobí, že explicitně podepsat kladná čísla.|
|[skipws](../standard-library/ios-functions.md#skipws)|Způsobit prostory vstupního datového proudu nelze číst.|
|[unitbuf](../standard-library/ios-functions.md#unitbuf)|Způsobí, že výstupní ke zpracování, pokud vyrovnávací paměť není prázdný.|
|[velká písmena](../standard-library/ios-functions.md#uppercase)|Určuje, že šestnáctkových číslic a exponent za použití vědeckého zápisu se zobrazí na velká písmena.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[basic_ios](../standard-library/basic-ios-class.md)|Třída šablony popisuje funkce úložiště a člena, které jsou společné pro oba vstupní datové proudy (třídy šablony [basic_istream](../standard-library/basic-istream-class.md)) tak za výstupní datové proudy (třídy šablony [basic_ostream –](../standard-library/basic-ostream-class.md)), který závisí na Parametry šablony.|
|[fpos –](../standard-library/fpos-class.md)|Třída šablony popisuje objekt, který můžete uložit všechny informace potřebné k obnovení Indikátor pozice souboru v libovolné v rámci jakékoli služby stream.|
|[ios_base](../standard-library/ios-base-class.md)|Tato třída popisuje úložiště a členské funkce společné pro vstupní a výstupní datové proudy, které nezávisí na parametry šablony.|

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream – programování](../standard-library/iostream-programming.md)<br/>
[iostreams – konvence](../standard-library/iostreams-conventions.md)<br/>
