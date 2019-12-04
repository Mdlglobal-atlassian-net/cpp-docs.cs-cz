---
title: Chyba kompilátoru C3451
ms.date: 11/04/2016
f1_keywords:
- C3451
helpviewer_keywords:
- C3451
ms.assetid: a4897a69-e3e7-40bb-bb1c-598644904012
ms.openlocfilehash: 2e0122dd53ba5318077dd33f22a07492c52db26b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756211"
---
# <a name="compiler-error-c3451"></a>Chyba kompilátoru C3451

' Attribute ': nespravovaný atribut nelze použít pro typ '

C++ Atribut nelze použít pro typ CLR. Další informace naleznete v tématu [ C++ Reference k atributům](../../windows/attributes/attributes-alphabetical-reference.md) .

Další informace najdete v tématu [uživatelsky definované atributy](../../extensions/user-defined-attributes-cpp-component-extensions.md).

Tato chyba se může vygenerovat v důsledku práce s shodami s kompilátorem, která se dokončila pro Visual Studio 2005: atribut [UUID](../../windows/uuid-cpp-attributes.md) už není povolený u uživatelsky definovaného atributu pomocí programování CLR. Místo nich se používá <xref:System.Runtime.InteropServices.GuidAttribute>.

## <a name="example"></a>Příklad

Následující ukázka generuje C3451.

```cpp
// C3451.cpp
// compile with: /clr /c
using namespace System;
[ attribute(AttributeTargets::All) ]
public ref struct MyAttr {};

[ MyAttr, helpstring("test") ]   // C3451
// try the following line instead
// [ MyAttr ]
public ref struct ABC {};
```
