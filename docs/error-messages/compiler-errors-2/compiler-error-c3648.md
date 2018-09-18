---
title: Chyba kompilátoru C3648 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3648
dev_langs:
- C++
helpviewer_keywords:
- C3648
ms.assetid: 5d042989-41cb-4cd0-aa50-976b70146aaf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6cb86e4b34295a31e6c2d9a6fb8567efd9fbfe12
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110494"
---
# <a name="compiler-error-c3648"></a>Chyba kompilátoru C3648

Tato syntaxe explicitního přepsání vyžaduje oldSyntax

Při kompilaci pro nejnovější spravované syntaxe, kompilátor najít explicitní přepsání syntaxi pro předchozí verze, která se už nepodporuje.

Další informace najdete v tématu [explicitní přepsání](../../windows/explicit-overrides-cpp-component-extensions.md).

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