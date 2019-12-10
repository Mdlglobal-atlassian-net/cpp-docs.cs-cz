---
title: 'Postupy: Převod kontejneru STL/CLR na typ .NET Collection'
ms.date: 11/04/2016
helpviewer_keywords:
- STL/CLR Containers [STL/CLR]
- STL/CLR, converting to .NET collections
ms.assetid: 70b2dfd9-869c-4e0f-9a29-b1ee0cb0d107
ms.openlocfilehash: f7539b10ca6c503aede61d19de3d14fb9dcee8be
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988515"
---
# <a name="how-to-convert-from-a-stlclr-container-to-a-net-collection"></a>Postupy: Převod kontejneru STL/CLR na typ .NET Collection

Toto téma ukazuje, jak převést kontejnery STL/CLR na jejich ekvivalentní kolekce .NET. Jako příklad ukazujeme, jak převést [vektor](../dotnet/vector-stl-clr.md) STL/clr na <xref:System.Collections.Generic.ICollection%601> .NET a jak převést [mapu](../dotnet/map-stl-clr.md) stl/CLR na <xref:System.Collections.Generic.IDictionary%602>.NET, ale postup je podobný pro všechny kolekce a kontejnery.

### <a name="to-create-a-collection-from-a-container"></a>Vytvoření kolekce z kontejneru

1. Použijte jednu z následujících metod:

   - Chcete-li převést část kontejneru, zavolejte funkci [make_collection](../dotnet/make-collection-stl-clr.md) a předejte iterátor a koncový ITERÁTOR kontejneru STL/CLR ke zkopírování do kolekce rozhraní .NET. Tato funkce šablony přijímá iterátor STL/CLR jako argument šablony. První příklad ukazuje tuto metodu.

   - Chcete-li převést celý kontejner, přetypujte kontejner na příslušné rozhraní kolekce .NET nebo kolekci rozhraní. Druhý příklad ukazuje tuto metodu.

## <a name="example"></a>Příklad

V tomto příkladu vytvoříme `vector` STL/CLR a přidáte do ní 5 prvků. Pak vytvoříme kolekci .NET voláním funkce `make_collection`. Nakonec zobrazíme obsah nově vytvořené kolekce.

```cpp
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

V tomto příkladu vytvoříme `map` STL/CLR a přidáte do ní 5 prvků. Pak vytvoříme <xref:System.Collections.Generic.IDictionary%602> .NET a přiřadíme k němu `map` přímo. Nakonec zobrazíme obsah nově vytvořené kolekce.

```cpp
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

## <a name="see-also"></a>Viz také:

[Referenční dokumentace knihoven STL/CLR](../dotnet/stl-clr-library-reference.md)<br/>
[Postupy: Převod kolekce .NET na kontejner STL/CLR](../dotnet/how-to-convert-from-a-dotnet-collection-to-a-stl-clr-container.md)<br/>
[range_adapter (STL/CLR)](../dotnet/range-adapter-stl-clr.md)
