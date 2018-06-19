---
title: C2015 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2015
dev_langs:
- C++
helpviewer_keywords:
- C2015
ms.assetid: 8f40af0a-3a5a-4d6a-8ed7-125966e6bfed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 91c682aadeab5a572ec2bb5c2e649a1511af77ef
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33165620"
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