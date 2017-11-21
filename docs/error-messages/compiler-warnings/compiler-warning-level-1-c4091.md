---
title: "Kompilátoru (úroveň 1) upozornění C4091 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4091
dev_langs: C++
helpviewer_keywords: C4091
ms.assetid: 3a404967-ab42-49b0-b324-fd7ba1859d78
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9b40596872bba7cc914f148f36c7d31dde5dd103
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4091"></a>C4091 kompilátoru upozornění (úroveň 1)
'– klíčové slovo': na nalevo od "typ" ignorována, pokud je deklarovaná žádné proměnné  
  
 Kompilátor zjištěna situaci, kdy uživatel pravděpodobně určené proměnnou deklarovat, ale kompilátor nebyl schopen deklarovat proměnnou.  
  
## <a name="example"></a>Příklad  
 A `__declspec` atribut na začátku prohlášení uživatelsky definovaný typ. platí pro proměnnou daného typu. C4091 označuje, že je deklarovaná žádné proměnné. Následující ukázka generuje C4091.  
  
```  
// C4091.cpp  
// compile with: /W1 /c  
__declspec(dllimport) class X {}; // C4091  
  
// __declspec attribute applies to varX  
__declspec(dllimport) class X2 {} varX;  
  
// __declspec attribute after the class or struct keyword   
// applies to user defined type  
class __declspec(dllimport) X3 {};  
```  
  
## <a name="example"></a>Příklad  
 Pokud je identifikátor definice typu, nelze ji také název proměnné. Následující ukázka generuje C4091.  
  
```  
// C4091_b.cpp  
// compile with: /c /W1 /WX  
#define LIST 4  
typedef struct _LIST {} LIST;   // C4091  
```