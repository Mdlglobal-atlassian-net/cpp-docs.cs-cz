---
title: 'Postupy: vystavení kontejneru STL/CLR ze sestavení | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- STL/CLR Containers [STL/CLR]
- STL/CLR, cross-assembly issues
ms.assetid: 87efb41b-3db3-4498-a2e7-f3ef8a99f04d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b4e2c9195557369fba380518a06fa08be7daeb1a
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44317955"
---
# <a name="how-to-expose-an-stlclr-container-from-an-assembly"></a>Postupy: Vystavení kontejneru STL/CLR ze sestavení

STL/CLR – kontejnery, jako `list` a `map` jsou implementovány jako šablony referenčních tříd. Protože instance šablony jazyka C++ se vytvářejí v době kompilace, dvě šablony třídy, které mají přesně stejnou signaturu, ale jsou v různých sestaveních jsou ve skutečnosti různé typy. To znamená, že šablony třídy nelze použít přes hranice sestavení.

Chcete-li umožní sdílení mezi sestaveními, kontejnerů STL/CLR implementovat obecné rozhraní <xref:System.Collections.Generic.ICollection%601>. Pomocí této obecné rozhraní přístupné všechny jazyky, které podporují obecných typů, včetně jazyka C++, C# a Visual Basic, kontejnerů STL/CLR.

V tomto tématu se dozvíte, jak zobrazit prvky několika kontejnerů STL/CLR napsané v sestavení C++ s názvem `StlClrClassLibrary`. Ukážeme dvě sestavení pro přístup k `StlClrClassLibrary`. První sestavení je napsané v jazyce C++ a druhý v jazyce C#.

Pokud jsou obě sestavení napsaný v jazyce C++, dostanete obecné rozhraní kontejner pomocí jeho `generic_container` typedef. Například, pokud máte kontejner typu `cliext::vector<int>`, pak je její obecná rozhraní: `cliext::vector<int>::generic_container`. Podobně můžete získat iterátor nad její obecná rozhraní s použitím `generic_iterator` definice typedef, jako v: `cliext::vector<int>::generic_iterator`.

Protože tyto funkce TypeDef jsou deklarovány v souborech hlaviček jazyka C++, nelze je použít sestavení, které jsou napsané v jiných jazycích. Proto se pro přístup k obecné rozhraní pro `cliext::vector<int>` v jazyce C# nebo jiném jazyce .NET, použijte `System.Collections.Generic.ICollection<int>`. Použít k iteraci přes tuto kolekci, `foreach` smyčky.

V následující tabulce jsou uvedeny obecné rozhraní, která implementuje každého kontejneru STL/CLR:

|Kontejner STL/CLR|Obecná rozhraní|
|------------------------|-----------------------|
|`deque<T>`|`ICollection<T>`|
|`hash_map<K, V>`|`IDictionary<K, V>`|
|`hash_multimap<K, V>`|`IDictionary<K, V>`|
|`hash_multiset<T>`|`ICollection<T>`|
|`hash_set<T>`|`ICollection<T>`|
|`list<T>`|`ICollection<T>`|
|`map<K, V>`|`IDictionary<K, V>`|
|`multimap<K, V>`|`IDictionary<K, V>`|
|`multiset<T>`|`ICollection<T>`|
|`set<T>`|`ICollection<T>`|
|`vector<T>`|`ICollection<T>`|

> [!NOTE]
> Vzhledem k tomu, `queue`, `priority_queue`, a `stack` kontejnery nepodporují iterátory, neprovádějte implementaci obecná rozhraní a nemůže být využívaných mezi sestaveními.

## <a name="example-1"></a>Příklad 1

### <a name="description"></a>Popis

V tomto příkladu jsme deklarovat třídu jazyka C++, který obsahuje privátní členská data STL/CLR. Pak můžeme deklarovat veřejné metody pro udělení přístupu k soukromé kolekce třídy. Provedeme to dvěma různými způsoby, jeden pro klienty jazyka C++ a jeden pro ostatní klienty .NET.

### <a name="code"></a>Kód

