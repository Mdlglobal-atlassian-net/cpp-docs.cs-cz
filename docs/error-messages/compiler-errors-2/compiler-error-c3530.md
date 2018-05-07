---
title: C3530 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3530
dev_langs:
- C++
helpviewer_keywords:
- C3530
ms.assetid: 21be81ce-b699-4c74-81bc-80a0c34d2d5a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b6514d655ab813ae21ecb440415f87bce63f3591
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3530"></a>C3530 chyby kompilátoru
'auto' nelze kombinovat s jakékoli jiné – specifikátor typu  
  
 Specifikátor typu se používá s `auto` – klíčové slovo.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Nepoužívejte specifikátor typu deklarace proměnné, která používá `auto` – klíčové slovo.  
  
## <a name="example"></a>Příklad  
 Následující příklad vypočítá C3530, protože proměnná `x` je deklarovaný s oběma `auto` – klíčové slovo a typ `int`, a proto, že v příkladu je kompilovat s **/Zc: Auto**.  
  
```  
// C3530.cpp  
// Compile with /Zc:auto  
int main()  
{  
   auto int x;   // C3530  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Auto – klíčové slovo](../../cpp/auto-keyword.md)