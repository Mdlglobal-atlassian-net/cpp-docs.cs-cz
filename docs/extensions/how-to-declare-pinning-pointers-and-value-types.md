---
title: 'Postupy: Deklarace přídavných ukazatelů a typů hodnot'
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- value types, declaring
- pinning pointers
ms.assetid: 57c5ec8a-f85a-48c4-ba8b-a81268bcede0
ms.openlocfilehash: 88ef7e82161703a272a571392fd66e6055371c61
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181964"
---
# <a name="how-to-declare-pinning-pointers-and-value-types"></a>Postupy: Deklarace přídavných ukazatelů a typů hodnot

Hodnotový typ může být implicitně zabalený. Pak můžete deklarovat ukazatel připnutí na samotný objekt typu hodnoty a použít **pin_ptr** na zabalený typ hodnoty.

## <a name="example"></a>Příklad

### <a name="code"></a>Kód

```cpp
// pin_ptr_value.cpp
// compile with: /clr
value struct V {
   int i;
};

int main() {
   V ^ v = gcnew V;   // imnplicit boxing
   v->i=8;
   System::Console::WriteLine(v->i);
   pin_ptr<V> mv = &*v;
   mv->i = 7;
   System::Console::WriteLine(v->i);
   System::Console::WriteLine(mv->i);
}
```

```Output
8
7
7
```

## <a name="see-also"></a>Viz také

[pin_ptr (C++/CLI)](pin-ptr-cpp-cli.md)
