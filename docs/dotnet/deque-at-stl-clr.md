---
title: deque::AT (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::deque::at
dev_langs: C++
helpviewer_keywords: at member [STL/CLR]
ms.assetid: 9af83d8a-c519-4b2a-a25f-d3dc8bbb87fb
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: bf07c109bfd80fb34af007b0a66dd6f7a2dbd3af
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="dequeat-stlclr"></a>deque::at (STL/CLR)
Přístup k elementu na zadané pozici.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
reference at(size_type pos);  
```  
  
#### <a name="parameters"></a>Parametry  
 POS  
 Pozice elementu přístup.  
  
## <a name="remarks"></a>Poznámky  
 Členská funkce vrátí odkaz na element řízené sekvenci na pozici `pos`. Můžete použít ke čtení nebo zápisu elementu, jejíž pozice s znáte.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_deque_at.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" using at   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1.at(i));   
    System::Console::WriteLine();   
  
// change an entry and redisplay   
    c1.at(1) = L'x';   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1[i]);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a x c  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / deque >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [deque::Operator(STL/CLR)](../dotnet/deque-operator-stl-clr.md)