---
title: "C2663 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2663
dev_langs: C++
helpviewer_keywords: C2663
ms.assetid: 1e93e368-fd52-42bf-9908-9b6df467c8c9
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a9efe20b4a80b9ff6f337d32acd35320125008dc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2663"></a>C2663 chyby kompilátoru
'function': číslo přetížení mít žádné právní převody pro "this" ukazatele  
  
 Nebylo možné převést kompilátor `this` k jakékoli přetížené verze členské funkce.  
  
 Tato chyba může být způsobeno vyvolání jinou hodnotu než`const` – členská funkce na `const` objektu.  Možná řešení:  
  
1.  Odeberte `const` z deklarace objektu.  
  
2.  Přidat `const` do jednoho z přetížení funkce člen.  
  
 Následující ukázka generuje C2663:  
  
```  
// C2663.cpp  
struct C {  
   void f() volatile {}  
   void f() {}  
};  
  
struct D {  
   void f() volatile;  
   void f() const {}  
};  
  
const C *pcc;  
const D *pcd;  
  
int main() {  
   pcc->f();    // C2663  
   pcd->f();    // OK  
}  
```