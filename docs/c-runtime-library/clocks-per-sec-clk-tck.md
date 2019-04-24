---
title: CLOCKS_PER_SEC, CLK_TCK
ms.date: 11/04/2016
f1_keywords:
- CLOCKS_PER_SEC
- CLK_TCK
helpviewer_keywords:
- CLOCKS_PER_SEC
- CLK_TCK constant
ms.assetid: bc285106-383d-44cb-91bf-276ad7de57bf
ms.openlocfilehash: eef065ac4fcedf13f3a5d54d4df0563fd04ef965
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62289972"
---
# <a name="clockspersec-clktck"></a>CLOCKS_PER_SEC, CLK_TCK

## <a name="syntax"></a>Syntaxe

```
#include <time.h>
```

## <a name="remarks"></a>Poznámky

Čas v sekundách je hodnoty vrácené `clock` funkce dělený `CLOCKS_PER_SEC`. `CLK_TCK` je ekvivalentní, ale považují za zastaralé.

## <a name="see-also"></a>Viz také:

[clock](../c-runtime-library/reference/clock.md)<br/>
[Globální konstanty](../c-runtime-library/global-constants.md)
