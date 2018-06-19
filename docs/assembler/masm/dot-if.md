---
title: . POKUD | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .IF
dev_langs:
- C++
helpviewer_keywords:
- .IF directive
ms.assetid: dccc7615-8fc7-4829-9f39-0ee405f6c1e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7ab0e2fc510b4be8c5a9a8c0c3d0fb1c4347f0b9
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
ms.locfileid: "32053113"
---
# <a name="if"></a>.IF
Generuje kód, který testuje `condition1` (například AX > 7) a spustí *příkazy* při splnění této podmínky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
   .IF condition1   
statements  
[[.ELSEIF condition2   
   statements]]  
[[.ELSE  
   statements]]  
.ENDIF  
```  
  
## <a name="remarks"></a>Poznámky  
 Pokud [. ELSE](../../assembler/masm/dot-else.md) způsobem, jeho příkazy jsou provést, pokud byl původní podmínku hodnotu false. Všimněte si, že v době běhu vyhodnocení podmínek.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)