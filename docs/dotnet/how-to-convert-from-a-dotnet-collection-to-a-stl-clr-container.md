---
title: 'Postupy: převod typu .NET Collection na kontejner STL/CLR | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- STL/CLR, converting from .NET collections
- STL/CLR Containers [STL/CLR]
ms.assetid: bb927c48-78e8-4150-bd0b-787c651f4a87
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6366dd10e60d8f2ea60811f74ba2b2e10457dd84
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-convert-from-a-net-collection-to-a-stlclr-container"></a>Postupy: Převod typu .NET Collection na kontejner STL/CLR
Toto téma ukazuje, jak převést kolekcí .NET na jejich ekvivalentní STL/CLR – kontejnery. Jako příklad ukážeme, jak převést .NET <xref:System.Collections.Generic.List%601> k STL/CLR [vektoru](../dotnet/vector-stl-clr.md) a jak převést rozhraní .NET <xref:System.Collections.Generic.Dictionary%602> k STL/CLR [mapy](../dotnet/map-stl-clr.md), ale postup je podobný pro všechny kolekce a kontejnery .  
  
### <a name="to-create-a-container-from-a-collection"></a>Chcete-li vytvořit kontejner z kolekce  
  
1.  Převést celou kolekci, vytvořte kontejner STL/CLR a předejte kolekce do konstruktoru.  
  
     V prvním příkladu ukazuje tento postup.  
  
 -NEBO-  
  
1.  Vytvořte kontejner STL/CLR obecné tak, že vytvoříte [collection_adapter –](../dotnet/collection-adapter-stl-clr.md) objektu. Tato třída šablony vezme kolekci rozhraní .NET jako argument. Pokud chcete ověřit, která rozhraní jsou podporované, najdete v části [collection_adapter – (STL/CLR)](../dotnet/collection-adapter-stl-clr.md).  
  
2.  Zkopírujte obsah .NET collection na kontejner. Tento krok můžete provést pomocí STL/CLR [algoritmus](../dotnet/algorithm-stl-clr.md), nebo podle iterace nad kolekcí .NET a vkládání kopii každého elementu do kontejneru STL/CLR.  
  
     Druhý příklad ukazuje, tento postup.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu vytvoříme obecný <xref:System.Collections.Generic.List%601> a přidejte do ní 5 elementy. Poté vytvoříme `vector` pomocí konstruktor, který přebírá <xref:System.Collections.Generic.IEnumerable%601> jako argument.  
  
```  
// cliext_convert_list_to_vector.cpp  
// compile with: /clr  
  
#include <cliext/adapter>  
#include <cliext/algorithm>  
#include <cliext/vector>  
  
using namespace System;  
using namespace System::Collections;  
using namespace System::Collections::Generic;  
  
int main(array<System::String ^> ^args)  
{  
    List<int> ^primeNumbersColl = gcnew List<int>();  
    primeNumbersColl->Add(2);  
    primeNumbersColl->Add(3);  
    primeNumbersColl->Add(5);  
    primeNumbersColl->Add(7);  
    primeNumbersColl->Add(11);  
  
    cliext::vector<int> ^primeNumbersCont =  
        gcnew cliext::vector<int>(primeNumbersColl);  
  
    Console::WriteLine("The contents of the cliext::vector are:");  
    cliext::vector<int>::const_iterator it;  
    for (it = primeNumbersCont->begin(); it != primeNumbersCont->end(); it++)  
    {  
        Console::WriteLine(*it);  
    }  
}  
```  
  
```Output  
The contents of the cliext::vector are:  
2  
3  
5  
7  
11  
```  
  
## <a name="example"></a>Příklad  
 V tomto příkladu vytvoříme obecný <xref:System.Collections.Generic.Dictionary%602> a přidejte do ní 5 elementy. Poté vytvoříme `collection_adapter` zabalit <xref:System.Collections.Generic.Dictionary%602> jako jednoduchý kontejneru STL/CLR. Nakonec se nám vytvořit `map` a zkopírujte obsah <xref:System.Collections.Generic.Dictionary%602> k `map` podle iterování přes `collection_adapter`. Během tohoto procesu, můžeme vytvořit nový pár pomocí `make_pair` funkce a vložit nový pár přímo do `map`.  
  
```  
// cliext_convert_dictionary_to_map.cpp  
// compile with: /clr  
  
#include <cliext/adapter>  
#include <cliext/algorithm>  
#include <cliext/map>  
  
using namespace System;  
using namespace System::Collections;  
using namespace System::Collections::Generic;  
  
int main(array<System::String ^> ^args)  
{  
    System::Collections::Generic::Dictionary<float, int> ^dict =  
        gcnew System::Collections::Generic::Dictionary<float, int>();  
    dict->Add(42.0, 42);  
    dict->Add(13.0, 13);  
    dict->Add(74.0, 74);  
    dict->Add(22.0, 22);  
    dict->Add(0.0, 0);  
  
    cliext::collection_adapter<System::Collections::Generic::IDictionary<float, int>> dictAdapter(dict);  
    cliext::map<float, int> aMap;  
    for each (KeyValuePair<float, int> ^kvp in dictAdapter)  
    {  
        cliext::pair<float, int> aPair = cliext::make_pair(kvp->Key, kvp->Value);  
        aMap.insert(aPair);  
    }  
  
    Console::WriteLine("The contents of the cliext::map are:");  
    cliext::map<float, int>::const_iterator it;  
    for (it = aMap.begin(); it != aMap.end(); it++)  
    {  
        Console::WriteLine("Key: {0:F} Value: {1}", it->first, it->second);  
    }  
}  
```  
  
```Output  
The contents of the cliext::map are:  
Key: 0.00 Value: 0  
Key: 13.00 Value: 13  
Key: 22.00 Value: 22  
Key: 42.00 Value: 42  
Key: 74.00 Value: 74  
```  
  
## <a name="see-also"></a>Viz také  
 [Referenční příručka knihovny STL/CLR](../dotnet/stl-clr-library-reference.md)   
 [adaptér (STL/CLR)](../dotnet/adapter-stl-clr.md)   
 [Postupy: Převod kontejneru STL/CLR na kolekci .NET](../dotnet/how-to-convert-from-a-stl-clr-container-to-a-dotnet-collection.md)