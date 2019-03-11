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
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57743170"
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
