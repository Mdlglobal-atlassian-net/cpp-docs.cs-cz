---
title: _ITERATOR_DEBUG_LEVEL | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- _ITERATOR_DEBUG_LEVEL
dev_langs:
- C++
helpviewer_keywords:
- _ITERATOR_DEBUG_LEVEL
ms.assetid: 718549cd-a9a9-4ab3-867b-aac00b321e67
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4163542d0ba741e6f0a123cbdcdc44dbbec470d1
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38957788"
---
# <a name="iteratordebuglevel"></a>_ITERATOR_DEBUG_LEVEL

Ovládací prvky makru _ITERATOR_DEBUG_LEVEL, zda [checked iterators](../standard-library/checked-iterators.md) a [podpora ladění iterátorů](../standard-library/debug-iterator-support.md) jsou povolené. Toto makro nahrazuje a kombinuje funkci starší _SECURE_SCL a _HAS_ITERATOR_DEBUGGING makra.

## <a name="macro-values"></a>Hodnoty – makro

Následující tabulka shrnuje možných hodnot pro makru _ITERATOR_DEBUG_LEVEL.

|Režim kompilace|Hodnota – makro|Popis|
|----------------------|----------------|-----------------|
|**Ladění**|||
||0|Zakáže kontrolované iterátory a zakáže pro iterační ladění.|
||1|Checked – iterátory povolí nebo zakáže pro iterační ladění.|
||2 (výchozí)|Umožňuje pro iterační ladění; checked – iterátory nejsou relevantní.|
|**Vydaná verze**|||
||0 (výchozí)|Zakáže kontroluje iterátory.|
||1|Umožňuje zkontrolovat iterátory; iterační ladění není relevantní.|

V režimu vydání kompilátor vygeneruje chybu, pokud zadáte _ITERATOR_DEBUG_LEVEL jako 2.

## <a name="remarks"></a>Poznámky

Ovládací prvky makru _ITERATOR_DEBUG_LEVEL, zda [checked iterators](../standard-library/checked-iterators.md) jsou povolené a v režimu ladění, ať už [podpora ladění iterátorů](../standard-library/debug-iterator-support.md) je povolená. Pokud _ITERATOR_DEBUG_LEVEL je definováno jako 1 nebo 2, kontrolované iterátory zajistí, že se nepřepíšou hranice vaše kontejnery. Pokud _ITERATOR_DEBUG_LEVEL je 0, nebudou kontrolovány iterátory. Při _ITERATOR_DEBUG_LEVEL je definováno jako 1, nebezpečné iterátoru použitím způsobí chybu modulu runtime a program se ukončí. Při _ITERATOR_DEBUG_LEVEL je definován jako 2, použít nezabezpečený iterátoru příčiny, které assert a dialogové okno chyby modulu runtime, která vám umožní proniknout do ladicího programu.

Makru _ITERATOR_DEBUG_LEVEL podporuje podobné funkce jako makra _SECURE_SCL a _HAS_ITERATOR_DEBUGGING, vám může být jisti které makra a makra hodnoty pro použití v konkrétních situacích. Pokud chcete zabránit nejasnostem, doporučujeme používat pouze makru _ITERATOR_DEBUG_LEVEL. Tato tabulka popisuje hodnotu makra ekvivalentní _ITERATOR_DEBUG_LEVEL pro různé hodnoty _SECURE_SCL a _HAS_ITERATOR_DEBUGGING v existujícím kódu.

|**_ITERATOR_DEBUG_LEVEL** |**_SECURE_SCL** |**_HAS_ITERATOR_DEBUGGING**|
|---|---|---|
|0 (výchozí verze)|0 (zakázáno)|0 (zakázáno)|
|1|1 (povoleno)|0 (zakázáno)|
|2 (výchozí nastavení ladění)|(není potřeba)|1 (Povolit v režimu ladění)|

Informace o tom, jak zakázat varování o kontrolovaných iterátorech naleznete v tématu [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md).

### <a name="example"></a>Příklad

Chcete-li zadat hodnotu makru _ITERATOR_DEBUG_LEVEL, použijte [/D](../build/reference/d-preprocessor-definitions.md) – možnost kompilátoru definujte ho v příkazovém řádku, nebo použít `#define` před standardní knihovny C++ jsou obsažena ve zdrojových souborech. Například na příkazovém řádku, chcete-li zkompilovat *sample.cpp* v režimu ladění a používat iterátor podporu ladění, můžete zadat _ITERATOR_DEBUG_LEVEL definice makra:

`cl /EHsc /Zi /MDd /D_ITERATOR_DEBUG_LEVEL=1 sample.cpp`

Ve zdrojovém souboru zadejte – makro před záhlaví standardní knihovny, které definují iterátory.

```cpp
// sample.cpp

#define _ITERATOR_DEBUG_LEVEL 1

#include <vector>

// ...
```

## <a name="see-also"></a>Viz také:

[Checked – iterátory](../standard-library/checked-iterators.md)<br/>
[Podpora ladění iterátorů](../standard-library/debug-iterator-support.md)<br/>
[Bezpečné knihovny: standardní knihovna C++](../standard-library/safe-libraries-cpp-standard-library.md)<br/>
