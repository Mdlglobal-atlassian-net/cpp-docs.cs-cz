---
title: _HAS_ITERATOR_DEBUGGING
ms.date: 11/04/2016
f1_keywords:
- _HAS_ITERATOR_DEBUGGING
helpviewer_keywords:
- _HAS_ITERATOR_DEBUGGING
ms.assetid: 90077dbb-8a76-4963-83a6-29f4854007a8
ms.openlocfilehash: a1e3017ed7c6def18ce02d99dc8253b69c11ab58
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448833"
---
# <a name="hasiteratordebugging"></a>_HAS_ITERATOR_DEBUGGING

Tímto makrem nahrazeno [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md), toto makro definuje, zda je funkce ladění iterátoru v sestavení ladění povolena. Ve výchozím nastavení je ladění iterátoru povolené v sestavení ladění a zakázané v maloobchodních sestavách. Další informace najdete v tématu [Podpora pro ladění iterátorů](../standard-library/debug-iterator-support.md).

> [!IMPORTANT]
> Přímé použití makra _HAS_ITERATOR_DEBUGGING je zastaralé. Místo toho použijte _ITERATOR_DEBUG_LEVEL k řízení nastavení ladění iterátoru. Další informace najdete v tématu [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md).

## <a name="remarks"></a>Poznámky

Chcete-li povolit ladění iterátoru v sestavení ladění, nastavte _ITERATOR_DEBUG_LEVEL na 2. Jedná se o ekvivalent _HAS_ITERATOR_DEBUGGING nastavení 1 nebo povoleno:

```cpp
#define _ITERATOR_DEBUG_LEVEL 2
```

_ITERATOR_DEBUG_LEVEL nelze nastavit na hodnotu 2 (a _HAS_ITERATOR_DEBUGGING nelze nastavit na hodnotu 1) v maloobchodních sestaveních.

Chcete-li zakázat iterátory ladění v sestaveních ladění, nastavte _ITERATOR_DEBUG_LEVEL na hodnotu 0 nebo 1. To je ekvivalentní nastavení _HAS_ITERATOR_DEBUGGING 0 nebo zakázáno:

```cpp
#define _ITERATOR_DEBUG_LEVEL 0
```

## <a name="see-also"></a>Viz také:

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)\
[Podpora ladění iterátorů](../standard-library/debug-iterator-support.md)\
[Kontrolované iterátory](../standard-library/checked-iterators.md)\
[Bezpečné knihovny: Standardní knihovna C++](../standard-library/safe-libraries-cpp-standard-library.md)
