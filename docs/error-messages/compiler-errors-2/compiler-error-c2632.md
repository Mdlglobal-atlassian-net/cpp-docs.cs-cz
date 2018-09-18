---
title: Chyba kompilátoru C2632 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2632
dev_langs:
- C++
helpviewer_keywords:
- C2632
ms.assetid: b15a6b1b-42d2-4e1b-8660-e6bfde61052d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7bf03c35c60bebb52c94ed04cca2349f35c06fbc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093647"
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