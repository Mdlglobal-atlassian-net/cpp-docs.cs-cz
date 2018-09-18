---
title: Chyba kompilátoru C2261 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2261
dev_langs:
- C++
helpviewer_keywords:
- C2261
ms.assetid: 60969482-9e83-49b5-9631-a04bc844da12
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2ed43dc43fb6ceaf514a8e7452b06eb7bdaf7362
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46051643"
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