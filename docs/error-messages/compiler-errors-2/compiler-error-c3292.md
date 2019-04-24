---
title: Chyba kompilátoru C3292
ms.date: 11/04/2016
f1_keywords:
- C3292
helpviewer_keywords:
- C3292
ms.assetid: ead485cc-5471-4e10-b361-300589ff5b70
ms.openlocfilehash: a68d3e922532480063fe4c294e40f453885743e8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222627"
---
# <a name="compiler-error-c3292"></a>Chyba kompilátoru C3292

obor názvů cli nejde znovu otevřít

Obor názvů cli se nedá deklarovat v kódu.  Další informace najdete v tématu [Platform, default a cli obory názvů](../../extensions/platform-default-and-cli-namespaces-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3292.

```
// C3292.cpp
// compile with: /clr /c
namespace cli {};   // C3292
```