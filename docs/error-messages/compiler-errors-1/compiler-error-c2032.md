---
title: C2032 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2032
dev_langs:
- C++
helpviewer_keywords:
- C2032
ms.assetid: 625d7c83-70b6-42c2-a558-81fbc0026324
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1db268222f3b9f7ca6f9ce297680866185e6661d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33167213"
---
# <a name="compiler-error-c2032"></a>C2032 chyby kompilátoru
"identifikátor": funkce nesmí být členem struktura/sjednocení 'structorunion.  
  
 Struktura nebo union obsahuje členské funkce, která je povolena v jazyce C++, ale není v C. Chcete-li vyřešit chyby, kompilovat jako programu C++ nebo odeberte – členská funkce.  
  
 Následující ukázka generuje C2032:  
  
```  
// C2032.c  
struct z {  
   int i;  
   void func();   // C2032  
};  
```  
  
 Možná řešení:  
  
```  
// C2032b.c  
// compile with: /c  
struct z {  
   int i;  
};  
```