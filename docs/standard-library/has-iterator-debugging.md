---
title: _HAS_ITERATOR_DEBUGGING | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- _HAS_ITERATOR_DEBUGGING
dev_langs:
- C++
helpviewer_keywords:
- _HAS_ITERATOR_DEBUGGING
ms.assetid: 90077dbb-8a76-4963-83a6-29f4854007a8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ab2de61df8c4e22b1955e9fd4798b5128a3e12be
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33845892"
---
# <a name="hasiteratordebugging"></a>_HAS_ITERATOR_DEBUGGING

Nahrazeno [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md), tento makro definuje, zda je povoleno iterator ladění funkce v sestavení ladicí verze. Ve výchozím nastavení ladění iterátorů povoleno v sestavení pro ladění a zakázáno v prodejní sestavení. Další informace najdete v tématu [podpora ladění iterátorů](../standard-library/debug-iterator-support.md).

> [!IMPORTANT]
> Přímé použití `_HAS_ITERATOR_DEBUGGING` makro je zastaralý. Místo toho použijte `_ITERATOR_DEBUG_LEVEL` k řízení iterator nastavení ladění. Další informace najdete v tématu [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md).

## <a name="remarks"></a>Poznámky

Chcete-li povolit iterator ladění v sestavení pro ladění, nastavte `_ITERATOR_DEBUG_LEVEL` 2. Jde o ekvivalent `_HAS_ITERATOR_DEBUGGING` nastavení 1 nebo povoleno:

```cpp
#define _ITERATOR_DEBUG_LEVEL 2
```

`_ITERATOR_DEBUG_LEVEL` Nelze nastavit na hodnotu 2 (a `_HAS_ITERATOR_DEBUGGING` nelze nastavit na hodnotu 1) v prodejní sestavení.

Chcete-li zakázat ladění iterátory v sestavení pro ladění, nastavte `_ITERATOR_DEBUG_LEVEL` na 0 nebo 1. Jde o ekvivalent `_HAS_ITERATOR_DEBUGGING` nastavení 0 nebo vypne:

```cpp
#define _ITERATOR_DEBUG_LEVEL 0
```

## <a name="see-also"></a>Viz také

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)<br/>
[Podpora ladění iterátorů](../standard-library/debug-iterator-support.md)<br/>
[Checked – iterátory](../standard-library/checked-iterators.md)<br/>
[Bezpečné knihovny: standardní knihovna C++](../standard-library/safe-libraries-cpp-standard-library.md)<br/>
