---
title: Vector::front_item (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::vector::front_item
dev_langs: C++
helpviewer_keywords: front_item member [STL/CLR]
ms.assetid: 7db87868-3e54-4c67-a06b-01bcfff3128d
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8f55a2aaa679d17da27b4ff80bdd3a2342078707
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="vectorfrontitem-stlclr"></a>vector::front_item (STL/CLR)
Přístup k první prvek.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
property value_type front_item;  
```  
  
## <a name="remarks"></a>Poznámky  
 Vlastnost přistupuje k první prvek řízené sekvenci, která musí být neprázdný. Použijete jej číst nebo zapisovat první prvek, když víte, že existuje.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_vector_front_item.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first item   
    System::Console::WriteLine("front_item = {0}", c1.front_item);   
  
// alter first item and reinspect   
    c1.front_item = L'x';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
front_item = a  
 x b c  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / vektoru >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [vektor (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [Vector::back (STL/CLR)](../dotnet/vector-back-stl-clr.md)   
 [Vector::back_item (STL/CLR)](../dotnet/vector-back-item-stl-clr.md)   
 [Vector::front (STL/CLR)](../dotnet/vector-front-stl-clr.md)