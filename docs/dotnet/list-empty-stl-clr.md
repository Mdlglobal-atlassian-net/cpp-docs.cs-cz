---
title: list::Empty (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::list::empty
dev_langs: C++
helpviewer_keywords: empty member [STL/CLR]
ms.assetid: f45edf8a-927d-41ff-9c09-cb0fba4f08b8
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 388a7ffd665652626dc48d4278a57e38c34e91b0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="listempty-stlclr"></a>list::empty (STL/CLR)
Zkouší, zda nejsou přítomny žádné prvky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
bool empty();  
```  
  
## <a name="remarks"></a>Poznámky  
 Členská funkce vrátí hodnotu true pro prázdný řízené sekvenci. Ta je ekvivalentní [list::size (STL/CLR)](../dotnet/list-size-stl-clr.md)`() == 0`. Můžete použít k ověření, zda seznam je prázdný.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_list_empty.cpp   
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
    System::Console::WriteLine("size() = {0}", c1.size());   
    System::Console::WriteLine("empty() = {0}", c1.empty());   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    System::Console::WriteLine("empty() = {0}", c1.empty());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
size() = 3  
empty() = False  
size() = 0  
empty() = True  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – nebo jejich výpisu >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [seznam (STL/CLR)](../dotnet/list-stl-clr.md)   
 [list::size (STL/CLR)](../dotnet/list-size-stl-clr.md)