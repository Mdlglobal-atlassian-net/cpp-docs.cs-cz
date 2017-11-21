---
title: "C2473 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2473
dev_langs: C++
helpviewer_keywords: C2473
ms.assetid: 6bb7dbf5-b198-490f-860e-fd64d0c2a284
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: bbc3432383e39913ed3cd89b310b00706a26a589
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2473"></a>C2473 chyby kompilátoru
"identifikátor": vypadá jako definice funkce, ale neexistuje žádný seznam parametrů.  
  
 Kompilátor zjištěna, co hledá jako funkci, bez seznam parametrů.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C2473.  
  
```  
// C2473.cpp  
// compile with: /clr /c  
class A {  
   int i {}   // C2473  
};  
  
class B {  
   int i() {}   // OK  
};  
```