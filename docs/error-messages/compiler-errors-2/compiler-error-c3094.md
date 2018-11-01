---
title: Chyba kompilátoru C3094
ms.date: 11/04/2016
f1_keywords:
- C3094
helpviewer_keywords:
- C3094
ms.assetid: 10da9b7c-e72d-4013-9925-c83e1bb142db
ms.openlocfilehash: 1b2cd29738763e5b31cc6727126114fca509a47f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512572"
---
# <a name="compiler-error-c3094"></a>Chyba kompilátoru C3094

'attribute': anonymní použití není povolené

Atribut nebyl správně oboru.  Další informace najdete v tématu [uživatelem definované atributy](../../windows/user-defined-attributes-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3094.

```
// C3094.cpp
// compile with: /clr /c
using namespace System;
[AttributeUsage(AttributeTargets::Class)]
public ref class AAttribute : Attribute {};

[A];   // C3094

// OK
[A]
ref class x{};
```