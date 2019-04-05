---
title: 'Postupy: Zlepšení výkonu pomocí obecných typů (C + +/ CLI)'
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- performance, C++
- C++, performance
- C++, generics
- generics [C++], performance
ms.assetid: f14a175b-301f-46cc-86e4-c82d35f9aa3e
ms.openlocfilehash: 958da08716022bedaa8d0fe217814fa2bd86c065
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59038781"
---
# <a name="how-to-improve-performance-with-generics-ccli"></a>Postupy: Zlepšení výkonu pomocí obecných typů (C + +/ CLI)

Pomocí obecných typů můžete vytvořit opakovaně použitelný kód založený na parametr typu. Skutečný typ parametru typu je odloženo, dokud není volán kód klienta. Další informace o obecných typů viz [obecných typů](generics-cpp-component-extensions.md).

Tento článek popisuje, jak obecných typů vám může pomoct zvýšit výkon aplikace, která používá kolekce.

## <a name="example"></a>Příklad

Rozhraní .NET Framework je součástí mnoha kolekcí tříd v <xref:System.Collections?displayProperty=fullName> oboru názvů. Většina těchto kolekcí pracovat s objekty typu <xref:System.Object?displayProperty=fullName>. Díky tomu kolekce pro ukládání libovolného typu, protože všechny typy v rozhraní .NET Framework, dokonce i typy hodnot jsou odvozeny z <xref:System.Object?displayProperty=fullName>. Existují však dva nevýhod tohoto přístupu.

Nejprve Pokud kolekce je uložení typů hodnot, jako jsou celá čísla, hodnota musí být přidán do kolekce v poli a rozbalit, pokud je hodnota načteny z kolekce. Jedná se o nákladné operace.

Za druhé neexistuje žádný způsob, jak řídit typy, které lze přidat do kolekce. Je naprosto právní přidat celé číslo a řetězec do stejné kolekce, i když to je pravděpodobně není co byl určen. Proto aby váš kód je typově bezpečný, budete muset zkontrolujte, že typ načten z kolekce ve skutečnosti je, co byl očekáván.

Následující příklad kódu ukazuje dvě podstatné nevýhody kolekcemi rozhraní .NET Framework před obecných typů.

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

Nové <xref:System.Collections.Generic?displayProperty=fullName> obor názvů obsahuje mnoho nenašly ve stejné kolekce <xref:System.Collections?displayProperty=fullName> obor názvů, ale byly upraveny tak, aby přijímal parametry obecného typu. Tím se eliminují dvě nevýhody obecné kolekce: zabalení a rozbalení typů hodnot a neschopnost určit typy ukládaly do kolekce. Operace na dvě kolekce jsou identické; se liší pouze v tom, jak jsou vytvořena instance.

V příkladu uvedená výše v tomto příkladu, který používá obecného porovnání <xref:System.Collections.Generic.Stack%601> kolekce. V rozsáhlých kolekcí, které jsou často bude výkon v tomto příkladu výrazně větší než v předchozím příkladu.

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

## <a name="see-also"></a>Viz také:

[Obecné typy](generics-cpp-component-extensions.md)