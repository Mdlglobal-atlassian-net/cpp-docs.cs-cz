---
title: Chyba kompilátoru C2483
ms.date: 09/15/2017
f1_keywords:
- C2483
helpviewer_keywords:
- C2483
ms.assetid: 5762b325-914b-442d-a604-e4617ba04038
ms.openlocfilehash: 20b08c0d2cd89224ed3d3b8b34915deb947b0b4b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205111"
---
# <a name="compiler-error-c2483"></a>Chyba kompilátoru C2483

>'*Identifier*': u objektu s konstruktorem nebo destruktorem nelze používat deklaraci ' Thread '

Tato chybová zpráva je zastaralá v aplikaci Visual Studio 2015 a novějších verzích. V předchozích verzích se proměnné deklarované s atributem `thread` nedají inicializovat pomocí konstruktoru nebo jiného výrazu, který vyžaduje vyhodnocení modulu runtime. Pro inicializaci `thread`ch dat je vyžadován statický výraz.

## <a name="example"></a>Příklad

Následující ukázka generuje C2483 v Visual Studio 2013 a starších verzích.

```cpp
// C2483.cpp
// compile with: /c
__declspec(thread) struct A {
   A(){}
   ~A(){}
} aa;   // C2483 error

__declspec(thread) struct B {} b;   // OK
```

## <a name="see-also"></a>Viz také

[thread](../../cpp/thread.md)
