---
title: 'Postupy: Deklarace hodnotových typů s použitím klíčového slova interior_ptr (C++/CLI)'
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- _ptr keyword
- value types, declaring
ms.assetid: 49eea66e-eeba-49bd-95b0-ba297be436e3
ms.openlocfilehash: 22c0fe4424e4df81ebb0355dfac2168af725b971
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172279"
---
# <a name="how-to-declare-value-types-with-the-interior_ptr-keyword-ccli"></a>Postupy: Deklarace hodnotových typů s použitím klíčového slova interior_ptr (C++/CLI)

**Interior_ptr** lze použít s typem hodnoty.

> [!IMPORTANT]
> Tato funkce jazyka je podporována možností kompilátoru `/clr`, ale ne pomocí možnosti kompilátoru `/ZW`.

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Následující C++ukázka/CLI ukazuje, jak použít **interior_ptr** s typem hodnoty.

### <a name="code"></a>Kód

```cpp
// interior_ptr_value_types.cpp
// compile with: /clr
value struct V {
   V(int i) : data(i){}
   int data;
};

int main() {
   V v(1);
   System::Console::WriteLine(v.data);

   // pointing to a value type
   interior_ptr<V> pv = &v;
   pv->data = 2;

   System::Console::WriteLine(v.data);
   System::Console::WriteLine(pv->data);

   // pointing into a value type
   interior_ptr<int> pi = &v.data;
   *pi = 3;
   System::Console::WriteLine(*pi);
   System::Console::WriteLine(v.data);
   System::Console::WriteLine(pv->data);
}
```

```Output
1
2
2
3
3
3
```

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

V typu hodnoty je **Tento** ukazatel vyhodnocen jako interior_ptr.

V těle nestatické členské funkce typu hodnoty `V`**Toto** je výraz typu `interior_ptr<V>` jehož hodnota je adresa objektu, pro který je funkce volána.

### <a name="code"></a>Kód

```cpp
// interior_ptr_value_types_this.cpp
// compile with: /clr /LD
value struct V {
   int data;
   void f() {
      interior_ptr<V> pv1 = this;
      // V* pv2 = this;   error
   }
};
```

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Následující příklad ukazuje, jak použít operátor address-of se statickými členy.

Adresa statického vizuálního C++ typu má za důsledek nativní ukazatel.  Adresa člena typu statických hodnot je spravovaný ukazatel, protože člen typu hodnoty je přidělen na haldu modulu runtime a může být přesunut systémem uvolňování paměti.

### <a name="code"></a>Kód

```cpp
// interior_ptr_value_static.cpp
// compile with: /clr
using namespace System;
value struct V { int i; };

ref struct G {
   static V v = {22};
   static int i = 23;
   static String^ pS = "hello";
};

int main() {
   interior_ptr<int> p1 = &G::v.i;
   Console::WriteLine(*p1);

   interior_ptr<int> p2 = &G::i;
   Console::WriteLine(*p2);

   interior_ptr<String^> p3 = &G::pS;
   Console::WriteLine(*p3);
}
```

```Output
22
23
hello
```

## <a name="see-also"></a>Viz také

[interior_ptr (C++/CLI)](interior-ptr-cpp-cli.md)
