---
title: 'Postupy: Deklarace a použití vnitřních ukazatelů a spravovaných polí (C++/CLI)'
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- pointers, interior
- arrays [C++], managed
ms.assetid: e61a2c09-a7d0-4867-91ea-6b8788a01079
ms.openlocfilehash: 88308e0ba79a8272b2fc323b9219a29e234b25ef
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181977"
---
# <a name="how-to-declare-and-use-interior-pointers-and-managed-arrays-ccli"></a>Postupy: Deklarace a použití vnitřních ukazatelů a spravovaných polí (C++/CLI)

Následující C++ukázka/CLI ukazuje, jak můžete deklarovat a použít vnitřní ukazatel na pole.

> [!IMPORTANT]
> Tato funkce jazyka je podporována možností kompilátoru `/clr`, ale ne pomocí možnosti kompilátoru `/ZW`.

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
