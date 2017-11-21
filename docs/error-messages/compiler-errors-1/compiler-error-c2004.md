---
title: "C2004 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2004
dev_langs: C++
helpviewer_keywords: C2004
ms.assetid: d81526dd-3a00-4593-87b0-d910d3d29bca
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f4596e43fad713f6b0a81eea9e697c6e0f91c75b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2004"></a>C2004 chyby kompilátoru
Očekávaný 'defined(id).  
  
 Identifikátor musí být uvedena v závorkách za preprocesoru – klíčové slovo.  
  
 Tato chyba může být také vygenerovaného jako výsledek kompilátoru shoda práci, kterou bylo provedeno pro Visual Studio .NET 2003: chybí závorky v direktivy preprocesoru. Pokud direktivy preprocesoru chybí uzavírací kulatá závorka, kompilátor vygeneruje chybu.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C2004:  
  
```  
// C2004.cpp  
// compile with: /DDEBUG  
#include <stdio.h>  
  
int main()   
{  
    #if defined(DEBUG   // C2004  
        printf_s("DEBUG defined\n");  
    #endif  
}  
```  
  
## <a name="example"></a>Příklad  
 Možná řešení:  
  
```  
// C2004b.cpp  
// compile with: /DDEBUG  
#include <stdio.h>  
  
int main()   
{  
    #if defined(DEBUG)  
        printf_s("DEBUG defined\n");  
    #endif  
}  
```