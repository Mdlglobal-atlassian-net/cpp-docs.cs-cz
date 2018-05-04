---
title: Null – příkaz | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- expressions [C++], null
- null statement
- null values, expressions
ms.assetid: 606f5953-55f0-40c8-ae03-3ee3a819b851
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 624ff1051977804e6cefd97a813dce36cacdc3e5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
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