---
title: "C2015 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2015
dev_langs: C++
helpviewer_keywords: C2015
ms.assetid: 8f40af0a-3a5a-4d6a-8ed7-125966e6bfed
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4669eec9d8134db6e024257855012eb78dcef95e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2015"></a>C2015 chyby kompilátoru
příliš mnoho znaků v konstanta  
  
 Konstanta znaků obsahuje více než dva znaky. Limit je jeden znak pro standardní znak konstanty a dva znaky pro konstanty znaků dlouhé.  
  
 Řídicí sekvence, jako je například \t, jsou převedeny na jednoho znaku.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C2015:  
  
```  
// C2015.cpp  
// compile with: /c  
  
char test1 = 'error';   // C2015  
char test2 = 'e';   // OK  
```  
  
## <a name="example"></a>Příklad  
 C2015 může dojít také při použití Microsoft rozšíření, převést na celá čísla konstanty znaků.  Následující ukázka generuje C2015:  
  
```  
// C2015b.cpp  
#include <stdio.h>  
  
int main()   
{  
    int a = 'abcde';   // C2015  
  
    int b = 'a';   // 'a' = ascii 0x61  
    printf_s("%x\n", b);  
}  
```