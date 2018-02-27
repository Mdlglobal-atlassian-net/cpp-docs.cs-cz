---
title: '&lt;IOS&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- <ios>
- ios/std::<ios>
dev_langs:
- C++
helpviewer_keywords:
- ios header
ms.assetid: d3d4c161-2f37-4f04-93cc-0a2a89984a9c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 76a5d6bf305e221f17b6059be3f3d770dc687000
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="ltiosgt"></a>&lt;IOS&gt;
Definuje několik typů a základní funkce pro operaci iostreams. Tuto hlavičku je obvykle zahrnuté pro můžete podle jiného iostream hlaviček; zřídka zahrnete ji přímo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#include <ios>  
  
```  
  
## <a name="remarks"></a>Poznámky  
 Velkou skupinu funkce jsou manipulátory. Manipulator deklarované v \<ios > mění hodnotami uloženými v jeho argument objekt třídy [ios_base](../standard-library/ios-base-class.md). Jiné manipulátory provádět akce na datové proudy řízené objekty typu odvozeného z této třídy, jako je například specializace jednoho tříd šablon [basic_istream](../standard-library/basic-istream-class.md) nebo [basic_ostream](../standard-library/basic-ostream-class.md). Například [noskipws](../standard-library/ios-functions.md#noskipws)(**str**) vymaže příznak formátu `ios_base::skipws` v objektu **str**, což může mít jednu z těchto typů.  
  
 Můžete také zavolat manipulator vložením do výstupního proudu nebo extrahování ze vstupního datového proudu z důvodu speciální operací vložení a extrakci zadaný pro třídy odvozené od `ios_base`. Příklad:  
  
```
istr>> noskipws;
```  
  
 volání [noskipws](../standard-library/ios-functions.md#noskipws)(**istr**).  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[IOS](../standard-library/ios-typedefs.md#ios)|Podporuje ios třída ze staré knihovny iostream.|  
|[streamoff](../standard-library/ios-typedefs.md#streamoff)|Podporuje interní operace.|  
|[streampos](../standard-library/ios-typedefs.md#streampos)|Obsahuje aktuální pozici vyrovnávací paměti ukazatele nebo ukazatele souboru.|  
|[streamsize](../standard-library/ios-typedefs.md#streamsize)|Určuje velikost datového proudu.|  
|[wios](../standard-library/ios-typedefs.md#wios)|Podporuje třídě wios ze staré knihovny iostream.|  
|[wstreampos](../standard-library/ios-typedefs.md#wstreampos)|Obsahuje aktuální pozici vyrovnávací paměti ukazatele nebo ukazatele souboru.|  
  
### <a name="manipulators"></a>Manipulátory  
  
|||  
|-|-|  
|[boolalpha](../standard-library/ios-functions.md#boolalpha)|Určuje, že proměnné typu [bool](../cpp/bool-cpp.md) zobrazí jako **true** nebo **false** v datovém proudu.|  
|[DEC](../standard-library/ios-functions.md#dec)|Určuje celé číslo proměnné, které se zobrazují v základní 10 zápisu.|  
|[defaultfloat –](../standard-library/ios-functions.md#ios_defaultfloat)|Nakonfiguruje příznaky z `ios_base` objekt, který chcete použít výchozí zobrazení formát pro hodnoty typu float.|  
|[Pevná](../standard-library/ios-functions.md#fixed)|Určuje, že číslo s plovoucí desetinnou čárkou zobrazí notaci decimal.|  
|[hex](../standard-library/ios-functions.md#hex)|Určuje celé číslo proměnné, které se zobrazují v základní 16 zápisu.|  
|[internal](../standard-library/ios-functions.md#internal)|Způsobí, že přihlášení počet zbývajících oprávněné a číslo, které má být zarovnání doprava.|  
|[left](../standard-library/ios-functions.md#left)|Způsobí, že text, který není široká jako šířka výstupu se objeví v vyprázdnění datového proudu s levým okrajem.|  
|[noboolalpha](../standard-library/ios-functions.md#noboolalpha)|Určuje, že proměnné typu [bool](../cpp/bool-cpp.md) zobrazí jako 1 nebo 0 v datovém proudu.|  
|[noshowbase](../standard-library/ios-functions.md#noshowbase)|Vypne označující konvenční základní, ve kterém se zobrazí číslo.|  
|[noshowpoint](../standard-library/ios-functions.md#noshowpoint)|Zobrazí jenom část celé číslo s plovoucí desetinnou čárkou čísel, jejichž zlomkové části je nulová.|  
|[noshowpos](../standard-library/ios-functions.md#noshowpos)|Způsobí, že nebyla výslovně podepsané kladná čísla.|  
|[noskipws](../standard-library/ios-functions.md#noskipws)|Způsobit prostory a číst vstupního datového proudu.|  
|[nounitbuf](../standard-library/ios-functions.md#nounitbuf)|Příčiny výstupní vyrovnávací paměti a zpracovat, když vyrovnávací paměť je plná.|  
|[nouppercase](../standard-library/ios-functions.md#nouppercase)|Určuje, že šestnáctkové číslice a exponent v vědecká notace se objeví na malá písmena.|  
|[OCT](../standard-library/ios-functions.md#oct)|Určuje celé číslo proměnné, které se zobrazují v základní 8 zápisu.|  
|[Vpravo](../standard-library/ios-functions.md#right)|Způsobí, že text, který není široká jako šířka výstupu se objeví v vyprázdnění datového proudu s pravým okrajem.|  
|[Scientific](../standard-library/ios-functions.md#scientific)|Příčiny plovoucí bodu čísla, který se má zobrazit pomocí exponenciální notace.|  
|[showbase](../standard-library/ios-functions.md#showbase)|Označuje konvenční základní, ve kterém se zobrazí číslo.|  
|[showpoint](../standard-library/ios-functions.md#showpoint)|Zobrazí celé číslo část číslo s plovoucí desetinnou čárkou a číslic vpravo od desetinné čárky, i v případě, že zlomkové části je nulová.|  
|[showpos](../standard-library/ios-functions.md#showpos)|Způsobí, že kladná čísla explicitně podepsat.|  
|[skipws](../standard-library/ios-functions.md#skipws)|Způsobit prostory a vstupní datový proud nelze číst.|  
|[unitbuf](../standard-library/ios-functions.md#unitbuf)|Příčiny výstupní mají být zpracovány, pokud vyrovnávací paměť není prázdný.|  
|[uppercase](../standard-library/ios-functions.md#uppercase)|Určuje, že šestnáctkové číslice a exponent v vědecká notace se objeví na velká písmena.|  
  
### <a name="classes"></a>Třídy  
  
|||  
|-|-|  
|[basic_ios](../standard-library/basic-ios-class.md)|Šablony třídy popisuje funkce úložiště a člen, které jsou společné pro obě vstupní datové proudy (šablony třídy [basic_istream](../standard-library/basic-istream-class.md)) a výstupní datové proudy (šablony třídy [basic_ostream](../standard-library/basic-ostream-class.md)), závisí na Parametry šablony.|  
|[fpos](../standard-library/fpos-class.md)|Šablony třídy popisuje objekt, který může ukládat všechny informace potřebné k obnovení indikátor libovolný pozice souboru v rámci všech datového proudu.|  
|[ios_base](../standard-library/ios-base-class.md)|Třída popisuje úložiště a členské funkce společné pro vstupní a výstupní datové proudy, které jsou nezávislé na parametry šablony.|  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)   
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream – programování](../standard-library/iostream-programming.md)   
 [iostreams – konvence](../standard-library/iostreams-conventions.md)



