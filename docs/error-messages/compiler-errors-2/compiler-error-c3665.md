---
title: Chyba kompilátoru C3665
ms.date: 11/04/2016
f1_keywords:
- C3665
helpviewer_keywords:
- C3665
ms.assetid: 893bb47e-8de1-43aa-af7d-fa47ad149ee9
ms.openlocfilehash: 4b0c019b2425b314f5b3503db41042d917283aa8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758174"
---
# <a name="compiler-error-c3665"></a>Chyba kompilátoru C3665

' destruktor ': specifikátor override ' klíčové slovo ' není u destruktoru nebo finalizační metody povolen

Použilo se klíčové slovo, které není u destruktoru nebo finalizační metody povolené.

Například novou patici nelze požadovat u destruktoru nebo finalizační metody.  Další informace naleznete v tématu [Explicitní přepsání](../../extensions/explicit-overrides-cpp-component-extensions.md) a [destruktory a finalizační metody](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

Následující ukázka generuje C3665:

```cpp
// C3665.cpp
// compile with: /clr
public ref struct R {
   virtual ~R() { }
   virtual void a() { }
};

public ref struct S : R {
   virtual ~S() new {}   // C3665
   virtual void a() new {}   // OK
};
```
