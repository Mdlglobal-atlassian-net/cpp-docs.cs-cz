---
title: 'Postupy: Deklarování a použití vnitřních ukazatelů a spravovaných polí (C + +/ CLI)'
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- pointers, interior
- arrays [C++], managed
ms.assetid: e61a2c09-a7d0-4867-91ea-6b8788a01079
ms.openlocfilehash: 61c6f9c2cd8a483711509a060b320b11ec273148
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58787027"
---
# <a name="how-to-declare-and-use-interior-pointers-and-managed-arrays-ccli"></a>Postupy: Deklarování a použití vnitřních ukazatelů a spravovaných polí (C + +/ CLI)

Následující C + +/ CLI příklad ukazuje, jak deklarovat a použít vnitřní ukazatel na pole.

> [!IMPORTANT]
> Této funkci jazyka podporuje `/clr` – možnost kompilátoru, ale ne za `/ZW` – možnost kompilátoru.

## <a name="example"></a>Příklad

### <a name="code"></a>Kód

```cpp
// interior_ptr_arrays.cpp
// compile with: /clr
#define SIZE 10

int main() {
   // declare the array
   array<int>^ arr = gcnew array<int>(SIZE);

   // initialize the array
   for (int i = 0 ; i < SIZE ; i++)
      arr[i] = i + 1;

   // create an interior pointer into the array
   interior_ptr<int> ipi = &arr[0];

   System::Console::WriteLine("1st element in arr holds: {0}", arr[0]);
   System::Console::WriteLine("ipi points to memory address whose value is: {0}", *ipi);

   ipi++;
   System::Console::WriteLine("after incrementing ipi, it points to memory address whose value is: {0}", *ipi);
}
```

```Output
1st element in arr holds: 1
ipi points to memory address whose value is: 1
after incrementing ipi, it points to memory address whose value is: 2
```

## <a name="see-also"></a>Viz také

[interior_ptr (C++/CLI)](interior-ptr-cpp-cli.md)