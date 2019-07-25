---
title: _SECURE_SCL
ms.date: 11/04/2016
f1_keywords:
- _SECURE_SCL
helpviewer_keywords:
- _SECURE_SCL
ms.assetid: 4ffbc788-cc12-4c6a-8cd7-490081675086
ms.openlocfilehash: 1af084363fc0d6d1723a9af7b633779f92ed2b38
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450533"
---
# <a name="securescl"></a>_SECURE_SCL

Nahrazeno [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md), toto makro definuje, zda jsou povoleny [Zaškrtnuté iterátory](../standard-library/checked-iterators.md) . Ve výchozím nastavení jsou zaškrtnuté iterátory povoleny v sestavení ladění a jsou zakázány v maloobchodních sestaveních.

> [!IMPORTANT]
> Přímé použití makra _SECURE_SCL je zastaralé. Místo toho použijte _ITERATOR_DEBUG_LEVEL k řízení kontrolovaného nastavení iterátoru. Další informace najdete v tématu [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md).

## <a name="remarks"></a>Poznámky

Pokud jsou povoleny Zaškrtnuté iterátory, nezabezpečené použití iterátoru způsobí chybu za běhu a program se ukončí. Chcete-li povolit Zaškrtnuté iterátory, nastavte _ITERATOR_DEBUG_LEVEL na 1 nebo 2. Jedná se o ekvivalent _SECURE_SCL nastavení 1 nebo povoleno:

```cpp
#define _ITERATOR_DEBUG_LEVEL 1
```

Chcete-li zakázat Zaškrtnuté iterátory, nastavte _ITERATOR_DEBUG_LEVEL na hodnotu 0. To je ekvivalentní nastavení _SECURE_SCL 0 nebo zakázáno:

```cpp
#define _ITERATOR_DEBUG_LEVEL 0
```

Informace o tom, jak zakázat upozornění na kontrolované iterátory, najdete v tématu [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md).

## <a name="see-also"></a>Viz také:

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)\
[Kontrolované iterátory](../standard-library/checked-iterators.md)\
[Podpora ladění iterátorů](../standard-library/debug-iterator-support.md)\
[Bezpečné knihovny: Standardní knihovna C++](../standard-library/safe-libraries-cpp-standard-library.md)
