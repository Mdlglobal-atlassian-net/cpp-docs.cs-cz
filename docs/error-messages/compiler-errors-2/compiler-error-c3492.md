---
title: "C3492 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3492
dev_langs: C++
helpviewer_keywords: C3492
ms.assetid: b1dc6342-9133-4b1f-a9c3-e8c65d20d121
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a1b2626d49f759b3e694890ddb73a33e92803dc6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
 [Lambda – výrazy](../../cpp/lambda-expressions-in-cpp.md)