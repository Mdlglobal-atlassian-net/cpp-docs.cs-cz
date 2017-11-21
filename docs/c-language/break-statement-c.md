---
title: "Rozdělit Statement (C) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: break
dev_langs: C++
helpviewer_keywords: break keyword [C]
ms.assetid: 015627c7-0924-49b2-a4d1-c77edf5eae6a
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a180c88fc71e4786e8512bc26421825132611ed4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="break-statement-c"></a>break – příkaz (C)
Příkaz `break` ukončí spouštění nejbližšího nadřazeného příkazu `do`, `for`, `switch` nebo `while`, v němž se vyskytuje. Řízení je předáno příkazu, který následuje ukončený příkaz.  
  
## <a name="syntax"></a>Syntaxe  
 *příkaz přechod*:  
 `break;`  
  
 Příkaz `break` se často používá k ukončení zpracování konkrétního případu v příkazu `switch`. Absence nadřazeného iterativního příkazu nebo příkazu `switch` způsobí chybu.  
  
 V rámci vnořených příkazů příkaz `break` ukončí pouze příkaz `do`, `for`, `switch` nebo `while`, který jej bezprostředně obklopuje. Pomocí příkazu `return` nebo `goto` lze převést řízení jinam mimo vnořenou strukturu.  
  
 Následující příklad znázorňuje příkaz `break`:  
  
```  
#include <stdio.h>  
int main() {  
   char c;  
   for(;;) {  
      printf_s( "\nPress any key, Q to quit: " );  
  
      // Convert to character value  
      scanf_s("%c", &c);  
      if (c == 'Q')  
          break;  
   }  
} // Loop exits only when 'Q' is pressed  
```  
  
## <a name="see-also"></a>Viz také  
 [Příkaz BREAK](../cpp/break-statement-cpp.md)