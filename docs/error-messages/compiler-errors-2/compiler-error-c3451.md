---
title: Chyba kompilátoru C3451
ms.date: 11/04/2016
f1_keywords:
- C3451
helpviewer_keywords:
- C3451
ms.assetid: a4897a69-e3e7-40bb-bb1c-598644904012
ms.openlocfilehash: 07cfda76af26ddb285be4f77131aaf48a20a761f
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447851"
---
# <a name="compiler-error-c3451"></a>Chyba kompilátoru C3451

'attribute': nelze použít nespravovaný atribut na "typ"

Na typ CLR nelze použít atribut jazyka C++. Zobrazit [referenční dokumentace k atributům C++](../../windows/attributes/attributes-alphabetical-reference.md) Další informace.

Další informace najdete v tématu [uživatelem definované atributy](../../extensions/user-defined-attributes-cpp-component-extensions.md).

Tuto chybu mohou být generovány jako důsledek kompilátoru prací, které bylo provedeno pro Visual Studio 2005: [uuid](../../windows/uuid-cpp-attributes.md) atribut již není povolena u atributu uživatelem definované pomocí CLR programování. Místo nich se používá <xref:System.Runtime.InteropServices.GuidAttribute>.

## <a name="example"></a>Příklad

Následující ukázka generuje C3451.

```
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