---
title: deque::to_array (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::deque::to_array
dev_langs: C++
helpviewer_keywords: to_array member [STL/CLR]
ms.assetid: ecd34f30-2ad8-47b5-8c5e-2466df46fe6d
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 106b28547d018dbdd5eb6fdd46d4f862cb9b77ab
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="dequetoarray-stlclr"></a>deque::to_array (STL/CLR)
Zkopíruje řízené sekvenci do nové pole.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
cli::array<Value>^ to_array();  
```  
  
## <a name="remarks"></a>Poznámky  
 Členská funkce vrátí pole obsahující řízené sekvenci. Můžete ji použít k získání kopii řízené sekvenci v pole formuláře.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_deque_to_array.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// copy the container and modify it   
    cli::array<wchar_t>^ a1 = c1.to_array();   
  
    c1.push_back(L'd');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display the earlier array copy   
    for each (wchar_t elem in a1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c d  
a b c  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / deque >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)