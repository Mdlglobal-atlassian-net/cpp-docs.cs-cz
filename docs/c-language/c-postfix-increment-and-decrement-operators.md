---
title: Operátory jazyka C přípony Inkrementace a dekrementace | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- increment operators, syntax
- scalar operators
- types [C], scalar
ms.assetid: 56ba218d-65f9-405f-8684-caccc0ca33aa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7dc0b4c71aafe3435def0b96ae621c60ff640dc0
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43751208"
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