---
title: "C3851 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3851
dev_langs: C++
helpviewer_keywords: C3851
ms.assetid: da30c21c-33aa-4439-8fb3-2f5021ea4985
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ed2a62b859e37455041171c81bb6830db372c697
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3851"></a>C3851 chyby kompilátoru
"char": universal znak name nelze určit znak v základní znakové sady  
  
 V kódu kompilovány jako C++ nemůžete použít název universal znaku představující znak ve znakové sadě základní zdroj mimo řetězec nebo znak literálu. Další informace najdete v tématu [znakových sad](../../cpp/character-sets2.md). V kódu kompilovány jako C nelze použijete název universal znak znaků v rozsahu 0x20-0x7f, včetně, s výjimkou 0x24 ('$'), 0x40 (' @'), nebo 0x60 ('' ').  
  
 Následující ukázky generovat C3851 a ukazují, jak to opravit:  
  
```cpp  
// C3851.cpp  
int main()  
{  
   int test1_\u0041 = 0;   // C3851, \u0041 = 'A' in basic character set  
   int test2_A = 0;        // OK  
}  
```