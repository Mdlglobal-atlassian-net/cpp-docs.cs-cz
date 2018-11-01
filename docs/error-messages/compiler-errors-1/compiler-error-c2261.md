---
title: Chyba kompilátoru C2261
ms.date: 11/04/2016
f1_keywords:
- C2261
helpviewer_keywords:
- C2261
ms.assetid: 60969482-9e83-49b5-9631-a04bc844da12
ms.openlocfilehash: 2df788efd93fb531822d858ea5aee1722487db81
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50535743"
---
# <a name="compiler-error-c2261"></a>Chyba kompilátoru C2261

"řetězec": odkaz na sestavení je neplatný a nelze rozpoznat

Hodnota není platný.

<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> slouží k určení přátelského sestavení. Například pokud a.dll chce b.dll zadat jako sestavení typu friend, zadali byste (v a.dll): InternalsVisibleTo("b"). Modul runtime pak umožní b.dll přístup ke všem, co a.dll (s výjimkou soukromé typy).

Další informace o správnou syntaxi při určování sestavení typu friend, naleznete v tématu [přátelská sestavení (C++)](../../dotnet/friend-assemblies-cpp.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C2261.

```
// C2261.cpp
// compile with: /clr /c
using namespace System::Runtime::CompilerServices;
[assembly: InternalsVisibleTo("a,a,a")];   // C2261
[assembly: InternalsVisibleTo("a.a")];   // OK
[assembly: InternalsVisibleTo("a")];   // OK
```