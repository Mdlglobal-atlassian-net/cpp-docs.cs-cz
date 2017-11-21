---
title: "goto – příkaz (C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: goto_cpp
dev_langs: C++
helpviewer_keywords: goto keyword [C++]
ms.assetid: 724c5deb-2de1-42d8-8ef1-23589d9bf5ed
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 467e432f9086198577d76c3624f5cb45562c7283
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="goto-statement-c"></a>goto – příkaz (C++)
`goto` Příkaz bezpodmínečně předá řízení příkaz označené zadaného identifikátoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
goto identifier;  
```  
  
## <a name="remarks"></a>Poznámky  
 Příkaz s popiskem, který je určen podle `identifier` musí být v aktuální funkce. Všechny `identifier` názvy jsou členy vnitřní obor názvů a proto nebudou v konfliktu s další identifikátory.  
  
 Má smysl pouze pro příkaz štítek `goto` příkaz; jinak, jsou ignorovány příkaz popisky. Popisky nelze deklarovat.  
  
 Je vhodné programování styl použitý `break`, `continue`, a `return` příkazy místo `goto` příkaz kdykoli je to možné. Ale protože `break` příkaz ukončí z pouze jedna úroveň smyčku, možná budete muset použít `goto` příkaz ukončíte hluboko vložené smyčky.  
  
 Další informace o popisky a `goto` prohlášení, najdete v části [příkazy s popiskem](../cpp/labeled-statements.md) a [pomocí štítků s goto příkaz](http://msdn.microsoft.com/en-us/6cd7c31a-9822-4241-8566-f79f51be48fe).  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `goto` příkaz předá řízení bod s názvem bez přípony `stop` při `i` rovná 3.  
  
```  
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