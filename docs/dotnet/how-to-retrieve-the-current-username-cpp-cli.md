---
title: "Postupy: načtení aktuálního jména uživatele (C + +/ CLI) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- current user names
- user names, retrieving
- UserName string
ms.assetid: 91679571-d029-41f5-b657-1460c81c608a
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c4738c829f346126dfed7990c50186a7c267df1a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-retrieve-the-current-username-ccli"></a>Postupy: Načtení aktuálního jména uživatele (C++/CLI)
Následující příklad kódu ukazuje načtení aktuální uživatelské jméno (název uživatele přihlášeného do systému Windows). Název je uložen v <xref:System.Environment.UserName%2A> řetězce, který je definován v <xref:System.Environment> oboru názvů.  
  
## <a name="example"></a>Příklad  
  
```  
// username.cpp  
// compile with: /clr  
using namespace System;  
  
int main()   
{  
   Console::WriteLine("\nCurrent user: {0}", Environment::UserName);  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Operace systému Windows (C + +/ CLI)](../dotnet/windows-operations-cpp-cli.md)   
 [.NET – programování s C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)