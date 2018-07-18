---
title: _HAS_ITERATOR_DEBUGGING | Dokumentace Microsoftu
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
ms.openlocfilehash: 81f0509c6230020b586c0341e1de608981c05476
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38965975"
---
# <a name="hasiteratordebugging"></a>_HAS_ITERATOR_DEBUGGING

Nahrazeno [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md), toto makro definuje, zda je povoleno ladění funkce iterátoru v sestavení pro ladění. Ve výchozím nastavení je pro iterační ladění povoleno v sestaveních ladění a v prodejní buildy zakázáno. Další informace najdete v tématu [Debug Iterator Support](../standard-library/debug-iterator-support.md).

> [!IMPORTANT]
> Přímé použití makra _HAS_ITERATOR_DEBUGGING je zastaralé. Místo toho použijte _ITERATOR_DEBUG_LEVEL nastavení ladění ovládacích prvků iterátoru. Další informace najdete v tématu [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md).

## <a name="remarks"></a>Poznámky

Pokud chcete povolit pro iterační ladění v sestaveních ladění, nastavte _ITERATOR_DEBUG_LEVEL na 2. To je ekvivalentní nastavení _HAS_ITERATOR_DEBUGGING 1 nebo povoleno:

```cpp
#define _ITERATOR_DEBUG_LEVEL 2
```

_ITERATOR_DEBUG_LEVEL nelze nastavit na 2 (a _HAS_ITERATOR_DEBUGGING nelze nastavit na hodnotu 1) v maloobchodním prodeji sestavení.

Pokud chcete zakázat ladění iterátorů v sestavení ladění, nastavte _ITERATOR_DEBUG_LEVEL na hodnotu 0 nebo 1. To je ekvivalentní nastavení _HAS_ITERATOR_DEBUGGING 0 nebo zakázané:

```cpp
#define _ITERATOR_DEBUG_LEVEL 0
```

## <a name="see-also"></a>Viz také:

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)<br/>
[Podpora ladění iterátorů](../standard-library/debug-iterator-support.md)<br/>
[Checked – iterátory](../standard-library/checked-iterators.md)<br/>
[Bezpečné knihovny: standardní knihovna C++](../standard-library/safe-libraries-cpp-standard-library.md)<br/>
