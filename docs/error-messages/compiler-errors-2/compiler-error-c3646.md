---
title: Chyba kompilátoru C3646
ms.date: 06/14/2018
f1_keywords:
- C3646
helpviewer_keywords:
- C3646
ms.assetid: 4391ead2-9637-4ca3-aeda-5a991b18d66d
ms.openlocfilehash: df2e52631ed75cc4a473429ea35e136ed0a88f98
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50606723"
---
# <a name="compiler-error-c3646"></a>Chyba kompilátoru C3646

> "specifikátor": Neznámý specifikátor override

## <a name="remarks"></a>Poznámky

Kompilátor nalezen token na pozici, kde se očekávalo se nalezení specifikátor přepisu, ale token, který nebyl rozpoznán kompilátorem.

Například pokud nerozpoznané *specifikátor* je **_NOEXCEPT**, nahraďte ho s klíčovým slovem **noexcept**.

Další informace najdete v tématu [specifikátory přepisu](../../windows/override-specifiers-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3646 a ukazuje způsob, jak ho opravit:

```cpp
// C3646.cpp
// compile with: /clr /c
ref class C {
   void f() unknown;   // C3646
   // try the following line instead
   // virtual void f() abstract;
};
```