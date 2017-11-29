---
title: "Kompilátoru (úroveň 1) upozornění C4742 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4742
dev_langs: C++
helpviewer_keywords: C4742
ms.assetid: e520881d-1eeb-48b1-9df0-8017ee8ba076
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 934c7d14d95d0b90cfdcdb694f743e6b13abd0e2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4742"></a>C4742 kompilátoru upozornění (úroveň 1)
'příkaz var' má jiné zarovnání v 'file1' a 'file2': číslo a číslo  
  
 Proměnná externí, která byla definována v dva soubory nebo odkazuje má jiné zarovnání v těchto souborů. Toto upozornění je vygenerované při kompilátoru zjistí, že `__alignof` pro proměnné v *file1* se liší od `__alignof` pro proměnné v *file2*. To může být způsobeno pomocí nekompatibilní typy při deklarace proměnné v různých souborů, nebo pomocí neodpovídající `#pragma pack` v různých souborů.  
  
 Chcete-li vyřešit toto upozornění, buď použijte stejné definice typu nebo použijte odlišné názvy proměnných.  
  
 Další informace najdete v tématu [pack](../../preprocessor/pack.md) a [__alignof – operátor](../../cpp/alignof-operator.md).  
  
## <a name="example"></a>Příklad  
 Toto je první soubor, který definuje typ.  
  
```  
// C4742a.c  
// compile with: /c  
struct X {  
   char x, y, z, w;  
} global;  
```  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4742.  
  
```  
// C4742b.c  
// compile with: C4742a.c /W1 /GL  
// C4742 expected  
extern struct X {  
   int a;  
} global;  
  
int main() {  
   global.a = 0;  
}  
```