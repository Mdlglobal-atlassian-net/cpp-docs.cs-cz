---
title: Chyba kompilátoru C3648
ms.date: 11/04/2016
f1_keywords:
- C3648
helpviewer_keywords:
- C3648
ms.assetid: 5d042989-41cb-4cd0-aa50-976b70146aaf
ms.openlocfilehash: 7394f6b9789caa09ffc2ad6c2cf56f037b5d57b8
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59775790"
---
# <a name="compiler-error-c3648"></a>Chyba kompilátoru C3648

Tato syntaxe explicitního přepsání vyžaduje oldSyntax

Při kompilaci pro nejnovější spravované syntaxe, kompilátor najít explicitní přepsání syntaxi pro předchozí verze, která se už nepodporuje.

Další informace najdete v tématu [explicitní přepsání](../../extensions/explicit-overrides-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3648:

```
// C3648.cpp
// compile with: /clr
public interface struct I {
   void f();
};

public ref struct R : I {
   virtual void I::f() {}   // C3648
   // try the following line instead
   // virtual void f() = I::f{}
};
```