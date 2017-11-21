---
title: collection_adapter::collection_adapter (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::collection_adapter
- cliext::collection_adapter::collection_adapter
dev_langs: C++
helpviewer_keywords: collection_adapter member [STL/CLR]
ms.assetid: 7e2bb75b-d735-4135-9523-719683e06fe9
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6b7f913ffb323bcfdb61d9d181f71297ec119e1a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="collectionadaptercollectionadapter-stlclr"></a>collection_adapter::collection_adapter (STL/CLR)
Vytvoří objekt adaptéru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
collection_adapter();  
collection_adapter(collection_adapter<Coll>% right);  
collection_adapter(collection_adapter<Coll>^ right);  
collection_adapter(Coll^ collection);  
```  
  
#### <a name="parameters"></a>Parametry  
 – kolekce  
 Obslužná rutina BCL Zabalit.  
  
 vpravo  
 Objekt, který chcete kopírovat.  
  
## <a name="remarks"></a>Poznámky  
 Konstruktor:  
  
 `collection_adapter();`  
  
 Inicializuje uložené popisovač s `nullptr`.  
  
 Konstruktor:  
  
 `collection_adapter(collection_adapter<Coll>% right);`  
  
 Inicializuje uložené popisovač s `right.` [collection_adapter::base (STL/CLR)](../dotnet/collection-adapter-base-stl-clr.md)`()`.  
  
 Konstruktor:  
  
 `collection_adapter(collection_adapter<Coll>^ right);`  
  
 Inicializuje uložené popisovač s `right->` [collection_adapter::base (STL/CLR)](../dotnet/collection-adapter-base-stl-clr.md)`()`.  
  
 Konstruktor:  
  
 `collection_adapter(Coll^ collection);`  
  
 Inicializuje uložené popisovač s s `collection`.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_collection_adapter_construct.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d6x(6, L'x');   
  
// construct an empty container   
    Mycoll c1;   
    System::Console::WriteLine("base() null = {0}", c1.base() == nullptr);   
  
// construct with a handle   
    Mycoll c2(%d6x);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Mycoll c3(c2);   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    Mycoll c4(%c3);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
  
```  
  
```Output  
base() null = True  
 x x x x x x  
 x x x x x x  
 x x x x x x  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – nebo adaptér >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [collection_adapter – (STL/CLR)](../dotnet/collection-adapter-stl-clr.md)   
 [collection_adapter::Operator = (STL/CLR)](../dotnet/collection-adapter-operator-assign-stl-clr.md)