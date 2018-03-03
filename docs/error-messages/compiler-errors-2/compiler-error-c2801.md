---
title: "C2801 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2801
dev_langs:
- C++
helpviewer_keywords:
- C2801
ms.assetid: 35dfc7ea-9e37-4e30-baa1-944dc61302f5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bbdbfdc1b7bb9445b1a709afb42944eea0d7f241
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2801"></a>C2801 chyby kompilátoru
'operátor operátor' musí být členem nestatické  
  
 Následující operátory mohou být přetíženy pouze jako nestatické členy:  
  
-   Přiřazení`=`  
  
-   Přístup ke členu – třída`->`  
  
-   Subscripting`[]`  
  
-   Volání funkce`()`  
  
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