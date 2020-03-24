---
title: Operátor sledovacího odkazuC++(/CLI C++a/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- '%'
helpviewer_keywords:
- tracking references
- '% tracking reference [C++]'
ms.assetid: 142a7269-ab69-4b54-a6d7-833bef06228f
ms.openlocfilehash: ab1b11d3f8d3416a6e9ed345085d63ce86d56010
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181782"
---
# <a name="tracking-reference-operator-ccli-and-ccx"></a>Operátor sledovacího odkazuC++(/CLI C++a/CX)

*Sledovací odkaz* (`%`) se chová jako běžný C++ odkaz (`&`) s tím rozdílem, že je-li objekt přiřazen k sledovacímu odkazu, je zvýšen počet odkazů na objekt.

## <a name="all-platforms"></a>Všechny platformy

Sledovací odkaz má následující vlastnosti.

- Přiřazení objektu na odkaz sledování způsobí zvýšení počtu odkazů na objekt.

- Nativní odkaz (`&`) je výsledkem při odkázání na `*`. Odkaz sledování (`%`) je výsledkem při odkázání na `^`. Dokud máte `%` objektu, objekt zůstane aktivní v paměti.

- Operátor přístupu člena tečky (`.`) se používá pro přístup k členu objektu.

- Sledovací odkazy jsou platné pro typy hodnot a obslužné rutiny (například `String^`).

- Sledovacímu odkazu nelze přiřadit hodnotu null nebo **nullptr** . Odkaz sledování se může znovu přiřadit k jinému platnému objektu, kolikrát je potřeba.

- Sledovací odkaz se nedá použít jako unární operátor přijetí-adresy.

## <a name="windows-runtime"></a>prostředí Windows Runtime

Sledovací odkaz se chová jako standardní C++ odkaz s tím rozdílem, že% je odkazem na vypočítané. Následující fragment kódu ukazuje, jak převést mezi typy% a ^:

```cpp
Foo^ spFoo = ref new Foo();
Foo% srFoo = *spFoo;
Foo^ spFoo2 = %srFoo;
```

Následující příklad ukazuje, jak předat ^ do funkce, která přijímá%.

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

V C++/CLI můžete použít sledovací odkaz na popisovač při vytváření vazby na objekt typu CLR v haldě uvolňování paměti.

V modulu CLR se hodnota referenční proměnné sledování automaticky aktualizuje pokaždé, když systém uvolňování paměti přesune odkazovaný objekt.

Sledovací odkaz lze deklarovat pouze v zásobníku. Sledovací odkaz nemůže být členem třídy.

Není možné mít nativní C++ odkaz na objekt na haldě shromážděné paměti.

Další informace o sledovacích odkazech C++v/CLI najdete v těchto tématech:

- [Postupy: Používání sledovacích odkazů v jazyce C++/CLI](../dotnet/how-to-use-tracking-references-in-cpp-cli.md)

### <a name="examples"></a>Příklady

Následující ukázka pro C++/CLI ukazuje, jak použít sledovací odkaz s nativními a spravovanými typy.

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

Následující ukázka pro C++/CLI ukazuje, jak vytvořit vazby sledovacího odkazu na pole.

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
