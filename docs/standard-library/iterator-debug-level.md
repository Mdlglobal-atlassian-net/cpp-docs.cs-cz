---
title: _ITERATOR_DEBUG_LEVEL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- _ITERATOR_DEBUG_LEVEL
dev_langs:
- C++
helpviewer_keywords:
- _ITERATOR_DEBUG_LEVEL
ms.assetid: 718549cd-a9a9-4ab3-867b-aac00b321e67
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3b317358a00879d4430b94ea29ab547761044e56
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="iteratordebuglevel"></a>_ITERATOR_DEBUG_LEVEL

`_ITERATOR_DEBUG_LEVEL` Ovládací prvky makro zda [zaškrtnutí iterátory](../standard-library/checked-iterators.md) a [podpora ladění iterátorů](../standard-library/debug-iterator-support.md) jsou povoleny. Toto makro nahrazuje a kombinuje funkce starší `_SECURE_SCL` a `_HAS_ITERATOR_DEBUGGING` makra.

## <a name="macro-values"></a>Hodnoty – makro

Následující tabulka shrnuje možné hodnoty `_ITERATOR_DEBUG_LEVEL` makro.

|Režim kompilace|Hodnota – makro|Popis|
|----------------------|----------------|-----------------|
|**Ladění**|||
||0|Zakáže checked – iterátory a zakáže iterační ladění.|
||1|Checked – iterátory povolí nebo zakáže iterační ladění.|
||2 (výchozí)|Umožňuje iterační ladění. checked – iterátory nejsou důležité.|
|**Vydaná verze**|||
||0 (výchozí)|Iterátory zakáže zaškrtnutí.|
||1|Umožňuje zkontrolovat iterátory; iterator ladění není relevantní.|

V režimu vydání, kompilátor vygeneruje chybu, pokud zadáte `_ITERATOR_DEBUG_LEVEL` jako 2.

## <a name="remarks"></a>Poznámky

`_ITERATOR_DEBUG_LEVEL` Ovládací prvky makro zda [zaškrtnutí iterátory](../standard-library/checked-iterators.md) jsou povolené a v režimu ladění, ať už [podpora ladění iterátorů](../standard-library/debug-iterator-support.md) je povoleno. Pokud `_ITERATOR_DEBUG_LEVEL` je definován jako 1 nebo 2, checked – iterátory Ujistěte se, že se nepřepíšou hranice kontejnerů. Pokud `_ITERATOR_DEBUG_LEVEL` je 0, iterátory nejsou zaškrtnutí. Když `_ITERATOR_DEBUG_LEVEL` je definován jako 1, všechny příčiny použití unsafe iterator běhová chyba a program je ukončen. Když `_ITERATOR_DEBUG_LEVEL` je definován jako 2, použijte příčiny unsafe iterator assert a runtime chybový dialog, který vám umožní rozdělit ladicího programu.

Protože `_ITERATOR_DEBUG_LEVEL` makro podporuje podobné funkce jako `_SECURE_SCL` a `_HAS_ITERATOR_DEBUGGING` makra, můžete být jisti, které makra a makra hodnoty pro použití v konkrétních situacích. Pokud chcete zabránit nejasnostem, doporučujeme používat jenom `_ITERATOR_DEBUG_LEVEL` makro. Tato tabulka popisuje ekvivalent `_ITERATOR_DEBUG_LEVEL` makro hodnotu, která se použije pro různé hodnoty `_SECURE_SCL` a `_HAS_ITERATOR_DEBUGGING` v existujícím kódu.

|**_ITERATOR_DEBUG_LEVEL** |**_SECURE_SCL** |**_HAS_ITERATOR_DEBUGGING**|
|---|---|---|
|0 (výchozí verze)|0 (zakázáno)|0 (zakázáno)|
|1|1 (povoleno)|0 (zakázáno)|
|2 (výchozí ladění)|(není relevantní)|1 (povoleno v režimu ladění)|

Informace o tom, jak zakázat upozornění o checked – iterátory najdete v tématu [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md).

### <a name="example"></a>Příklad

Můžete zadat hodnotu pro `_ITERATOR_DEBUG_LEVEL` makro, použití [/D](../build/reference/d-preprocessor-definitions.md) – možnost kompilátoru zadejte na příkazovém řádku nebo použijte `#define` před standardní knihovna C++ jsou obsažena ve zdrojových souborech. Například na příkazovém řádku, zkompilovat *sample.cpp* v režimu ladění a použít – podpora ladění iterátorů, můžete zadat `_ITERATOR_DEBUG_LEVEL` definici makra:

`cl /EHsc /Zi /MDd /D_ITERATOR_DEBUG_LEVEL=1 sample.cpp`

Ve zdrojovém souboru zadejte makro před všechny standardní knihovna hlavičky, které definují iterátory.

```cpp
// sample.cpp

#define _ITERATOR_DEBUG_LEVEL 1

#include <vector>

// ...
```

## <a name="see-also"></a>Viz také

[Checked – iterátory](../standard-library/checked-iterators.md)<br/>
[Podpora ladění iterátorů](../standard-library/debug-iterator-support.md)<br/>
[Bezpečné knihovny: standardní knihovna C++](../standard-library/safe-libraries-cpp-standard-library.md)<br/>
