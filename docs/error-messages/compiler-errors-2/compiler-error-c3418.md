---
title: C3418 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3418
dev_langs:
- C++
helpviewer_keywords:
- C3418
ms.assetid: 54042c04-3c45-41c1-bad7-90f9ee05a21b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 92147a636ff1b087134dd7c2d3fdbdb1398d5135
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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