---
title: Operátor sledovacího odkazu (C++/CLI a C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- '%'
helpviewer_keywords:
- tracking references
- '% tracking reference [C++]'
ms.assetid: 142a7269-ab69-4b54-a6d7-833bef06228f
ms.openlocfilehash: ccd31b3e334dc5a4cd2e48b94c9dbe85cf13c16b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368240"
---
# <a name="tracking-reference-operator-ccli-and-ccx"></a>Operátor sledovacího odkazu (C++/CLI a C++/CX)

Odkaz *na* `%`sledování ( ) se chová jako`&`běžný odkaz jazyka C++ ( ) s tím rozdílem, že když je objekt přiřazen k odkazu na sledování, počet odkazů na objekt se zintácí.

## <a name="all-platforms"></a>Všechny platformy

Odkaz na sledování má následující charakteristiky.

- Přiřazení objektu k odkazu sledování způsobí zvýšení počtu odkazů objektu.

- Nativní odkaz`&`( ) je výsledek `*`při dereference . Odkaz na`%`sledování ( ) je výsledek `^`při dereferenci . Tak dlouho, dokud `%` máte objekt, objekt zůstane naživu v paměti.

- Operátor přístupu`.`k členu tečka ( ) slouží k přístupu k členu objektu.

- Sledování odkazy jsou platné pro typy hodnot `String^`a popisovače (například).

- Odkaz na sledování nelze přiřadit hodnotu null nebo **nullptr.** Odkaz na sledování může být znovu přiřazen jinému platnému objektu tolikrát, kolikrát je to požadováno.

- Odkaz na sledování nelze použít jako operátor unární ho dohledu.

## <a name="windows-runtime"></a>prostředí Windows Runtime

Odkaz sledování se chová jako standardní odkaz jazyka C++ s tím rozdílem, že % se počítá s odkazem. Následující úryvek ukazuje, jak převést mezi % a ^ typy:

```cpp
Foo^ spFoo = ref new Foo();
Foo% srFoo = *spFoo;
Foo^ spFoo2 = %srFoo;
```

Následující příklad ukazuje, jak předat ^ do funkce, která trvá %.

```cpp
ref class Foo sealed {};

    // internal or private
    void UseFooHelper(Foo% f)
    {
        auto x = %f;
    }

    // public method on ABI boundary
    void UseFoo(Foo^ f)
    {
        if (f != nullptr) { UseFooHelper(*f); }
    }
```

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

V jazyce C++/CLI můžete použít odkaz na sledování popisovače, když se vážete na objekt typu CLR na haldě uvolněné.

V CLR hodnota referenční proměnné sledování se aktualizuje automaticky vždy, když systém uvolňování paměti přesune odkazovaný objekt.

Sledování odkaz lze deklarovat pouze v zásobníku. Odkaz na sledování nemůže být členem třídy.

Není možné mít nativní C++ odkaz na objekt na haldě uvolňování paměti.

Další informace o sledování odkazů v jazyce C++/CLI naleznete v tématu:

- [Postupy: Používání sledovacích odkazů v jazyce C++/CLI](../dotnet/how-to-use-tracking-references-in-cpp-cli.md)

### <a name="examples"></a>Příklady

Následující ukázka pro C++/CLI ukazuje, jak používat odkaz na sledování s nativními a spravovanými typy.

```cpp
// tracking_reference_1.cpp
// compile with: /clr
ref class MyClass {
public:
   int i;
};

value struct MyStruct {
   int k;
};

int main() {
   MyClass ^ x = ref new MyClass;
   MyClass ^% y = x;   // tracking reference handle to reference object

   int %ti = x->i;   // tracking reference to member of reference type

   int j = 0;
   int %tj = j;   // tracking reference to object on the stack

   int * pi = new int[2];
   int % ti2 = pi[0];   // tracking reference to object on native heap

   int *% tpi = pi;   // tracking reference to native pointer

   MyStruct ^ x2 = ref new MyStruct;
   MyStruct ^% y2 = x2;   // tracking reference to value object

   MyStruct z;
   int %tk = z.k;   // tracking reference to member of value type

   delete[] pi;
}
```

Následující ukázka pro C++/CLI ukazuje, jak svázat sledovací odkaz na pole.

```cpp
// tracking_reference_2.cpp
// compile with: /clr
using namespace System;

int main() {
   array<int> ^ a = ref new array<Int32>(5);
   a[0] = 21;
   Console::WriteLine(a[0]);
   array<int> ^% arr = a;
   arr[0] = 222;
   Console::WriteLine(a[0]);
}
```

```Output
21
222
```
