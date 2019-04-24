---
title: Chyba kompilátoru C3099
ms.date: 11/04/2016
f1_keywords:
- C3099
helpviewer_keywords:
- C3099
ms.assetid: b3dded0f-76c9-42c1-991b-532eb8619661
ms.openlocfilehash: 0f3eac1c232ef159d220a347d6b6dc3aed2fdd9a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62324776"
---
# <a name="compiler-error-c3099"></a>Chyba kompilátoru C3099

! – klíčové slovo': použijte [System::AttributeUsageAttribute] pro spravované atributy; Použijte [Windows::Foundation::Metadata::AttributeUsageAttribute] pro atributy WinRT

Použití <xref:System.AttributeUsageAttribute> deklarovat **/CLR** atributy. Použití `Windows::Foundation::Metadata::AttributeUsageAttribute` deklarovat atributy modulu Windows Runtime.

Další informace o atributech/CLR naleznete v tématu [uživatelem definované atributy](../../extensions/user-defined-attributes-cpp-component-extensions.md). Podporované atributy v prostředí Windows Runtime naleznete v tématu [Windows.Foundation.Metadata obor názvů](/uwp/api/windows.foundation.metadata)

## <a name="example"></a>Příklad

Následující ukázka generuje C3099 a ukazuje, jak ho opravit.

```
// C3099.cpp
// compile with: /clr /c
using namespace System;
[usage(10)]   // C3099
// try the following line instead
// [AttributeUsageAttribute(AttributeTargets::All)]
ref class A : Attribute {};
```