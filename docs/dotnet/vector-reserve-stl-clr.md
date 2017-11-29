---
title: Vector::Reserve (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::vector::reserve
dev_langs: C++
helpviewer_keywords: reserve member [STL/CLR]
ms.assetid: d1d5ede9-9628-4b55-95ec-f087a57205f2
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3e84ba7b9d59e1c15c2d01ecc7cc73eab9209c34
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="vectorreserve-stlclr"></a>vector::reserve (STL/CLR)
Zajišťuje růstu minimální kapacitu kontejneru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void reserve(size_type count);  
```  
  
#### <a name="parameters"></a>Parametry  
 count  
 Nové minimální kapacitu kontejneru.  
  
## <a name="remarks"></a>Poznámky  
 Členská funkce zajišťuje, že `capacity()` od nynějška vrátí alespoň `count`. Použijte k zajištění, že kontejner nemusí znovu přidělte úložiště pro řízené sekvenci dokud se zvětšil zadané velikosti.  
  
## <a name="example"></a>Příklad  
  
```  
// cliext_vector_reserve.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1.at(i));   
    System::Console::WriteLine();   
  
// increase capacity   
    cliext::vector<wchar_t>::size_type cap = c1.capacity();   
    System::Console::WriteLine("capacity() = {0}, ok = {1}",   
        cap, c1.size() <= cap);   
    c1.reserve(cap + 5);   
    System::Console::WriteLine("capacity() = {0}, ok = {1}",   
        c1.capacity(), cap + 5 <= c1.capacity());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
capacity() = 4, ok = True  
capacity() = 9, ok = True  
```  
  
## <a name="description"></a>Popis  
 Všimněte si, že skutečné kapacity může lišit od zde zobrazených hodnot, tak dlouho i všechny `ok` testy sestavy hodnotu true.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / vektoru >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [vektor (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [Vector::Capacity (STL/CLR)](../dotnet/vector-capacity-stl-clr.md)   
 [Vector::Resize (STL/CLR)](../dotnet/vector-resize-stl-clr.md)