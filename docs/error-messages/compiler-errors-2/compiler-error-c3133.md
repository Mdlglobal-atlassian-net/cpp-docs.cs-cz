---
title: Chyba kompilátoru C3133
ms.date: 11/04/2016
f1_keywords:
- C3133
helpviewer_keywords:
- C3133
ms.assetid: 4a709405-b67b-4061-8a2a-19fa5fb34a2a
ms.openlocfilehash: 003befa97b033eec38d7187966da15e4a275f310
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760709"
---
# <a name="compiler-error-c3133"></a>Chyba kompilátoru C3133

Pro C++ vararg nelze použít atributy.

Atribut byl použit nesprávně. Atributy nelze použít pro tři tečky reprezentující argumenty proměnných.

Další informace najdete v tématu [uživatelsky definované atributy](../../extensions/user-defined-attributes-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3133.

```cpp
// C3133.cpp
// compile with: /clr /c
ref struct MyAttr: System::Attribute {};
void Func([MyAttr]...);   // C3133
void Func2([MyAttr] int i);   // OK
```
