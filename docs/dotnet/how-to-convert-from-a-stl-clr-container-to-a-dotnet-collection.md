---
title: "Postupy: převod kontejneru STL/CLR na typ .NET Collection | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
helpviewer_keywords:
- STL/CLR Containers [STL/CLR]
- STL/CLR, converting to .NET collections
ms.assetid: 70b2dfd9-869c-4e0f-9a29-b1ee0cb0d107
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 817f04af0f6d2c24296b5775a9863b8c34dccd30
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-convert-from-a-stlclr-container-to-a-net-collection"></a>Postupy: Převod kontejneru STL/CLR na typ .NET Collection
Toto téma ukazuje, jak převést kontejnery STL/CLR na jejich ekvivalentní kolekcí .NET. Jako příklad ukážeme, jak převést STL/CLR [vektoru](../dotnet/vector-stl-clr.md) k .NET <xref:System.Collections.Generic.ICollection%601> a jak převést STL/CLR [mapy](../dotnet/map-stl-clr.md) k .NET <xref:System.Collections.Generic.IDictionary%602>, ale postup je podobný pro všechny kolekce a kontejnery.  
  
### <a name="to-create-a-collection-from-a-container"></a>Můžete vytvořit kolekci z kontejneru  
  
1.  Použijte jednu z následujících metod:  
  
    -   Chcete-li převést součástí kontejner, zavolejte [make_collection –](../dotnet/make-collection-stl-clr.md) fungovat a předat begin iterator a end iterator kontejneru STL/CLR, které se mají zkopírovat do kolekce rozhraní .NET. Tato šablona funkce přebírá iterovat STL/CLR jako šablonu argumentu. V prvním příkladu ukazuje tuto metodu.  
  
    -   Převést celého kontejneru, přetypování kontejneru do příslušné kolekce rozhraní .NET nebo rozhraní kolekce. Druhý příklad ukazuje tuto metodu.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu vytvoříme STL/CLR `vector` a přidejte do ní 5 elementy. Poté vytvoříme typu .NET collection voláním `make_collection` funkce. Nakonec zobrazuje se obsah nově vytvořené kolekce.  
  
```  
// cliext_convert_vector_to_icollection.cpp  
// compile with: /clr  
  
#include <cliext/adapter>  
#include <cliext/vector>  
  
using namespace cliext;  
using namespace System;  
using namespace System::Collections::Generic;  
  
int main(array<System::String ^> ^args)  
{  
    cliext::vector<int> primeNumbersCont;  
    primeNumbersCont.push_back(2);  
    primeNumbersCont.push_back(3);  
    primeNumbersCont.push_back(5);  
    primeNumbersCont.push_back(7);  
    primeNumbersCont.push_back(11);  
  
    System::Collections::Generic::ICollection<int> ^iColl =  
        make_collection<cliext::vector<int>::iterator>(  
            primeNumbersCont.begin() + 1,  
            primeNumbersCont.end() - 1);  
  
    Console::WriteLine("The contents of the System::Collections::Generic::ICollection are:");  
    for each (int i in iColl)  
    {  
        Console::WriteLine(i);  
    }  
}  
```  
  
```Output  
The contents of the System::Collections::Generic::ICollection are:  
3  
5  
7  
```  
  
## <a name="example"></a>Příklad  
 V tomto příkladu vytvoříme STL/CLR `map` a přidejte do ní 5 elementy. Poté vytvoříme .NET <xref:System.Collections.Generic.IDictionary%602> a přiřaďte `map` přímo do ní. Nakonec zobrazuje se obsah nově vytvořené kolekce.  
  
```  
// cliext_convert_map_to_idictionary.cpp  
// compile with: /clr  
  
#include <cliext/adapter>  
#include <cliext/map>  
  
using namespace cliext;  
using namespace System;  
using namespace System::Collections::Generic;  
  
int main(array<System::String ^> ^args)  
{  
    cliext::map<float, int> ^aMap = gcnew cliext::map<float, int>;  
    aMap->insert(cliext::make_pair<float, int>(42.0, 42));  
    aMap->insert(cliext::make_pair<float, int>(13.0, 13));  
    aMap->insert(cliext::make_pair<float, int>(74.0, 74));  
    aMap->insert(cliext::make_pair<float, int>(22.0, 22));  
    aMap->insert(cliext::make_pair<float, int>(0.0, 0));  
  
    System::Collections::Generic::IDictionary<float, int> ^iDict = aMap;  
  
    Console::WriteLine("The contents of the IDictionary are:");  
    for each (KeyValuePair<float, int> ^kvp in iDict)  
    {  
        Console::WriteLine("Key: {0:F} Value: {1}", kvp->Key, kvp->Value);  
    }  
}  
```  
  
```Output  
The contents of the IDictionary are:  
Key: 0.00 Value: 0  
Key: 13.00 Value: 13  
Key: 22.00 Value: 22  
Key: 42.00 Value: 42  
Key: 74.00 Value: 74  
```  
  
## <a name="see-also"></a>Viz také  
 [Referenční příručka knihovny STL/CLR](../dotnet/stl-clr-library-reference.md)   
 [Postupy: převod typu .NET Collection na kontejner STL/CLR](../dotnet/how-to-convert-from-a-dotnet-collection-to-a-stl-clr-container.md)   
 [range_adapter – (STL/CLR)](../dotnet/range-adapter-stl-clr.md)