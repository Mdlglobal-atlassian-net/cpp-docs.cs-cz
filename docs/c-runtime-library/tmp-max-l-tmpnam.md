---
title: TMP_MAX, L_tmpnam
ms.date: 11/04/2016
f1_keywords:
- TMP_MAX
- L_tmpnam
helpviewer_keywords:
- temporary files, length
- L_tmpnam constant
- TMP_MAX constant
ms.assetid: ab19fd0c-b5b7-49f7-b23d-da9dfbcf0c1f
ms.openlocfilehash: 21b56a05b60067e04d0d3864a135ed5eccacfddc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50609713"
---
# <a name="tmpmax-ltmpnam"></a>TMP_MAX, L_tmpnam

## <a name="syntax"></a>Syntaxe

```
#include <stdio.h>
```

## <a name="remarks"></a>Poznámky

`TMP_MAX` je maximální počet jedinečných názvů souborů, které `tmpnam` funkce můžete vygenerovat. `L_tmpnam` je délka dočasné názvy souborů generovaných `tmpnam`.

## <a name="see-also"></a>Viz také

[Globální konstanty](../c-runtime-library/global-constants.md)