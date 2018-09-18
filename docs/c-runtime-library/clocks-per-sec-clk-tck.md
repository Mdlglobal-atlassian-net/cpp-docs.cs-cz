---
title: CLOCKS_PER_SEC, CLK_TCK | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- CLOCKS_PER_SEC
- CLK_TCK
dev_langs:
- C++
helpviewer_keywords:
- CLOCKS_PER_SEC
- CLK_TCK constant
ms.assetid: bc285106-383d-44cb-91bf-276ad7de57bf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c3c7eac1db91abf7a84e424f7166402f346d3e4e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033573"
---
# <a name="clockspersec-clktck"></a>CLOCKS_PER_SEC, CLK_TCK

## <a name="syntax"></a>Syntaxe

```

#include <time.h>
```

## <a name="remarks"></a>Poznámky

Čas v sekundách je hodnoty vrácené `clock` funkce dělený `CLOCKS_PER_SEC`. `CLK_TCK` je ekvivalentní, ale považují za zastaralé.

## <a name="see-also"></a>Viz také

[clock](../c-runtime-library/reference/clock.md)<br/>
[Globální konstanty](../c-runtime-library/global-constants.md)