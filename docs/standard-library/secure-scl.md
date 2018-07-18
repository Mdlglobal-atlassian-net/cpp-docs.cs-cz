---
title: _SECURE_SCL | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- _SECURE_SCL
dev_langs:
- C++
helpviewer_keywords:
- _SECURE_SCL
ms.assetid: 4ffbc788-cc12-4c6a-8cd7-490081675086
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f6a9fa05a4cb8c421a511a30fd62310d69003fde
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38966430"
---
# <a name="securescl"></a>_SECURE_SCL

Nahrazeno [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md), tato makra definuje, jestli [Checked Iterators](../standard-library/checked-iterators.md) jsou povolené. Ve výchozím nastavení jsou kontrolované iterátory povoleno v sestaveních ladění a v prodejní buildy zakázáno.

> [!IMPORTANT]
> Přímé použití makra _SECURE_SCL je zastaralé. Místo toho použijte _ITERATOR_DEBUG_LEVEL nastavení iterátoru zaškrtnutí ovládacího prvku. Další informace najdete v tématu [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md).

## <a name="remarks"></a>Poznámky

Při checked – iterátory jsou povolené, nebezpečné používání iterátorů způsobí chybu modulu runtime a program se ukončí. Pokud chcete povolit kontrolované iterátory, nastavte _ITERATOR_DEBUG_LEVEL na 1 nebo 2. To je ekvivalentní nastavení _SECURE_SCL 1 nebo povoleno:

```cpp
#define _ITERATOR_DEBUG_LEVEL 1
```

Pokud chcete zakázat kontrolované iterátory, nastavit _ITERATOR_DEBUG_LEVEL na hodnotu 0. To je ekvivalentní nastavení _SECURE_SCL 0 nebo zakázané:

```cpp
#define _ITERATOR_DEBUG_LEVEL 0
```

Informace o tom, jak zakázat varování o kontrolovaných iterátorech naleznete v tématu [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md).

## <a name="see-also"></a>Viz také:

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)<br/>
[Checked – iterátory](../standard-library/checked-iterators.md)<br/>
[Podpora ladění iterátorů](../standard-library/debug-iterator-support.md)<br/>
[Bezpečné knihovny: standardní knihovna C++](../standard-library/safe-libraries-cpp-standard-library.md)<br/>
