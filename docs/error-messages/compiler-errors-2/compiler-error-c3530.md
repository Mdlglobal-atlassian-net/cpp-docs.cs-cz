---
title: "C3530 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3530
dev_langs: C++
helpviewer_keywords: C3530
ms.assetid: 21be81ce-b699-4c74-81bc-80a0c34d2d5a
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0d66e76fc3e44a037f52aa6e217fae848f1338d2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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