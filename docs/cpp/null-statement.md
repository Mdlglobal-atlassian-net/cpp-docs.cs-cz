---
title: "Null – příkaz | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- expressions [C++], null
- null statement
- null values, expressions
ms.assetid: 606f5953-55f0-40c8-ae03-3ee3a819b851
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ecaa8d968efa9a3cd8c700d3d4dfe4cae0f0dd53
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="null-statement"></a>Null – příkaz
Příkaz výrazu s je "Null příkaz" *výraz* chybí. Je užitečný, když syntaxe jazyka vyžaduje výraz, ale žádné vyhodnocení výrazu. Skládá se ze středníku.  
  
 Příkazy null se obvykle používají jako zástupné symboly v příkazech iterace nebo jako příkazy, na které chcete umístit popisky na konci složených příkazů nebo funkcí.  
  
 Následující fragment kódu ukazuje, jak zkopírovat jeden řetězec do druhého a zahrnuje příkaz null:  
  
```  
// null_statement.cpp  
char *myStrCpy( char *Dest, const char *Source )  
{  
    char *DestStart = Dest;  
  
    // Assign value pointed to by Source to  
    // Dest until the end-of-string 0 is  
    // encountered.  
    while( *Dest++ = *Source++ )  
        ;   // Null statement.  
  
    return DestStart;  
}  
  
int main()  
{  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Příkaz výrazu](../cpp/expression-statement.md)