---
title: list::Remove (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::list::remove
dev_langs: C++
helpviewer_keywords: remove member [STL/CLR]
ms.assetid: eaf598ee-e8fd-4cc0-be69-ca81a80e1d51
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 306c758ba2278fcac9ceb0e6b701d298804e8b6e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="listremove-stlclr"></a>list::remove (STL/CLR)
Odebere element se zadanou hodnotou.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void remove(value_type val);  
```  
  
#### <a name="parameters"></a>Parametry  
 Val  
 Hodnota elementu, který chcete odebrat.  
  
## <a name="remarks"></a>Poznámky  
 Členská funkce odebere elementu v řízené sekvenci pro kterou `((System::Object^)val)->Equals((System::Object^)x)` hodnotu true (pokud existuje). Použijete jej vymazat libovolně zvolený element se zadanou hodnotou.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_list_remove.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// fail to remove and redisplay   
    c1.remove(L'A');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();  
  
// remove and redisplay   
    c1.remove(L'b');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
a c  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – nebo jejich výpisu >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [seznam (STL/CLR)](../dotnet/list-stl-clr.md)   
 [list::clear (STL/CLR)](../dotnet/list-clear-stl-clr.md)   
 [list::Erase (STL/CLR)](../dotnet/list-erase-stl-clr.md)   
 [list::remove_if (STL/CLR)](../dotnet/list-remove-if-stl-clr.md)