---
title: 'Postupy: převod typu .NET Collection na kontejner STL/CLR | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- STL/CLR, converting from .NET collections
- STL/CLR Containers [STL/CLR]
ms.assetid: bb927c48-78e8-4150-bd0b-787c651f4a87
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4dd67728773df86f9961fe54c7dd9e4a08ec743d
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50060946"
---
# <a name="how-to-convert-from-a-net-collection-to-a-stlclr-container"></a>Postupy: Převod typu .NET Collection na kontejner STL/CLR

Toto téma ukazuje, jak převod kolekce .NET na jejich ekvivalentní kontejnerů STL/CLR. Jako příklad vám ukážeme, jak převést .NET <xref:System.Collections.Generic.List%601> STL/CLR [vektoru](../dotnet/vector-stl-clr.md) a jak převést .NET <xref:System.Collections.Generic.Dictionary%602> STL/CLR [mapy](../dotnet/map-stl-clr.md), ale postup je podobný pro všechny kolekce a kontejnery .

### <a name="to-create-a-container-from-a-collection"></a>Vytvořte kontejner z kolekce

1. Převést celou kolekci, vytvořte kontejner STL/CLR a předat konstruktoru kolekce.

   První příklad ukazuje tento postup.

-OR-

1. Vytvořit obecný kontejneru STL/CLR vytvořením [collection_adapter –](../dotnet/collection-adapter-stl-clr.md) objektu. Tato třída šablony přijímá jako argument kolekce rozhraní .NET. Pokud chcete ověřit, která rozhraní jsou podporovány, naleznete v tématu [collection_adapter – (STL/CLR)](../dotnet/collection-adapter-stl-clr.md).

1. Zkopírujte obsah .NET collection na kontejner. To můžete udělat pomocí STL/CLR [algoritmus](../dotnet/algorithm-stl-clr.md), nebo podle iterace nad kolekcí .NET a vložením kopie každý prvek do kontejneru STL/CLR.

   Druhý příklad ukazuje tento postup.

## <a name="example"></a>Příklad

V tomto příkladu vytvoříme obecný <xref:System.Collections.Generic.List%601> a přidejte do ní 5 elementů. Pak vytvoříme `vector` pomocí konstruktoru, který přijímá <xref:System.Collections.Generic.IEnumerable%601> jako argument.

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

V tomto příkladu vytvoříme obecný <xref:System.Collections.Generic.Dictionary%602> a přidejte do ní 5 elementů. Pak vytvoříme `collection_adapter` zalomení <xref:System.Collections.Generic.Dictionary%602> jako jednoduchý kontejner STL/CLR. Nakonec vytvoříme `map` a zkopírujte obsah <xref:System.Collections.Generic.Dictionary%602> k `map` pomocí provádí iterace `collection_adapter`. Během tohoto procesu jsme vytvořit nový pár pomocí `make_pair` fungovat a vložit nový pár přímo do `map`.

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

[Referenční dokumentace knihoven STL/CLR](../dotnet/stl-clr-library-reference.md)<br/>
[adapter (STL/CLR)](../dotnet/adapter-stl-clr.md)<br/>
[Postupy: Převod kontejneru STL/CLR na kolekci .NET](../dotnet/how-to-convert-from-a-stl-clr-container-to-a-dotnet-collection.md)