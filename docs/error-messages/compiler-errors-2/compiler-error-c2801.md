---
title: "C2801 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2801
dev_langs: C++
helpviewer_keywords: C2801
ms.assetid: 35dfc7ea-9e37-4e30-baa1-944dc61302f5
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 41e7956ace6c54cd55a2ed9f68f18c867bc80ad9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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