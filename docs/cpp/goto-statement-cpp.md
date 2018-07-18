---
title: goto – příkaz (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- goto_cpp
dev_langs:
- C++
helpviewer_keywords:
- goto keyword [C++]
ms.assetid: 724c5deb-2de1-42d8-8ef1-23589d9bf5ed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7676f38e52734fa2f0ce8ecbc9b268be1939f6dc
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38953392"
---
# <a name="goto-statement-c"></a>goto – příkaz (C++)
**Goto** příkaz bezpodmínečně přenese ovládací prvek na příkaz s popiskem podle zadaného identifikátoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
goto identifier;  
```  
  
## <a name="remarks"></a>Poznámky  
 Příkaz s popiskem určeným `identifier` musí být v aktuální funkci. Všechny `identifier` názvy jsou členy vnitřní obor názvů a proto nejsou v konfliktu s další identifikátory.  
  
 Má smysl jenom na popisek příkazu **goto** příkazu; v opačném případě se ignorují popisků příkazů. Popisky nelze deklarovat znovu.  
  
 Styl programování je dobrým **přerušení**, **pokračovat**, a **vrátit** příkazy místo **goto** příkaz pokaždé, když je to možné. Ale protože **přerušení** příkaz ukončí pouze jednu úroveň smyčky, možná budete muset použít **goto** příkaz Ukončit hluboce vnořený smyčku.  
  
 Další informace o popisky a **goto** příkaz, naleznete v tématu [příkazy s popiskem](../cpp/labeled-statements.md).  
  
## <a name="example"></a>Příklad  
 V tomto příkladu **goto** příkaz přenese ovládací prvek na bod s názvem `stop` při `i` rovná 3.  
  
```cpp  
// goto_statement.cpp  
#include <stdio.h>  
int main()  
{  
    int i, j;  
  
    for ( i = 0; i < 10; i++ )  
    {  
        printf_s( "Outer loop executing. i = %d\n", i );  
        for ( j = 0; j < 2; j++ )  
        {  
            printf_s( " Inner loop executing. j = %d\n", j );  
            if ( i == 3 )  
                goto stop;  
        }  
    }  
  
    // This message does not print:   
    printf_s( "Loop exited. i = %d\n", i );  
  
    stop:   
    printf_s( "Jumped to stop. i = %d\n", i );  
}  
```  
  
```Output  
Outer loop executing. i = 0  
 Inner loop executing. j = 0  
 Inner loop executing. j = 1  
Outer loop executing. i = 1  
 Inner loop executing. j = 0  
 Inner loop executing. j = 1  
Outer loop executing. i = 2  
 Inner loop executing. j = 0  
 Inner loop executing. j = 1  
Outer loop executing. i = 3  
 Inner loop executing. j = 0  
Jumped to stop. i = 3  
```  
  
## <a name="see-also"></a>Viz také  
 [Jump – příkazy](../cpp/jump-statements-cpp.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)