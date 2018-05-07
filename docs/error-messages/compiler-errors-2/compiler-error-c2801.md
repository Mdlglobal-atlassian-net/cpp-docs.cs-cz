---
title: C2801 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2801
dev_langs:
- C++
helpviewer_keywords:
- C2801
ms.assetid: 35dfc7ea-9e37-4e30-baa1-944dc61302f5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f68b3f575fcb8b909f58ac2ffbcaca26580279da
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2801"></a>C2801 chyby kompilátoru
'operátor operátor' musí být členem nestatické  
  
 Následující operátory mohou být přetíženy pouze jako nestatické členy:  
  
-   Přiřazení `=`  
  
-   Přístup ke členu – třída `->`  
  
-   Subscripting `[]`  
  
-   Volání funkce `()`  
  
 Možné příčiny C2801:  
  
-   Přetížené operátor není třídy, struktury nebo členů sjednocení.  
  
-   Přetížené operátor je deklarovaná `static`.  
  
-   Následující ukázka generuje C2801:  
  
```  
// C2801.cpp  
// compile with: /c  
operator[]();   // C2801 not a member  
class A {  
   static operator->();   // C2801 static  
   operator()();   // OK  
};  
```