```cpp
// StlClrClassLibrary.h
#pragma once

#include <cliext/deque>
#include <cliext/list>
#include <cliext/map>
#include <cliext/set>
#include <cliext/stack>
#include <cliext/vector>

using namespace System;
using namespace System::Collections::Generic;
using namespace cliext;

namespace StlClrClassLibrary {

    public ref class StlClrClass
    {
    public:
        StlClrClass();

        // These methods can be called by a C++ class
        // in another assembly to get access to the
        // private STL/CLR types defined below.
        deque<wchar_t>::generic_container ^GetDequeCpp();
        list<float>::generic_container ^GetListCpp();
        map<int, String ^>::generic_container ^GetMapCpp();
        set<double>::generic_container ^GetSetCpp();
        vector<int>::generic_container ^GetVectorCpp();

        // These methods can be called by a non-C++ class
        // in another assembly to get access to the
        // private STL/CLR types defined below.
        ICollection<wchar_t> ^GetDequeCs();
        ICollection<float> ^GetListCs();
        IDictionary<int, String ^> ^GetMapCs();
        ICollection<double> ^GetSetCs();
        ICollection<int> ^GetVectorCs();

    private:
        deque<wchar_t> ^aDeque;
        list<float> ^aList;
        map<int, String ^> ^aMap;
        set<double> ^aSet;
        vector<int> ^aVector;
    };
}
```

## <a name="example-2"></a>Příklad 2

### <a name="description"></a>Popis

V tomto příkladu jsme implementace třídy deklarované v příkladu 1. Aby klientům použití této třídy knihovny, nástroj manifest používáme **mt.exe** vložit soubor manifestu do knihovny DLL. Podrobnosti najdete v tématu v komentářích ke kódu.

Další informace o manifestu nástroje a sestavení vedle sebe, naleznete v tématu [vytváření izolovaných aplikací C/C++ a sestavení vedle sebe](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md).

### <a name="code"></a>Kód

```cpp
// StlClrClassLibrary.cpp
// compile with: /clr /LD /link /manifest
// post-build command: (attrib -r StlClrClassLibrary.dll & mt /manifest StlClrClassLibrary.dll.manifest /outputresource:StlClrClassLibrary.dll;#2 & attrib +r StlClrClassLibrary.dll)

#include "StlClrClassLibrary.h"

namespace StlClrClassLibrary
{
    StlClrClass::StlClrClass()
    {
        aDeque = gcnew deque<wchar_t>();
        aDeque->push_back(L'a');
        aDeque->push_back(L'b');

        aList = gcnew list<float>();
        aList->push_back(3.14159f);
        aList->push_back(2.71828f);

        aMap = gcnew map<int, String ^>();
        aMap[0] = "Hello";
        aMap[1] = "World";

        aSet = gcnew set<double>();
        aSet->insert(3.14159);
        aSet->insert(2.71828);

        aVector = gcnew vector<int>();
        aVector->push_back(10);
        aVector->push_back(20);
    }

    deque<wchar_t>::generic_container ^StlClrClass::GetDequeCpp()
    {
        return aDeque;
    }

    list<float>::generic_container ^StlClrClass::GetListCpp()
    {
        return aList;
    }

    map<int, String ^>::generic_container ^StlClrClass::GetMapCpp()
    {
        return aMap;
    }

    set<double>::generic_container ^StlClrClass::GetSetCpp()
    {
        return aSet;
    }

    vector<int>::generic_container ^StlClrClass::GetVectorCpp()
    {
        return aVector;
    }

    ICollection<wchar_t> ^StlClrClass::GetDequeCs()
    {
        return aDeque;
    }

    ICollection<float> ^StlClrClass::GetListCs()
    {
        return aList;
    }

    IDictionary<int, String ^> ^StlClrClass::GetMapCs()
    {
        return aMap;
    }

    ICollection<double> ^StlClrClass::GetSetCs()
    {
        return aSet;
    }

    ICollection<int> ^StlClrClass::GetVectorCs()
    {
        return aVector;
    }
}
```

## <a name="example-3"></a>Příklad 3

### <a name="description"></a>Popis

V tomto příkladu vytvoříme C++ klienta, který používá knihovnu tříd vytvoří v příklady 1 a 2. Tento klient použije `generic_container` – definice TypeDef kontejnerů STL/CLR k iteraci přes kontejnery a zobrazit jejich obsah.

### <a name="code"></a>Kód

