---
title: Chyba kompilátoru C2261
ms.date: 11/04/2016
f1_keywords:
- C2261
helpviewer_keywords:
- C2261
ms.assetid: 60969482-9e83-49b5-9631-a04bc844da12
ms.openlocfilehash: f23c2a38f8e4d6781af73fb70a25cf4737e2c4e8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758772"
---
# <a name="compiler-error-c2261"></a>Chyba kompilátoru C2261

String: odkaz na sestavení je neplatný a nedá se přeložit.

Hodnota není platná.

<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> slouží k určení sestavení typu Friend. Například pokud chce soubor. dll zadat b. dll jako sestavení typu Friend, zadali byste (v souboru. dll): InternalsVisibleTo ("b"). Modul runtime pak umožňuje b. dll přistupovat ke všemu v souboru. dll (s výjimkou privátních typů).

Další informace o správné syntaxi při určení sestavení typu Friend naleznete v tématu [Friend AssembliesC++()](../../dotnet/friend-assemblies-cpp.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C2261.

```cpp
// C2261.cpp
// compile with: /clr /c
using namespace System::Runtime::CompilerServices;
[assembly: InternalsVisibleTo("a,a,a")];   // C2261
[assembly: InternalsVisibleTo("a.a")];   // OK
[assembly: InternalsVisibleTo("a")];   // OK
```
