---
title: HUGE_VAL, _HUGE
ms.date: 11/04/2016
apiname:
- _HUGE
apilocation:
- msvcrt.dll
apitype: DLLExport
f1_keywords:
- _HUGE
- HUGE_VAL
helpviewer_keywords:
- _HUGE constant
- HUGE_VAL constant
- double value
ms.assetid: 3f044b45-02cd-46b2-b1de-87fd0441dd6a
ms.openlocfilehash: e6e3ec4c59ad22510233289d901fd3a89cb0d257
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62289816"
---
# <a name="hugeval-huge"></a>HUGE_VAL, _HUGE

## <a name="syntax"></a>Syntaxe

```
#include <math.h>
```

## <a name="remarks"></a>Poznámky

`HUGE_VAL` je největší reprezentovatelné dvojitou hodnotu. Mnoho za běhu matematické funkce vrátí tuto hodnotu při výskytu chyby. Pro některé funkce-`HUGE_VAL` je vrácena. `HUGE_VAL` je definován jako `_HUGE`, ale za běhu matematické funkce vrátit `HUGE_VAL`. Také byste měli použít `HUGE_VAL` ve vašem kódu pro zajištění konzistence.

## <a name="see-also"></a>Viz také:

[Globální konstanty](../c-runtime-library/global-constants.md)
