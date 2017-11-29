---
title: "C2032 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2032
dev_langs: C++
helpviewer_keywords: C2032
ms.assetid: 625d7c83-70b6-42c2-a558-81fbc0026324
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 81bbe4c9e5242f68a5e0e304858c13c9274c1743
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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