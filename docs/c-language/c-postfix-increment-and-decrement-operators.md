---
title: Operátory jazyka C operátory přírůstku a snížení | Microsoft Docs
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
ms.openlocfilehash: 8f96c48a69f692c8646de5dec8ad8e6431fb63c5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="c-postfix-increment-and-decrement-operators"></a>Operátory přírůstku a snížení přípony jazyka C
Zvýšit operandy operátory a operátory snížení jsou Skalární typy, které jsou upravitelnými hodnoty l.  
  
## <a name="syntax"></a>Syntaxe  
 *operátory výraz*:  
 *operátory – výraz*  **++**  
  
 *operátory – výraz*  **--**  
  
 Výsledek operátory přírůstek nebo snížení operaci je hodnota operand. Po získání výsledek operand hodnotu zvýšena (nebo odečte). Následující kód ukazuje operátor přírůstku operátory.  
  
```  
if( var++ > 0 )  
    *p++ = *q++;  
```  
  
 V tomto příkladu proměnná `var` se ve srovnání s 0, pak je zvýší. Pokud `var` byl kladné před se zvýší, je-li provést další příkaz. Nejprve hodnota objektu, na kterou odkazuje `q` je přiřazen k objektu, na kterou odkazuje `p`. Potom `q` a `p` se zvýší.  
  
## <a name="see-also"></a>Viz také  
 [Operátory přírůstku a snížení přípony: ++ a --](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)