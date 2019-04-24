---
title: Chyba kompilátoru C3450
ms.date: 11/04/2016
f1_keywords:
- C3450
helpviewer_keywords:
- C3450
ms.assetid: 78892cf7-0b82-4589-90d0-e06666247003
ms.openlocfilehash: a5228e0396221c51f5fc7336255656416c1e553b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62328632"
---
# <a name="compiler-error-c3450"></a>Chyba kompilátoru C3450

'type': nejde o atribut; Nelze zadat [System::AttributeUsageAttribute] nebo [Windows::Foundation::Metadata::AttributeUsageAttribute]

Uživatelem definované spravované atribut musí dědit z <xref:System.ComponentModel.AttributeCollection.%23ctor%2A>. Atribut modulu Windows Runtime musí být definován v `Windows::Foundation::Metadata` oboru názvů.

Další informace najdete v tématu [uživatelem definované atributy](../../extensions/user-defined-attributes-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3450 a ukazuje, jak ho opravit.

```
// C3450.cpp
// compile with: /clr
// C3450 expected
using namespace System;
using namespace System::Security;
using namespace System::Security::Permissions;

public ref class MyClass {};

class MyClass2 {};

[attribute(AttributeTargets::All)]
ref struct AtClass {
   AtClass(Type ^) {}
};

[attribute(AttributeTargets::All)]
ref struct AtClass2 {
   AtClass2() {}
};

// Apply the AtClass and AtClass2 attributes to class B
[AtClass(MyClass::typeid), AtClass2]
[AttributeUsage(AttributeTargets::All)]
// Delete the following line to resolve.
ref class B {};
// Uncomment the following line to resolve.
// ref class B : Attribute {};
```