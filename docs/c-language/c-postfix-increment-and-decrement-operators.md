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

Operandy operátorů přírůstku a snížení přípon jsou skalární typy, které lze upravovat jako hodnoty l.

## <a name="syntax"></a>Syntaxe

*výraz přípony*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony*  **++**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony*  **--**

Výsledkem operace zvýšení nebo snížení přípony je hodnota operandu. Po získání výsledku je hodnota operandu zvýšena (nebo snížena). Následující kód ilustruje operátor přírůstku přípony.

```
if( var++ > 0 )
    *p++ = *q++;
```

V tomto příkladu je proměnná `var` porovnána s 0 a pak zvýšena. Pokud `var` bylo před zvýšením kladné, je proveden další příkaz. Nejprve hodnota objektu, na kterou `q` ukazuje, je přiřazena objektu, na který odkazuje. `p` `q` Pak `p` se zvýší.

## <a name="see-also"></a>Viz také

[Operátory přírůstku a snížení přípony: + + a--](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)
