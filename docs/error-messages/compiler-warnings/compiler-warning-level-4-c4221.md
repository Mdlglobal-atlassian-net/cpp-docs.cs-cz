---
title: "Kompilátoru (úroveň 4) upozornění C4221 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4221
dev_langs: C++
helpviewer_keywords: C4221
ms.assetid: 8532bd68-54dc-4526-8597-f61dcb0a0129
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cb797b4efce63f3fd8d0b19226611809dd2a5d3c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4221"></a>C4221 kompilátoru upozornění (úroveň 4)
nestandardní rozšíření používané: "identifikátor": Nelze inicializovat pomocí adresy automatické proměnné  
  
 Rozšíření Microsoft výchozí (/Ze), bude možné inicializovat typ agregace (**pole**, `struct`, nebo **sjednocení**) s adresou místní proměnné (automaticky).  
  
## <a name="example"></a>Příklad  
  
```  
// C4221.c  
// compile with: /W4  
struct S  
{  
   int *i;  
};  
  
void func()  
{  
   int j;  
   struct S s1 = { &j };   // C4221  
}  
  
int main()  
{  
}  
```  
  
 Takové inicializacích jsou neplatné v části kompatibility ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).