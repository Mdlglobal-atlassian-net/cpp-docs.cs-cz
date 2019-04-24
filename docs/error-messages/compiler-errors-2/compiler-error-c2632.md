---
title: Chyba kompilátoru C2632
ms.date: 11/04/2016
f1_keywords:
- C2632
helpviewer_keywords:
- C2632
ms.assetid: b15a6b1b-42d2-4e1b-8660-e6bfde61052d
ms.openlocfilehash: b92d44bcfd04d4de7b39c5bdab5ee146d9b6693b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62257631"
---
# <a name="compiler-error-c2632"></a>Chyba kompilátoru C2632

'type1' následuje 'type2' je neplatný.

Tato chyba může nastat, pokud chybí kód mezi dva specifikátory typu.

Následující ukázka generuje C2632:

```
// C2632.cpp
int float i;   // C2632
```

Tato chyba může být také generovány jako důsledek kompilátoru prací, které bylo provedeno pro Visual Studio .NET 2003. `bool` je teď správný typ. V předchozích verzích `bool` byla definice typu, a můžete vytvořit identifikátory s tímto názvem.

Následující ukázka generuje C2632:

```
// C2632_2.cpp
// compile with: /LD
void f(int bool);   // C2632
```

Chcete-li vyřešit tuto chybu tak, aby kód je platný v Visual Studio .NET 2003 i Visual Studio .NET verzí jazyka Visual C++, přejmenujte identifikátor.