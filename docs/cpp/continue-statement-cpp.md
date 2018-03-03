---
title: "pokračovat – příkaz (C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- continue_cpp
dev_langs:
- C++
helpviewer_keywords:
- continue keyword [C++]
ms.assetid: 3c94ee57-f732-4c1d-8537-d0ce5382bfd4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3e4dd91489bfe22fca875f98110dadcb75def39d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="continue-statement-c"></a>continue – příkaz (C++)
Vynutí přenos řízení na řízení výraz nejmenší obklopuje [provést](../cpp/do-while-statement-cpp.md), [pro](../cpp/for-statement-cpp.md), nebo [při](../cpp/while-statement-cpp.md) smyčky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
continue;  
```  
  
## <a name="remarks"></a>Poznámky  
 Všechny zbývající příkazy v aktuální iteraci nebudou provedeny. Další iterace smyčky je stanoven následujícím způsobem:  
  
-   V `do` nebo `while` smyčky, další iterace začne reevaluating řízení výraz `do` nebo `while` příkaz.  
  
-   V `for` smyčky (pomocí syntaxe `for`(`init-expr`; `cond-expr`; `loop-expr`)), `loop-expr` klauzule se spustí. Pak se `cond-expr` klauzule je již znovu a, v závislosti na výsledek, že opakování ve smyčce buď končí nebo nastane jiný iterace.  
  
 Následující příklad ukazuje jak `continue` příkaz lze použít vynechat sekcí kódu a spustíte následující iteraci smyčky.  
  
## <a name="example"></a>Příklad  
  
```  
// continue_statement.cpp  
#include <stdio.h>  
int main()  
{  
    int i = 0;  
    do  
    {  
        i++;  
        printf_s("before the continue\n");  
        continue;  
        printf("after the continue, should never print\n");  
     } while (i < 3);  
  
     printf_s("after the do loop\n");  
}  
```  
  
```Output  
before the continue  
before the continue  
before the continue  
after the do loop  
```  
  
## <a name="see-also"></a>Viz také  
 [Jump – příkazy](../cpp/jump-statements-cpp.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)