---
title: Stack::to_array (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::stack::to_array
dev_langs: C++
helpviewer_keywords: to_array member [STL/CLR]
ms.assetid: e83bd7c4-ffdb-4151-bd2b-c36ca828e12f
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: de5b050263998e752abbc3bc03bde4adc9dc1dc1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="stacktoarray-stlclr"></a>stack::to_array (STL/CLR)
Zkopíruje řízené sekvenci do nové pole.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
cli::array<Value>^ to_array();  
```  
  
## <a name="remarks"></a>Poznámky  
 Členská funkce vrátí pole obsahující řízené sekvenci. Můžete ji použít k získání kopii řízené sekvenci v pole formuláře.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_stack_to_array.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// copy the container and modify it   
    cli::array<wchar_t>^ a1 = c1.to_array();   
  
    c1.push(L'd');   
    for each (wchar_t elem in c1.get_container())   
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
 **Záhlaví:** \<cliext – / stack >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [Zásobník (STL/CLR)](../dotnet/stack-stl-clr.md)