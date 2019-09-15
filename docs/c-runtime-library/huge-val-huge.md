---
title: HUGE_VAL, _HUGE
ms.date: 11/04/2016
api_name:
- _HUGE
api_location:
- msvcrt.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _HUGE
- HUGE_VAL
helpviewer_keywords:
- _HUGE constant
- HUGE_VAL constant
- double value
ms.assetid: 3f044b45-02cd-46b2-b1de-87fd0441dd6a
ms.openlocfilehash: 3a0469b7158e765b1b1c6f34cb01c0e90beb1401
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940269"
---
# <a name="huge_val-_huge"></a>HUGE_VAL, _HUGE

## <a name="syntax"></a>Syntaxe

```
#include <math.h>
```

## <a name="remarks"></a>Poznámky

`HUGE_VAL`je největší reprezentovatelné dvojitá hodnota. Tato hodnota je vrácena řadou matematických funkcí run-time, když dojde k chybě. Pro některé funkce –`HUGE_VAL` je vráceno. `HUGE_VAL`je definován jako `_HUGE`, ale funkce run-time vrátí `HUGE_VAL`matematické funkce. Měli byste také použít `HUGE_VAL` v kódu pro konzistenci.

## <a name="see-also"></a>Viz také:

[Globální konstanty](../c-runtime-library/global-constants.md)
