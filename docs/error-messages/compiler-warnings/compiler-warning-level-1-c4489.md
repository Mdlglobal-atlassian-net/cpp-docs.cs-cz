---
title: "Kompilátoru (úroveň 1) upozornění C4489 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4489
dev_langs: C++
helpviewer_keywords: C4489
ms.assetid: 43b51c8c-27b5-44c9-b974-fe4b48f4896f
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3a937200e75a58a98b791a7096f005329848f5fa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4489"></a>C4489 kompilátoru upozornění (úroveň 1)
'specifikátor': není povoleno pro metodu rozhraní 'metoda'; přepsání specifikátory jsou povolená jenom u metody ref třídy a hodnota – třída  
  
 Klíčové slovo specifikátor byl nesprávně použit na metodu rozhraní.  
  
 Další informace najdete v tématu [přepsat specifikátory](../../windows/override-specifiers-cpp-component-extensions.md).  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4489.  
  
```  
// C4489.cpp  
// compile with: /clr /c /W1  
public interface class I {   
   void f() new;   // C4489  
   virtual void b() override;   // C4489  
  
   void g();   // OK  
};  
```