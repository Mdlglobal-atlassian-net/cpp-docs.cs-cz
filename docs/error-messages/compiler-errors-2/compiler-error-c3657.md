---
title: Chyba kompilátoru C3657
ms.date: 11/04/2016
f1_keywords:
- C3657
helpviewer_keywords:
- C3657
ms.assetid: 89a28a18-4c17-43a1-bda6-deb52c32d203
ms.openlocfilehash: f979d5776bea5e8fb6e0255bdcdeaacb284932ac
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59778459"
---
# <a name="compiler-error-c3657"></a>Chyba kompilátoru C3657

Destruktory nelze explicitně přepisovat ani explicitně přepsat

Destruktory a finalizační metody nelze explicitně přepsat. Další informace najdete v tématu [explicitní přepsání](../../extensions/explicit-overrides-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3657.

```
// C3657.cpp
// compile with: /clr
public ref struct I {
   virtual ~I() { }
   virtual void a();
};

public ref struct D : I {
   virtual ~D() = I::~I {}   // C3657
   virtual void a() = I::a {}   // OK
};
```