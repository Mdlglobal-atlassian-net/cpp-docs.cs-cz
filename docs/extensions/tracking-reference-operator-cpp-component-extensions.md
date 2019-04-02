---
title: Operátor sledovacího odkazu (C + +/ CLI a C + +/ CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- '%'
helpviewer_keywords:
- tracking references
- '% tracking reference [C++]'
ms.assetid: 142a7269-ab69-4b54-a6d7-833bef06228f
ms.openlocfilehash: c6fef4562545b03e212d0e4e58742a1209a6ab81
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58786915"
---
# <a name="tracking-reference-operator-ccli-and-ccx"></a>Operátor sledovacího odkazu (C + +/ CLI a C + +/ CX)

A *sledovací odkaz* (`%`) se chová jako běžná reference C++ (`&`) s tím rozdílem, že když objekt přiřazen sledovacímu odkazu, je zvýšen počet odkazů na objekt.

## <a name="all-platforms"></a>Všechny platformy

Sledovací odkaz má následující vlastnosti.

- Přiřazení objektu do sledovacího odkazu způsobí, že počet odkazů na objekt k navýšení.

- Nativní odkaz (`&`) je výsledkem v případě, že přestoupíte `*`. Sledovací odkaz (`%`) je výsledkem v případě, že přestoupíte `^`. Za předpokladu, že máte `%` na objekt, objekt zůstane zachován v paměti.

- Tečka (`.`) – operátor přístupu členů slouží k přístupu k člena objektu.

- Sledovací odkazy jsou platné pro typy hodnot a popisovače (například `String^`).

- Sledovací odkaz nelze přiřadit hodnotu null nebo **nullptr** hodnotu. Sledovací odkaz může být přeřazen jinému platnému objektu tolikrát, kolikrát podle potřeby.

- Sledovací odkaz nelze použít jako unární operátor převzetí adresy.

## <a name="windows-runtime"></a>prostředí Windows Runtime

Sledovací odkaz se chová jako referenční standard C++, s tím rozdílem, že je % počítáním referencí. Následující fragment kódu ukazuje, jak převod mezi % a ^ typy:

```cpp
Foo^ spFoo = ref new Foo();
Foo% srFoo = *spFoo;
Foo^ spFoo2 = %srFoo;
```

Následující příklad ukazuje, jak předat ^ funkci, která přebírá %.

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

V jazyce C + +/ CLI, můžete použít sledovací odkaz na popisovač Pokud svážete objekt typu CLR na haldě uvolňování paměti.

V modulu CLR, hodnota sady sledovacího odkazu proměnná se automaticky aktualizuje pokaždé, když uvolňování paměti přesune odkazovaný objekt.

Sledovací odkaz lze deklarovat pouze v zásobníku. Sledovací odkaz nemůže být členem třídy.

Není možné mít nativní odkaz C++ na objekt na haldě uvolňování paměti.

Další informace o sledování odkazů v jazyce C + +/ CLI, najdete v článku:

- [Postupy: Používání sledovacích odkazů v jazyce C++/CLI](../dotnet/how-to-use-tracking-references-in-cpp-cli.md)

### <a name="examples"></a>Příklady

Následující ukázka pro C + +/ CLI ukazuje, jak použít sledovací odkaz s nativními a spravovanými typy.

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

Následující ukázka pro C + +/ CLI ukazuje, jak vytvořit vazbu sledovací odkaz na pole.

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