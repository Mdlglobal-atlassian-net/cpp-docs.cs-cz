---
title: "Operátory jazyka C operátory přírůstku a snížení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- increment operators, syntax
- scalar operators
- types [C], scalar
ms.assetid: 56ba218d-65f9-405f-8684-caccc0ca33aa
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9fd1efe80cf5227c682a3bac47299a0daea49e1a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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