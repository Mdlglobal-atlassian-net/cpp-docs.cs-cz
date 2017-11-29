---
title: "Operátory jazyka C operátory přírůstku a snížení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- increment operators, syntax
- scalar operators
- types [C], scalar
ms.assetid: 56ba218d-65f9-405f-8684-caccc0ca33aa
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6279ede332ffbcc12db4f8c72e17fe9050cc96e4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
 [Operátory přírůstku a snížení přípony: ++ a--](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)