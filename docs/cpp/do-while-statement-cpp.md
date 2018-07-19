---
title: Proveďte-while – příkaz (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- do_cpp
dev_langs:
- C++
helpviewer_keywords:
- do keyword [C++], do-while
- do-while keyword [C++]
- do keyword [C++]
- while keyword [C++], do-while
ms.assetid: e01e6f7c-7da1-4591-87f9-c26ff848e7b0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d2de180d58c31f4bd6c8b15eb69076b99f8b57b0
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947647"
---
# <a name="do-while-statement-c"></a>do-while – příkaz (C++)
Spustí *příkaz* opakovaně, dokud není zadaná ukončovací podmínka ( *výraz*) vyhodnocen jako nula.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
do  
   statement  
while ( expression ) ;  
```  
  
## <a name="remarks"></a>Poznámky  
 Podmínka ukončení zkoušky se provádí po každém spuštění smyčky; Proto **proveďte – zatímco** cyklus se opakuje, jednou nebo vícekrát, v závislosti na hodnotě výrazu ukončení. **Proveďte-při** příkaz může také skončit při [přerušení](../cpp/break-statement-cpp.md), [goto](../cpp/goto-statement-cpp.md), nebo [vrátit](../cpp/return-statement-cpp.md) je proveden příkaz v rámci těla příkazu.  
  
 *Výraz* musí mít aritmetický typ nebo typ ukazatele. Spuštění probíhá následujícím způsobem:  
  
1.  Provede se tělo příkazu.  
  
2.  Dále *výraz* vyhodnocena. Pokud *výraz* má hodnotu false, **proveďte-při** příkaz skončí a předá řízení dalšímu příkazu v programu. Pokud *výraz* má hodnotu true (nenulový), proces se opakuje, počínaje krokem 1.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje **proveďte – zatímco** – příkaz:  
  
```cpp 
// do_while_statement.cpp  
#include <stdio.h>  
int main()  
{  
    int i = 0;  
    do  
    {  
        printf_s("\n%d",i++);  
    } while (i < 3);  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Příkazy iterace](../cpp/iteration-statements-cpp.md)   
 [klíčová slova](../cpp/keywords-cpp.md)   
 [while – příkaz (C++)](../cpp/while-statement-cpp.md)   
 [for – příkaz (C++)](../cpp/for-statement-cpp.md)   
 [Příkaz For založený na rozsahu (C++)](../cpp/range-based-for-statement-cpp.md)