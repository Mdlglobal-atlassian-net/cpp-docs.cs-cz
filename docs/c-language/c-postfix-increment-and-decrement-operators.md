---
title: Operátory přírůstku a snížení přípony jazyka C
ms.date: 11/04/2016
helpviewer_keywords:
- increment operators, syntax
- scalar operators
- types [C], scalar
ms.assetid: 56ba218d-65f9-405f-8684-caccc0ca33aa
ms.openlocfilehash: 8c2e3ba50ce3e768b377a588cd3e82ad29df79ee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325572"
---
# <a name="c-postfix-increment-and-decrement-operators"></a>Operátory přírůstku a snížení přípony jazyka C

Operandy Příponové přírůstek a snížení operátory jsou Skalární typy, které jsou upravitelné l hodnoty.

## <a name="syntax"></a>Syntaxe

*postfix-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **++**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **--**

Výsledek přípony zvýšení nebo snížení operace je hodnota operandu. Po získání výsledku, hodnota operandu je zvýšena (nebo snížen). Následující kód znázorňuje příponový operátor Inkrementace.

```
if( var++ > 0 )
    *p++ = *q++;
```

V tomto příkladu je proměnná `var` má v porovnání s 0, bude zvýšen. Pokud `var` byl pozitivní před se zvýší, dalšího příkazu. Nejprve hodnotu objektu, na které odkazuje `q` je přiřazena k objektu, na které odkazuje `p`. Potom `q` a `p` jsou zvětšeny.

## <a name="see-also"></a>Viz také:

[Operátory přírůstku a snížení přípony: ++ a --](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)
