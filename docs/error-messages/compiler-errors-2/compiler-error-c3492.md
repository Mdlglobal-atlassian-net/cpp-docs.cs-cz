---
title: C3492 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3492
dev_langs:
- C++
helpviewer_keywords:
- C3492
ms.assetid: b1dc6342-9133-4b1f-a9c3-e8c65d20d121
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: de9fb29b13c1bbae7c86f80da53c11590e7c7d2b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3492"></a>C3492 chyby kompilátoru
'příkaz var': nemůže zaznamenat členem anonymní sjednocení  
  
 Nelze zaznamenat členem nepojmenované union.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Pojmenujte sjednocení a předejte strukturu dokončení sjednocení seznamu zachycení výrazu lambda.  
  
## <a name="example"></a>Příklad  
 Následující příklad generuje C3492, protože zachycení členem anonymní sjednocení:  
  
```  
// C3492a.cpp  
  
int main()  
{  
   union  
   {  
      char ch;  
      int x;  
   };  
  
   ch = 'y';  
   [&x](char ch) { x = ch; }(ch); // C3492  
}  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad přeloží C3492 tím, že název sjednocení a předáním strukturu dokončení union do seznamu zachycení výrazu lambda:  
  
```  
// C3492b.cpp  
  
int main()  
{  
   union  
   {  
      char ch;  
      int x;  
   } u;  
  
   u.ch = 'y';  
   [&u](char ch) { u.x = ch; }(u.ch);  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)