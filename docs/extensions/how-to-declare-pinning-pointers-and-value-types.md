---
title: 'Postupy: Deklarace přídavných ukazatelů a typů hodnot'
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- value types, declaring
- pinning pointers
ms.assetid: 57c5ec8a-f85a-48c4-ba8b-a81268bcede0
ms.openlocfilehash: 2f62d8e93af48d0d916349f7c58fbd5fe445e322
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58786912"
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

[pin_ptr (C++/CLI)](pin-ptr-cpp-cli.md)