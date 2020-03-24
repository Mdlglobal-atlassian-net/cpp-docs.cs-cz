---
title: Chyba kompilátoru C3646
ms.date: 06/14/2018
f1_keywords:
- C3646
helpviewer_keywords:
- C3646
ms.assetid: 4391ead2-9637-4ca3-aeda-5a991b18d66d
ms.openlocfilehash: 13a3ebeb6e7783687abc73cd0dcc018abe827809
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200470"
---
# <a name="compiler-error-c3646"></a>Chyba kompilátoru C3646

> specifikátor: neznámý specifikátor override

## <a name="remarks"></a>Poznámky

Kompilátor našel token na pozici, kde se očekává, že najde specifikátor přepsání, ale token nerozpoznal kompilátor.

Například pokud je nerozpoznaný *specifikátor* **_NOEXCEPT**, nahraďte ho klíčovým slovem s **výjimkou**.

Další informace najdete v tématu [specifikátory přepisu](../../extensions/override-specifiers-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3646 a ukazuje způsob, jak ji opravit:

```cpp
// C3646.cpp
// compile with: /clr /c
ref class C {
   void f() unknown;   // C3646
   // try the following line instead
   // virtual void f() abstract;
};
```
