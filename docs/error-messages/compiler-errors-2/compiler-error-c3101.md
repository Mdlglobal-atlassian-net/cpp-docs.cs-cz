---
title: Chyba kompilátoru C3101
ms.date: 11/04/2016
f1_keywords:
- C3101
helpviewer_keywords:
- C3101
ms.assetid: 4f673766-d4f7-4632-94a5-d36a83f7f4b5
ms.openlocfilehash: dca91b9359417b8c4cce9329e2aa25107016c086
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749997"
---
# <a name="compiler-error-c3101"></a>Chyba kompilátoru C3101

neplatný výraz pro pojmenovaný argument atributu Field

Při inicializaci argumentu pojmenovaného atributu musí být hodnota časovou konstantou kompilace.

Další informace o atributech naleznete v tématu [uživatelsky definované atributy](../../extensions/user-defined-attributes-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3101.

```cpp
// C3101.cpp
// compile with: /clr /c
ref class AAttribute : System::Attribute {
public:
   int Field;
};

extern int i;

[assembly:A(Field = i)];   // C3101
[assembly:A(Field = 0)];   // OK
```