```cpp
// CppConsoleApp.cpp
// compile with: /clr /FUStlClrClassLibrary.dll

#include <cliext/deque>
#include <cliext/list>
#include <cliext/map>
#include <cliext/set>
#include <cliext/vector>

using namespace System;
using namespace StlClrClassLibrary;
using namespace cliext;

int main(array<System::String ^> ^args)
{
    StlClrClass theClass;

    Console::WriteLine("cliext::deque contents:");
    deque<wchar_t>::generic_container ^aDeque = theClass.GetDequeCpp();
    for each (wchar_t wc in aDeque)
    {
        Console::WriteLine(wc);
    }
    Console::WriteLine();

    Console::WriteLine("cliext::list contents:");
    list<float>::generic_container ^aList = theClass.GetListCpp();
    for each (float f in aList)
    {
        Console::WriteLine(f);
    }
    Console::WriteLine();

    Console::WriteLine("cliext::map contents:");
    map<int, String ^>::generic_container ^aMap = theClass.GetMapCpp();
    for each (map<int, String ^>::value_type rp in aMap)
    {
        Console::WriteLine("{0} {1}", rp->first, rp->second);
    }
    Console::WriteLine();

    Console::WriteLine("cliext::set contents:");
    set<double>::generic_container ^aSet = theClass.GetSetCpp();
    for each (double d in aSet)
    {
        Console::WriteLine(d);
    }
    Console::WriteLine();

    Console::WriteLine("cliext::vector contents:");
    vector<int>::generic_container ^aVector = theClass.GetVectorCpp();
    for each (int i in aVector)
    {
        Console::WriteLine(i);
    }
    Console::WriteLine();

    return 0;
}
```

### <a name="output"></a>Výstup

```Output
cliext::deque contents:
a
b

cliext::list contents:
3.14159
2.71828

cliext::map contents:
0 Hello
1 World

cliext::set contents:
2.71828
3.14159

cliext::vector contents:
10
20
```

## <a name="example-4"></a>Příklad 4:

### <a name="description"></a>Popis

V tomto příkladu vytvoříme klienta jazyka C#, který používá knihovnu tříd vytvoří v příklady 1 a 2. Tento klient použije <xref:System.Collections.Generic.ICollection%601> metody kontejnerů STL/CLR k iteraci přes kontejnery a zobrazit jejich obsah.

### <a name="code"></a>Kód

```csharp
// CsConsoleApp.cs
// compile with: /r:Microsoft.VisualC.STLCLR.dll /r:StlClrClassLibrary.dll /r:System.dll

using System;
using System.Collections.Generic;
using StlClrClassLibrary;
using cliext;

namespace CsConsoleApp
{
    class Program
    {
        static int Main(string[] args)
        {
            StlClrClass theClass = new StlClrClass();

            Console.WriteLine("cliext::deque contents:");
            ICollection<char> iCollChar = theClass.GetDequeCs();
            foreach (char c in iCollChar)
            {
                Console.WriteLine(c);
            }
            Console.WriteLine();

            Console.WriteLine("cliext::list contents:");
            ICollection<float> iCollFloat = theClass.GetListCs();
            foreach (float f in iCollFloat)
            {
                Console.WriteLine(f);
            }
            Console.WriteLine();

            Console.WriteLine("cliext::map contents:");
            IDictionary<int, string> iDict = theClass.GetMapCs();
            foreach (KeyValuePair<int, string> kvp in iDict)
            {
                Console.WriteLine("{0} {1}", kvp.Key, kvp.Value);
            }
            Console.WriteLine();

            Console.WriteLine("cliext::set contents:");
            ICollection<double> iCollDouble = theClass.GetSetCs();
            foreach (double d in iCollDouble)
            {
                Console.WriteLine(d);
            }
            Console.WriteLine();

            Console.WriteLine("cliext::vector contents:");
            ICollection<int> iCollInt = theClass.GetVectorCs();
            foreach (int i in iCollInt)
            {
                Console.WriteLine(i);
            }
            Console.WriteLine();

            return 0;
        }
    }
}
```

### <a name="output"></a>Výstup

```Output
cliext::deque contents:
a
b

cliext::list contents:
3.14159
2.71828

cliext::map contents:
0 Hello
1 World

cliext::set contents:
2.71828
3.14159

cliext::vector contents:
10
20
```

## <a name="see-also"></a>Viz také

[Referenční dokumentace knihoven STL/CLR](../dotnet/stl-clr-library-reference.md)