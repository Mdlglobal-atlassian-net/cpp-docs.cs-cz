---
title: Chyba kompilátoru C3099
ms.date: 11/04/2016
f1_keywords:
- C3099
helpviewer_keywords:
- C3099
ms.assetid: b3dded0f-76c9-42c1-991b-532eb8619661
ms.openlocfilehash: 81f508c47c678d86f8f95303861b42f8a70daa57
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750049"
---
# <a name="compiler-error-c3099"></a>Chyba kompilátoru C3099

klíčové slovo: pro spravované atributy použijte [System:: AttributeUsageAttribute]; pro atributy WinRT použijte [Windows:: Foundation:: metadata:: AttributeUsageAttribute].

Použijte <xref:System.AttributeUsageAttribute> k deklaraci atributů **/CLR** . Použijte `Windows::Foundation::Metadata::AttributeUsageAttribute` k deklaraci atributů prostředí Windows Runtime.

Další informace o atributech/CLR naleznete v tématu [uživatelsky definované atributy](../../extensions/user-defined-attributes-cpp-component-extensions.md). Podporované atributy v prostředí Windows Runtime najdete v tématu [obor názvů Windows. Foundation. Metadata.](/uwp/api/windows.foundation.metadata)

## <a name="example"></a>Příklad

Následující ukázka generuje C3099 a ukazuje, jak ji opravit.

```cpp
// C3099.cpp
// compile with: /clr /c
using namespace System;
[usage(10)]   // C3099
// try the following line instead
// [AttributeUsageAttribute(AttributeTargets::All)]
ref class A : Attribute {};
```
