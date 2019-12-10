---
title: 'Postupy: Převod typu .NET Collection na kontejner STL/CLR'
ms.date: 11/04/2016
helpviewer_keywords:
- STL/CLR, converting from .NET collections
- STL/CLR Containers [STL/CLR]
ms.assetid: bb927c48-78e8-4150-bd0b-787c651f4a87
ms.openlocfilehash: 156b4162f742915939ebdfaec6a84d77afaad8cd
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988278"
---
# <a name="how-to-convert-from-a-net-collection-to-a-stlclr-container"></a>Postupy: Převod typu .NET Collection na kontejner STL/CLR

Toto téma ukazuje, jak převést kolekce .NET na jejich ekvivalentní kontejnery STL/CLR. Jako příklad ukazujeme, jak převést <xref:System.Collections.Generic.List%601> .NET na [vektor](../dotnet/vector-stl-clr.md) STL/CLR a jak převést rozhraní .NET <xref:System.Collections.Generic.Dictionary%602> na [mapu](../dotnet/map-stl-clr.md)STL/CLR, ale postup je podobný pro všechny kolekce a kontejnery.

### <a name="to-create-a-container-from-a-collection"></a>Vytvoření kontejneru z kolekce

1. Chcete-li převést celou kolekci, vytvořte kontejner STL/CLR a předejte kolekci do konstruktoru.

   První příklad ukazuje tento postup.

-OR-

1. Vytvořte obecný kontejner STL/CLR vytvořením objektu [collection_adapter](../dotnet/collection-adapter-stl-clr.md) . Tato třída šablony přebírá rozhraní .NET Collection jako argument. Chcete-li ověřit, která rozhraní jsou podporována, přečtěte si téma [collection_adapter (STL/CLR)](../dotnet/collection-adapter-stl-clr.md).

1. Zkopírujte obsah kolekce .NET do kontejneru. To lze provést pomocí [algoritmu](../dotnet/algorithm-stl-clr.md)STL/CLR nebo pomocí iterace kolekce .NET a vložením kopie každého prvku do kontejneru STL/CLR.

   Druhý příklad ukazuje tento postup.

## <a name="example"></a>Příklad

V tomto příkladu vytvoříme obecné <xref:System.Collections.Generic.List%601> a do něj přidáte 5 prvků. Pak vytvoříme `vector` pomocí konstruktoru, který jako argument přijímá <xref:System.Collections.Generic.IEnumerable%601>.

```cpp
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

V tomto příkladu vytvoříme obecné <xref:System.Collections.Generic.Dictionary%602> a do něj přidáte 5 prvků. Pak vytvoříme `collection_adapter` k zabalení <xref:System.Collections.Generic.Dictionary%602> jako jednoduchého kontejneru STL/CLR. Nakonec vytvoříme `map` a zkopírujte obsah <xref:System.Collections.Generic.Dictionary%602> do `map` tak, že na `collection_adapter`provedete iteraci. Během tohoto procesu vytvoříme novou dvojici pomocí funkce `make_pair` a vložíte dvojici New přímo do `map`.

```cpp
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

## <a name="see-also"></a>Viz také:

[Referenční dokumentace knihoven STL/CLR](../dotnet/stl-clr-library-reference.md)<br/>
[adapter (STL/CLR)](../dotnet/adapter-stl-clr.md)<br/>
[Postupy: Převod kontejneru STL/CLR na kolekci .NET](../dotnet/how-to-convert-from-a-stl-clr-container-to-a-dotnet-collection.md)
