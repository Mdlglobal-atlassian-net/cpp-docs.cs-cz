---
title: Konstanty jazyka _locking
ms.date: 11/04/2016
f1_keywords:
- _LK_RLCK
- _LK_NBLCK
- _LK_LOCK
- _LK_NBRLCK
- _LK_UNLCK
helpviewer_keywords:
- LK_UNLCK constant
- LK_NBRLCK constant
- _LK_NBRLCK constant
- _LK_NBLCK constant
- _LK_LOCK constant
- LK_NBLCK constant
- _LK_UNLCK constant
- LK_RLCK constant
- _LK_RLCK constant
- LK_LOCK constant
ms.assetid: c3dc92c8-60e3-4d29-9f50-5d217627c8ad
ms.openlocfilehash: d559a68e8fede6e0b6dd40505a041b14da703681
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57738487"
---
# <a name="locking-constants"></a>Konstanty jazyka _locking

## <a name="syntax"></a>Syntaxe

```
#include <sys/locking.h>
```

## <a name="remarks"></a>Poznámky

*Režimu* argument ve volání `_locking` určuje funkce zamykání akce má být provedena.

*Režimu* argument musí být jedna z následujících konstant manifestu.

|||
|-|-|
| `_LK_LOCK`  | Zamkne zadaný počet bajtů. Pokud počet bajtů nemůže být uzamčen, funkce se pokusí znovu za 1 sekundu. Pokud po 10 pokusech, nelze uzamknout počet bajtů, funkce vrátí chybu.  |
| `_LK_RLCK`  | Stejné jako `_LK_LOCK`.  |
|`_LK_NBLCK`  | Zamkne zadaný počet bajtů. Pokud nelze uzamknout bajtů, funkce vrátí chybu.  |
| `_LK_NBRLCK`  | Stejné jako `_LK_NBLCK`.  |
| `_LK_UNLCK`  | Odemkne zadaný počet bajtů. (Počet bajtů musí být dříve uzamčeny.)  |

## <a name="see-also"></a>Viz také:

[_locking](../c-runtime-library/reference/locking.md)<br/>
[Globální konstanty](../c-runtime-library/global-constants.md)
