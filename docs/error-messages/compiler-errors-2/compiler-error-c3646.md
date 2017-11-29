---
title: "C3646 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3646
dev_langs: C++
helpviewer_keywords: C3646
ms.assetid: 4391ead2-9637-4ca3-aeda-5a991b18d66d
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0bc9b2601a57e2be98c3a356cbd2ede69dc7be79
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3646"></a>C3646 chyby kompilátoru
'specifikátor': Neznámý přepsání specifikátor  
  
 Kompilátor nalezen token v pozice, kdy se očekává nalezení specifikátor přepsání, ale token nebyl rozpoznán překladačem.  
  
 Další informace najdete v tématu [přepsat specifikátory](../../windows/override-specifiers-cpp-component-extensions.md).  
  
 Následující ukázka generuje C3646:  
  
```  
// C3646.cpp  
// compile with: /clr /c  
ref class C {  
   void f() unknown;   // C3646  
   // try the following line instead  
   // virtual void f() abstract;  
};  
```