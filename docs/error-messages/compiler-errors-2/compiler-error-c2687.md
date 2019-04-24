---
title: Chyba kompilátoru C2687
ms.date: 11/04/2016
f1_keywords:
- C2687
helpviewer_keywords:
- C2687
ms.assetid: 1d24b24a-cd0f-41cc-975c-b08dcfb7f402
ms.openlocfilehash: a30efa264a4e7be387c3c2363940bd5ceca1bcc4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62266189"
---
# <a name="compiler-error-c2687"></a>Chyba kompilátoru C2687

'type': deklarace výjimky nemůže být void' nebo označení neúplný typ nebo ukazatel nebo odkaz na neúplný typ.

Pro typ jako součást deklaraci výjimky musí být definované a ne void.

Následující ukázka generuje C2687:

```
// C2687.cpp
class C;

int main() {
   try {}
   catch (C) {}   // C2687 error
}
```

Možná řešení:

```
// C2687b.cpp
// compile with: /EHsc
class C {};

int main() {
   try {}
   catch (C) {}
}
```