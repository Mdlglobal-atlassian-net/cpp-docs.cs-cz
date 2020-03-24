---
title: 'Postupy: zlepšení výkonu pomocí obecných typů (C++/CLI)'
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- performance, C++
- C++, performance
- C++, generics
- generics [C++], performance
ms.assetid: f14a175b-301f-46cc-86e4-c82d35f9aa3e
ms.openlocfilehash: a460456a383fcb3eb81e17c1ad5817f790f3c399
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181938"
---
# <a name="how-to-improve-performance-with-generics-ccli"></a>Postupy: zlepšení výkonu pomocí obecných typů (C++/CLI)

S obecnými typy lze vytvořit opakovaně použitelný kód na základě parametru typu. Skutečný typ parametru typu je odložen, dokud se nevolá klientským kódem. Další informace o obecných typech naleznete v tématu [generické typy](generics-cpp-component-extensions.md).

Tento článek pojednává o tom, jak obecné typy mohou přispět ke zvýšení výkonu aplikace, která používá kolekce.

## <a name="example"></a>Příklad

.NET Framework obsahuje mnoho tříd kolekce v oboru názvů <xref:System.Collections?displayProperty=fullName>. Většina těchto kolekcí funguje na objektech typu <xref:System.Object?displayProperty=fullName>. To umožňuje, aby kolekce ukládaly libovolný typ, protože všechny typy v .NET Framework, dokonce i typ hodnoty, jsou odvozeny z <xref:System.Object?displayProperty=fullName>. Tento přístup ale obsahuje dvě nevýhody.

Za prvé, pokud kolekce ukládá typy hodnot, jako jsou například celá čísla, musí být hodnota zabalena před přidáním do kolekce a v případě, že je hodnota načtena z kolekce, nesmí být zabalena. Jedná se o náročné operace.

Za druhé neexistuje žádný způsob, jak určit, které typy lze do kolekce přidat. Pro přidání celého čísla a řetězce do stejné kolekce je naprosto právní, i když to pravděpodobně není zamýšlené. Proto, aby byl kód typově bezpečný, je nutné ověřit, že typ načtený z kolekce je skutečně očekávaný.

Následující příklad kódu ukazuje dvě hlavní nevýhody kolekce .NET Framework před obecnými typy.

```cpp
// perf_pre_generics.cpp
// compile with: /clr

using namespace System;
using namespace System::Collections;

int main()
{
    // This Stack can contain any type.
    Stack ^s = gcnew Stack();

    // Push an integer to the Stack.
    // A boxing operation is performed here.
    s->Push(7);

    // Push a String to the same Stack.
    // The Stack now contains two different data types.
    s->Push("Seven");

    // Pop the items off the Stack.
    // The item is returned as an Object, so a cast is
    // necessary to convert it to its proper type.
    while (s->Count> 0)
    {
        Object ^o = s->Pop();
        if (o->GetType() == Type::GetType("System.String"))
        {
            Console::WriteLine("Popped a String: {0}", (String ^)o);
        }
        else if (o->GetType() == Type::GetType("System.Int32"))
        {
            Console::WriteLine("Popped an int: {0}", (int)o);
        }
        else
        {
            Console::WriteLine("Popped an unknown type!");
        }
    }
}
```

```Output
Popped a String: Seven
Popped an int: 7
```

## <a name="example"></a>Příklad

Nový obor názvů <xref:System.Collections.Generic?displayProperty=fullName> obsahuje mnoho ze stejných kolekcí nalezených v oboru názvů <xref:System.Collections?displayProperty=fullName>, ale byly upraveny tak, aby přijímaly parametry obecného typu. Tím se eliminují dvě nevýhody neobecných kolekcí: zabalení a rozbalení typů hodnot a neschopnost určit typy, které mají být uloženy v kolekcích. Operace na těchto dvou kolekcích jsou identické. liší se pouze při vytváření instancí.

Porovnejte příklad uvedený výše s tímto příkladem, který používá obecnou kolekci <xref:System.Collections.Generic.Stack%601>. U rozsáhlých kolekcí, ke kterým dochází často, výkon tohoto příkladu bude mnohem větší než v předchozím příkladu.

```cpp
// perf_post_generics.cpp
// compile with: /clr

#using <System.dll>

using namespace System;
using namespace System::Collections::Generic;

int main()
{
    // This Stack can only contain integers.
    Stack<int> ^s = gcnew Stack<int>();

    // Push an integer to the Stack.
    // A boxing operation is performed here.
    s->Push(7);
    s->Push(14);

    // You can no longer push a String to the same Stack.
    // This will result in compile time error C2664.
    //s->Push("Seven");

    // Pop an item off the Stack.
    // The item is returned as the type of the collection, so no
    // casting is necessary and no unboxing is performed for
    // value types.
    int i = s->Pop();
    Console::WriteLine(i);

    // You can no longer retrieve a String from the Stack.
    // This will result in compile time error C2440.
    //String ^str = s->Pop();
}
```

```Output
14
```

## <a name="see-also"></a>Viz také

[Obecné typy](generics-cpp-component-extensions.md)
