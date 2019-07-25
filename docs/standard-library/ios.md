---
title: '&lt;iOS&gt;'
ms.date: 11/04/2016
f1_keywords:
- <ios>
- ios/std::<ios>
helpviewer_keywords:
- ios header
ms.assetid: d3d4c161-2f37-4f04-93cc-0a2a89984a9c
ms.openlocfilehash: 96e8588e72e864d5324e406859e5a39053a46ccf
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449135"
---
# <a name="ltiosgt"></a>&lt;iOS&gt;

Definuje několik typů a funkcí základních pro provoz iostreams. Tato hlavička je obvykle zahrnutá v dalších hlavičkách iostream –. Jenom zřídka ho zahrnete přímo.

## <a name="requirements"></a>Požadavky

**Hlavička**: \<iOS >

**Obor názvů:** std

> [!NOTE]
> Knihovna \<> pro iOS `#include <iosfwd>` používá příkaz.

## <a name="remarks"></a>Poznámky

Velkou skupinou funkcí jsou manipulace s nimi. Manipulátor deklarované v \<iOS > mění hodnoty uložené v objektu argumentu třídy [ios_base](../standard-library/ios-base-class.md). Jiné manipulace provádějí akce s datovými proudy řízenými objekty typu odvozenými z této třídy, jako je například specializace jedné z tříd šablon [basic_istream](../standard-library/basic-istream-class.md) nebo [basic_ostream](../standard-library/basic-ostream-class.md). Například [noskipws](../standard-library/ios-functions.md#noskipws)(**str**) vymaže příznak `ios_base::skipws` Format v objektu `str`, který může být jednoho z těchto typů.

Můžete také volat manipulátor vložením do výstupního datového proudu nebo extrakci ze vstupního datového proudu z důvodu speciálního vkládání a extrakce operací pro třídy odvozené z `ios_base`. Příklad:

```cpp
istr>> noskipws;
```

volá [noskipws](../standard-library/ios-functions.md#noskipws)(**ISTR**).

## <a name="members"></a>Členové

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[iOS](../standard-library/ios-typedefs.md#ios)|Podporuje třídu iOS z staré knihovny iostream –.|
|[streamoff](../standard-library/ios-typedefs.md#streamoff)|Podporuje interní operace.|
|[streampos](../standard-library/ios-typedefs.md#streampos)|Obsahuje aktuální pozici ukazatele vyrovnávací paměti nebo ukazatele na soubor.|
|[streamsize](../standard-library/ios-typedefs.md#streamsize)|Určuje velikost datového proudu.|
|[wios](../standard-library/ios-typedefs.md#wios)|Podporuje třídu wios ze staré knihovny iostream –.|
|[wstreampos](../standard-library/ios-typedefs.md#wstreampos)|Obsahuje aktuální pozici ukazatele vyrovnávací paměti nebo ukazatele na soubor.|

### <a name="manipulators"></a>Manipulátory

|||
|-|-|
|[boolalpha](../standard-library/ios-functions.md#boolalpha)|Určuje, že proměnné typu [bool](../cpp/bool-cpp.md) se v datovém proudu zobrazují jako **true** nebo **false** .|
|[18.12](../standard-library/ios-functions.md#dec)|Určuje, že se celočíselné proměnné zobrazují v zápisu se základem 10.|
|[defaultfloat](../standard-library/ios-functions.md#ios_defaultfloat)|Nakonfiguruje příznaky `ios_base` objektu na použití výchozího formátu zobrazení pro hodnoty float.|
|[určí](../standard-library/ios-functions.md#fixed)|Určuje, že se v zápisu s pevným počtem desetinných míst zobrazuje číslo s plovoucí desetinnou čárkou.|
|[soustavy](../standard-library/ios-functions.md#hex)|Určuje, že se celočíselné proměnné zobrazují v zápisu se základem 16.|
|[hexfloat](../standard-library/ios-functions.md#hexfloat)|
|[internal](../standard-library/ios-functions.md#internal)|Způsobí zarovnání zarovnaného čísla na levou a číslo, které se má zarovnat vpravo.|
|[zbývá](../standard-library/ios-functions.md#left)|Způsobí, že text, který není stejně široké jako šířka výstupu, se zobrazí v vyprázdnění streamu s levým okrajem.|
|[noboolalpha](../standard-library/ios-functions.md#noboolalpha)|Určuje, že proměnné typu [bool](../cpp/bool-cpp.md) se v datovém proudu zobrazují jako 1 nebo 0.|
|[noshowbase](../standard-library/ios-functions.md#noshowbase)|Vypne označení základu zápisu, ve kterém se zobrazuje číslo.|
|[noshowpoint](../standard-library/ios-functions.md#noshowpoint)|Zobrazí pouze část čísla s plovoucí desetinnou čárkou, jejichž Zlomková část je nulová.|
|[noshowpos](../standard-library/ios-functions.md#noshowpos)|Způsobí, že kladná čísla nebudou explicitně podepsána.|
|[noskipws](../standard-library/ios-functions.md#noskipws)|Způsobí, že vstupní datový proud přečte mezery.|
|[nounitbuf](../standard-library/ios-functions.md#nounitbuf)|Způsobí, že výstup bude uložen do vyrovnávací paměti a zpracován po zaplnění vyrovnávací paměti.|
|[Velká písmena](../standard-library/ios-functions.md#nouppercase)|Určuje, že hexadecimální číslice a exponent v matematickém zápisu se zobrazí malými písmeny.|
|[mořská](../standard-library/ios-functions.md#oct)|Určuje, že se v zápisu se základem 8 vyskytují celočíselné proměnné.|
|[Kliknutím](../standard-library/ios-functions.md#right)|Způsobí, že text, který není stejně široké jako šířka výstupu, se zobrazí v vyprázdnění streamu s pravým okrajem.|
|[odbornou](../standard-library/ios-functions.md#scientific)|Způsobí, že se čísla s plovoucí desetinnou čárkou budou zobrazovat pomocí vědeckého zápisu.|
|[showbase](../standard-library/ios-functions.md#showbase)|Určuje notaci základ, ve kterém je zobrazeno číslo.|
|[showpoint](../standard-library/ios-functions.md#showpoint)|Zobrazí část čísla s plovoucí desetinnou čárkou a číslicemi vpravo od desetinné čárky, a to i v případě, že desetinná část je nula.|
|[showpos](../standard-library/ios-functions.md#showpos)|Způsobí, že kladné číslo bude explicitně podepsáno.|
|[skipws](../standard-library/ios-functions.md#skipws)|Způsobí, že vstupní datový proud nebude číst mezery.|
|[unitbuf](../standard-library/ios-functions.md#unitbuf)|Způsobí, že výstup bude zpracován, pokud není vyrovnávací paměť prázdná.|
|[všechna](../standard-library/ios-functions.md#uppercase)|Určuje, že hexadecimální číslice a exponent v matematickém zápisu se zobrazí velkými písmeny.|

### <a name="error-reporting"></a>Hlášení chyb

|||
|-|-|
|[io_errc](../standard-library/ios-functions.md#io_errc)||
|[is_error_code_enum](../standard-library/ios-functions.md#is_error_code_enum)||
|[iostream_category](../standard-library/ios-functions.md#iostream_category)||
|[make_error_code](../standard-library/ios-functions.md#make_error_code)||
|[make_error_condition](../standard-library/ios-functions.md#make_error_condition)||

### <a name="classes"></a>Třídy

|||
|-|-|
|[basic_ios](../standard-library/basic-ios-class.md)|Třída šablony popisuje funkce úložiště a členů společné pro vstupní datové proudy (ze třídy template [basic_istream](../standard-library/basic-istream-class.md)) a výstupní datové proudy (ze třídy template [basic_ostream](../standard-library/basic-ostream-class.md)), která závisí na parametrech šablony.|
|[fpos](../standard-library/fpos-class.md)|Třída šablony popisuje objekt, který může ukládat všechny informace potřebné k obnovení libovolného indikátoru pozice souboru v jakémkoli datovém proudu.|
|[ios_base](../standard-library/ios-base-class.md)|Třída popisuje funkce úložiště a členů společné pro vstupní i výstupní proudy, které nezávisí na parametrech šablony.|

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programování iostream –](../standard-library/iostream-programming.md)\
[iostreams – konvence](../standard-library/iostreams-conventions.md)
