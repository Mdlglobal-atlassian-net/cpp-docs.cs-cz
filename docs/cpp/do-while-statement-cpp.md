---
title: Proveďte-while – příkaz (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
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
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7e03a20ad2b49d5c9337e0c8250e5d7c321ee882
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="do-while-statement-c"></a>do-while – příkaz (C++)
Spustí *příkaz* opakovaně až do ukončení zadanou podmínku ( *výraz*) vyhodnotí na hodnotu nula.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
do  
   statement  
while ( expression ) ;  
```  
  
## <a name="remarks"></a>Poznámky  
 Test stavu ukončení se provádí po každé spuštění smyčky; Proto `do-while` provede jeden či více krát, v závislosti na hodnotě výrazu ukončení smyčky. `do-while` Příkaz můžete také při ukončení [zalomení](../cpp/break-statement-cpp.md), [goto](../cpp/goto-statement-cpp.md), nebo [vrátit](../cpp/return-statement-cpp.md) do těla příkazu je spustit příkaz.  
  
 *Výraz* musí mít typ aritmetické nebo ukazatel. Provádění pokračuje následujícím způsobem:  
  
1.  Provede se tělo příkaz.  
  
2.  Dále *výraz* vyhodnotí. Pokud *výraz* je nastavena hodnota false, `do-while` příkaz ukončí a předá řízení další příkaz v programu. Pokud *výraz* hodnotu true (nenulové hodnoty), tento proces se opakuje, počínaje z kroku 1.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje `do-while` příkaz:  
  
```  
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
 [Klíčová slova](../cpp/keywords-cpp.md)   
 [while – příkaz (C++)](../cpp/while-statement-cpp.md)   
 [pro příkaz (C++)](../cpp/for-statement-cpp.md)   
 [Příkaz For založený na rozsahu (C++)](../cpp/range-based-for-statement-cpp.md)