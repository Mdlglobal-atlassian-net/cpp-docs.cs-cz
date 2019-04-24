---
title: Chyba kompilátoru C2087
ms.date: 11/04/2016
f1_keywords:
- C2087
helpviewer_keywords:
- C2087
ms.assetid: 89761e83-415a-4468-a4c6-b6dedfd1dd6a
ms.openlocfilehash: 11d5a0a86ba399e28a641fa490f19be020db2d9d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301432"
---
# <a name="compiler-error-c2087"></a>Chyba kompilátoru C2087

'identifier': chybí subscript

V definici pole s více dolními indexy chybí dolní hodnotu vyšší než jedna dimenze.

Následující ukázka generuje C2087:

```
// C2087.cpp
int main() {
   char a[10][];   // C2087
}
```

Možná řešení:

```
// C2087b.cpp
int main() {
   char b[4][5];
}
```