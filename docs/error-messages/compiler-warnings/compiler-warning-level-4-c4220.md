---
title: "Kompilátoru (úroveň 4) upozornění C4220 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4220
dev_langs: C++
helpviewer_keywords: C4220
ms.assetid: aba18868-825f-4763-9af6-3296406a80e4
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 82e921ecbb19ff705c7e2341d39d07991d6cb30a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4220"></a>C4220 kompilátoru upozornění (úroveň 4)
vararg odpovídá zbývající parametry  
  
 V části rozšíření Microsoft výchozí (/Ze) odpovídá ukazatel na funkci ukazatel na funkci s podobné, ale proměnné, argumenty.  
  
## <a name="example"></a>Příklad  
  
```  
// C4220.c  
// compile with: /W4  
  
int ( *pFunc1) ( int a, ... );  
int ( *pFunc2) ( int a, int b);  
  
int main()  
{  
   if ( pFunc1 != pFunc2 ) {};  // C4220  
}  
```  
  
 Tyto ukazatele neodpovídají žádné pod kompatibility ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).