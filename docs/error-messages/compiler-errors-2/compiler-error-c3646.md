---
title: Chyba kompilátoru C3646
ms.date: 06/14/2018
f1_keywords:
- C3646
helpviewer_keywords:
- C3646
ms.assetid: 4391ead2-9637-4ca3-aeda-5a991b18d66d
ms.openlocfilehash: 04ff1d026c97c56611f8b786d8a7254db711e4a8
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59775555"
---
# <a name="compiler-error-c3646"></a>Chyba kompilátoru C3646

> "specifikátor": Neznámý specifikátor override

## <a name="remarks"></a>Poznámky

Kompilátor nalezen token na pozici, kde se očekávalo se nalezení specifikátor přepisu, ale token, který nebyl rozpoznán kompilátorem.

Například pokud nerozpoznané *specifikátor* je **_NOEXCEPT**, nahraďte ho s klíčovým slovem **noexcept**.

Další informace najdete v tématu [specifikátory přepisu](../../extensions/override-specifiers-cpp-component-extensions.md).

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