---
title: Upozornění kompilátoru (úroveň 1) C4677
ms.date: 11/04/2016
f1_keywords:
- C4677
helpviewer_keywords:
- C4677
ms.assetid: a8d656a1-e2ff-4f8b-9028-201765131026
ms.openlocfilehash: 5b31fd22c917b2c0f505ca189425f8160f62f748
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175542"
---
# <a name="compiler-warning-level-1-c4677"></a>Upozornění kompilátoru (úroveň 1) C4677

' function ': podpis neprivátního členu obsahuje typ sestavení Private ' private_type '

Typ, který má veřejné přístupnost mimo sestavení, používá typ, který má privátní přístup mimo sestavení. Komponenta, která odkazuje na typ veřejného sestavení, nebude moci používat člena typu nebo členy, kteří odkazují na privátní typ sestavení.

## <a name="example"></a>Příklad

Následující ukázka generuje C4677.

```cpp
// C4677.cpp
// compile with: /clr /c /W1
delegate void TestDel();
public delegate void TestDel2();

public ref class MyClass {
public:
   static event TestDel^ MyClass_Event;   // C4677
   static event TestDel2^ MyClass_Event2;   // OK
};
```
