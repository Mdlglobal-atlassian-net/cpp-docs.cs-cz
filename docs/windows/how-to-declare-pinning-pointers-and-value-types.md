---
title: 'Postupy: Deklarace přídavných ukazatelů a typů hodnot'
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- value types, declaring
- pinning pointers
ms.assetid: 57c5ec8a-f85a-48c4-ba8b-a81268bcede0
ms.openlocfilehash: ed7835e3ab6ccda724ccb6c0d7cf5dab8dd4d342
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50660860"
---
# <a name="how-to-declare-pinning-pointers-and-value-types"></a>Postupy: Deklarace přídavných ukazatelů a typů hodnot

Hodnotový typ jde použít boxing implicitně. Pak může deklarovat ukazatel Připnutí na objekt typu hodnoty samostatně a použití **pin_ptr** na hodnotový typu.

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

[pin_ptr (C++/CLI)](../windows/pin-ptr-cpp-cli.md)