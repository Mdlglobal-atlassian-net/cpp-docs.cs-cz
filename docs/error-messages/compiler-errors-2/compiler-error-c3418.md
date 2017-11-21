---
title: "C3418 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3418
dev_langs: C++
helpviewer_keywords: C3418
ms.assetid: 54042c04-3c45-41c1-bad7-90f9ee05a21b
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0ae644c17a39e574984dc8bb0689955fd1bef2be
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3418"></a>C3418 chyby kompilátoru
specifikátor přístupu 'specifikátor' není podporován.  
  
CLR specifikátor přístup byl nesprávně zadán.  Další informace najdete v tématu viditelnost typů a viditelnost členů v [postupy: definování a využívat třídy a struktury (C + +/ CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md).  
  
## <a name="example"></a>Příklad  
Následující ukázka generuje C3418.  
  
```cpp  
// C3418.cpp  
// compile with: /clr /c  
ref struct m {  
internal public:   // C3418  
   void test(){}  
};  
  
ref struct n {  
internal:   // OK  
   void test(){}  
};  
```