---
title: Compiler Error C3103
ms.date: 11/04/2016
f1_keywords:
- C3103
helpviewer_keywords:
- C3103
ms.assetid: 7984bd3e-d51d-43e4-b6f4-08c1e9fb9704
ms.openlocfilehash: 6a68e39ac92433eadacd666861f9e00431e4a34a
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59775927"
---
# <a name="compiler-error-c3103"></a>Compiler Error C3103

"argument": opakovaný pojmenovaný argument

Atribut se nemůže opakovat. pojmenované argumenty.

Další informace najdete v tématu [uživatelem definované atributy](../../extensions/user-defined-attributes-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3103.

```
// C3103.cpp
// compile with: /clr /c
using namespace System;

[AttributeUsage(AttributeTargets::All)]
public ref class Attr : public Attribute {
public:
   int m_t;
};

[Attr(m_t = 10, m_t = 1)]   // C3103
// try the following line instead
// [Attr(m_t = 10)]
ref class A {};
```