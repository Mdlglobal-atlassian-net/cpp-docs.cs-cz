---
title: Operátory přírůstku a snížení přípony jazyka C
ms.date: 11/04/2016
helpviewer_keywords:
- increment operators, syntax
- scalar operators
- types [C], scalar
ms.assetid: 56ba218d-65f9-405f-8684-caccc0ca33aa
ms.openlocfilehash: 8d45ce34457779e668124d9f48b82a5b74da1c56
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50506842"
---
# <a name="c-postfix-increment-and-decrement-operators"></a>Operátory přírůstku a snížení přípony jazyka C

Operandy Příponové přírůstek a snížení operátory jsou Skalární typy, které jsou upravitelné l hodnoty.

## <a name="syntax"></a>Syntaxe

*výraz přípony*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony*  **++**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony*  **--**

Výsledek přípony zvýšení nebo snížení operace je hodnota operandu. Po získání výsledku, hodnota operandu je zvýšena (nebo snížen). Následující kód znázorňuje příponový operátor Inkrementace.

```
if( var++ > 0 )
    *p++ = *q++;
```

V tomto příkladu je proměnná `var` má v porovnání s 0, bude zvýšen. Pokud `var` byl pozitivní před se zvýší, dalšího příkazu. Nejprve hodnotu objektu, na které odkazuje `q` je přiřazena k objektu, na které odkazuje `p`. Potom `q` a `p` jsou zvětšeny.

## <a name="see-also"></a>Viz také

[Operátory přírůstku a snížení přípony: ++ a --](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)