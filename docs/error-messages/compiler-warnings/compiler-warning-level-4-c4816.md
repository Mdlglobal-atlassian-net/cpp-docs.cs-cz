---
title: "Kompilátoru (úroveň 4) upozornění C4816 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4816
dev_langs: C++
helpviewer_keywords: C4816
ms.assetid: 60f730ae-d942-4db9-ab97-41d4a874d8da
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 718f44a665757941c9dc837819494eb1d36061a5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4816"></a>C4816 kompilátoru upozornění (úroveň 4)
'param': parametr má nulovou velikostí pole, která bude zkrácen (Pokud je objekt předán odkazem)  
  
 Parametr pro objekt s polem nula velikost nebyl předán odkazem. Pole získat nezkopírují, když je předána objektu.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4816:  
  
```  
// C4816.cpp  
// compile with: /W4  
#include <stdio.h>  
  
extern "C" int printf_s(const char *, ...);  
  
#pragma warning(disable : 4200)  
  
struct S1  
{  
    int i;  
    char cArr[];  
};  
  
void TestErr(S1 s1)   // C4816 param with zero-array   
                      // not passed by reference  
{  
    printf_s("%d %c %c\n", s1.i, s1.cArr[0], s1.cArr[1]);  
}  
  
void TestOk(S1 &s1)  
{  
    printf_s("%d %c %c\n", s1.i, s1.cArr[0], s1.cArr[1]);  
}  
  
int main()  
{  
    S1 myS_1 = { 6, 'a', 'b', 'c' };  
    TestErr(myS_1);  
    TestOk(myS_1);  
}  
```