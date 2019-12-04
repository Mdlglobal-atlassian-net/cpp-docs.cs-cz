---
title: Chyba kompilátoru C3097
ms.date: 11/04/2016
f1_keywords:
- C3097
helpviewer_keywords:
- C3097
ms.assetid: b24bd8f8-e04f-4fbb-be57-4feb9165572e
ms.openlocfilehash: 71a7762d03c600fed71d76a19088fb70ce311f67
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756809"
---
# <a name="compiler-error-c3097"></a>Chyba kompilátoru C3097

' Attribute ': atribut musí být v oboru ' Assembly: ' nebo ' Module: '

Globální atribut byl použit nesprávně.

Další informace najdete v tématu [uživatelsky definované atributy](../../extensions/user-defined-attributes-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3097.

```cpp
// C3097.cpp
// compile with: /clr /c
using namespace System;

[AttributeUsage(AttributeTargets::All, AllowMultiple = true)]
public ref class Attr : public Attribute {
public:
   Attr(int t) : m_t(t) {}
   int m_t;
};

[Attr(10)];   // C3097
[assembly:Attr(10)];   // OK

[Attr(10)]   // OK
public ref class MyClass {};
```
