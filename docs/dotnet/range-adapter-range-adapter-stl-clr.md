---
title: range_adapter::range_adapter (STL/CLR) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- cliext::range_adapter::range_adapter
dev_langs:
- C++
helpviewer_keywords:
- range_adapter member [STL/CLR]
ms.assetid: b16af13f-3358-4e82-927d-d0d4986bcb18
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3a8b93b6a02a2ad0db7282f7e5e8e3159dd23add
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="rangeadapterrangeadapter-stlclr"></a>range_adapter::range_adapter (STL/CLR)
Vytvoří objekt adaptéru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
range_adapter();  
range_adapter(range_adapter<Iter>% right);  
range_adapter(range_adapter<Iter>^ right);  
range_adapter(Iter first, Iter last);  
```  
  
#### <a name="parameters"></a>Parametry  
 první  
 První iterator zabalit.  
  
 poslední  
 Druhý iterator zabalit.  
  
 vpravo  
 Objekt, který chcete kopírovat.  
  
## <a name="remarks"></a>Poznámky  
 Konstruktor:  
  
 `range_adapter();`  
  
 Inicializuje pár uložené iterator s iterátory výchozí zkonstruovat.  
  
 Konstruktor:  
  
 `range_adapter(range_adapter<Iter>% right);`  
  
 Inicializuje pár uložené iterator zkopírováním pár uložené v `right`.  
  
 Konstruktor:  
  
 `range_adapter(range_adapter<Iter>^ right);`  
  
 Inicializuje pár uložené iterator zkopírováním pár uložené v `*right`.  
  
 Konstruktor:  
  
 `range_adapter(Iter^ first, last);`  
  
 Inicializuje pár uložené iterator s `first` a `last`.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_range_adapter_construct.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::deque<wchar_t> Mycont;   
typedef cliext::range_adapter<Mycont::iterator> Myrange;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
  
// construct an empty adapter   
    Myrange c1;   
  
// construct with an iterator pair   
    Myrange c2(d1.begin(), d1.end());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another adapter   
    Myrange c3(c2);   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying an adapter handle   
    Myrange c4(%c3);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
a b c  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – nebo adaptér >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [range_adapter – (STL/CLR)](../dotnet/range-adapter-stl-clr.md)   
 [range_adapter::operator= (STL/CLR)](../dotnet/range-adapter-operator-assign-stl-clr.md)