---
title: Stack::top_item (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::stack::top_item
dev_langs: C++
helpviewer_keywords: top_item member [STL/CLR]
ms.assetid: 01571acf-4880-44c4-80c4-bd91408a032d
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8138ce1d0eb313f5e84c374a35b6e9e0d58ef909
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="stacktopitem-stlclr"></a>stack::top_item (STL/CLR)
Přístup k posledním elementem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
property value_type top_item;  
```  
  
## <a name="remarks"></a>Poznámky  
 Vlastnost přistupuje ke poslední elementu řízené sekvenci, která musí být neprázdný. Použijete jej číst nebo zapisovat posledním elementem, když víte, že existuje.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_stack_top_item.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last item   
    System::Console::WriteLine("top_item = {0}", c1.top_item);   
  
// alter last item and reinspect   
    c1.top_item = L'x';   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
top_item = c  
 a b x  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / stack >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [Zásobník (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [Stack::top (STL/CLR)](../dotnet/stack-top-stl-clr.md)