---
title: _ITERATOR_DEBUG_LEVEL
ms.date: 11/04/2016
f1_keywords:
- _ITERATOR_DEBUG_LEVEL
helpviewer_keywords:
- _ITERATOR_DEBUG_LEVEL
ms.assetid: 718549cd-a9a9-4ab3-867b-aac00b321e67
ms.openlocfilehash: 7b573127518969accdfdcc4a25a50269dd6aa002
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456392"
---
# <a name="iteratordebuglevel"></a>_ITERATOR_DEBUG_LEVEL

Makro _ITERATOR_DEBUG_LEVEL určuje, zda [](../standard-library/checked-iterators.md) jsou povoleny Zaškrtnuté iterátory a [Podpora iterátoru ladění](../standard-library/debug-iterator-support.md) . Toto makro nahrazuje a kombinuje funkce starších maker _SECURE_SCL a _HAS_ITERATOR_DEBUGGING.

## <a name="macro-values"></a>Hodnoty maker

Následující tabulka shrnuje možné hodnoty pro _ITERATOR_DEBUG_LEVEL makro.

|Režim kompilace|Hodnota makra|Popis|
|----------------------|----------------|-----------------|
|**Ladění**|||
||0|Zakáže kontrolované iterátory a zakáže ladění iterátoru.|
||1|Povoluje kontrolované iterátory a zakáže ladění iterátoru.|
||2 (výchozí)|Povolí ladění iterátoru; kontrolované iterátory nejsou relevantní.|
|**Vydaná verze**|||
||0 (výchozí)|Zakáže kontrolované iterátory.|
||1|Povoluje kontrolované iterátory; ladění iterátoru není relevantní.|

V režimu vydání kompilátor vygeneruje chybu, pokud zadáte _ITERATOR_DEBUG_LEVEL jako 2.

## <a name="remarks"></a>Poznámky

Makro _ITERATOR_DEBUG_LEVEL řídí, zda jsou povoleny [kontrolované iterátory](../standard-library/checked-iterators.md) a v režimu ladění, zda je povolena [Podpora iterátoru ladění](../standard-library/debug-iterator-support.md) . Pokud je _ITERATOR_DEBUG_LEVEL definováno jako 1 nebo 2, kontrolované iterátory zajistí, že hranice vašich kontejnerů nebudou přepsány. Pokud je _ITERATOR_DEBUG_LEVEL 0, iterátory nejsou zaškrtnuté. Pokud je _ITERATOR_DEBUG_LEVEL definováno jako 1, nezabezpečené použití iterátoru způsobí chybu za běhu a program se ukončí. Když je _ITERATOR_DEBUG_LEVEL definováno jako 2, nezabezpečené použití iterátoru způsobí vyhodnocení a běhový chybový dialog, který umožňuje přerušit ladicí program.

Vzhledem k tomu, že makro _ITERATOR_DEBUG_LEVEL podporuje podobnou funkci pro makra _SECURE_SCL a _HAS_ITERATOR_DEBUGGING, možná nebudete chtít, aby makro a hodnota makra používaly v konkrétní situaci. Chcete-li zabránit nejasnostem, doporučujeme použít pouze makro _ITERATOR_DEBUG_LEVEL. Tato tabulka popisuje ekvivalentní hodnotu makra _ITERATOR_DEBUG_LEVEL, která se má použít pro různé hodnoty _SECURE_SCL a _HAS_ITERATOR_DEBUGGING v existujícím kódu.

|**_ITERATOR_DEBUG_LEVEL** |**_SECURE_SCL** |**_HAS_ITERATOR_DEBUGGING**|
|---|---|---|
|0 (výchozí verze)|0 (zakázáno)|0 (zakázáno)|
|1|1 (povoleno)|0 (zakázáno)|
|2 (výchozí ladění)|(není relevantní)|1 (povoleno v režimu ladění)|

Informace o tom, jak zakázat upozornění na kontrolované iterátory, najdete v tématu [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md).

### <a name="example"></a>Příklad

Chcete-li zadat hodnotu pro makro _ITERATOR_DEBUG_LEVEL, použijte možnost [/d](../build/reference/d-preprocessor-definitions.md) Compiler k jejímu definování na příkazovém řádku, nebo použijte `#define` před zahrnutím C++ standardních hlaviček knihoven do zdrojových souborů. Například na příkazovém řádku pro zkompilování *Sample. cpp* v režimu ladění a použití podpory ladění iterátorů můžete zadat definici makra _ITERATOR_DEBUG_LEVEL:

`cl /EHsc /Zi /MDd /D_ITERATOR_DEBUG_LEVEL=1 sample.cpp`

Ve zdrojovém souboru určete makro před všemi standardními hlavičkami knihovny, které definují iterátory.

```cpp
// sample.cpp

#define _ITERATOR_DEBUG_LEVEL 1

#include <vector>

// ...
```

## <a name="see-also"></a>Viz také:

[Kontrolované iterátory](../standard-library/checked-iterators.md)\
[Podpora ladění iterátorů](../standard-library/debug-iterator-support.md)\
[Bezpečné knihovny: Standardní knihovna C++](../standard-library/safe-libraries-cpp-standard-library.md)
