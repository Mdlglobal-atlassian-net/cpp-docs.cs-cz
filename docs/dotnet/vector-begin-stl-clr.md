---
title: Vector::begin (STL/CLR) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::vector::begin
dev_langs:
- C++
helpviewer_keywords:
- begin member [STL/CLR]
ms.assetid: f9cdf854-0770-4334-a3dd-7f4d728a42bd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: ea81b63f6ebfd01634941c1e1c34706fb1ee8477
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33171474"
---
# <a name="vectorbegin-stlclr"></a>vector::begin (STL/CLR)
Určuje začátek řízené sekvence.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
iterator begin();  
```  
  
## <a name="remarks"></a>Poznámky  
 Členská funkce vrátí iterator náhodný přístup, který určuje první elementu v řízené sekvenci nebo právě přesahuje za konec prázdnou sekvencí. Můžete ji použít k získání iterátor, který označuje `current` začátku řízené sekvenci, ale jeho stav můžete změnit, pokud se změní délka řízené sekvenci.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_vector_begin.cpp   
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
  
// inspect first two items   
    cliext::vector<wchar_t>::iterator it = c1.begin();   
    System::Console::WriteLine("*begin() = {0}", *it);   
    System::Console::WriteLine("*++begin() = {0}", *++it);   
  
// alter first two items and reinspect   
    *--it = L'x';   
    *++it = L'y';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*begin() = a  
*++begin() = b  
 x y c  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / vektoru >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [vektor (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [Vector::end (STL/CLR)](../dotnet/vector-end-stl-clr.md)   
 [Vector::front (STL/CLR)](../dotnet/vector-front-stl-clr.md)   
 [vector::front_item (STL/CLR)](../dotnet/vector-front-item-stl-clr.md)