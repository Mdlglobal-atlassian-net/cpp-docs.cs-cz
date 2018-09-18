---
title: Chyba kompilátoru C2921 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2921
dev_langs:
- C++
helpviewer_keywords:
- C2921
ms.assetid: 323642a0-bfc4-4942-9f41-c3adf5c54296
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: afc445bd9d30e97d669cf02b53d98553e9658e47
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46100939"
---
# <a name="compiler-error-c2921"></a>Chyba kompilátoru C2921

Předefinování: 'class': Třída šablona nebo obecná hodnota je znovu deklarován jako 'type'

Třída rozvrhy generic nebo šablony má více deklarací, které nejsou ekvivalentní. Chcete-li vyřešit tuto chybu, použijte jiné názvy pro různé typy nebo odeberte předefinování název typu.

Následující ukázka generuje C2921:

```
// C2921.cpp
// compile with: /c
template <class T> struct TC2 {};
typedef int TC2;   // C2921
// try the following line instead
// typedef struct TC2<int> x;   // OK - declare a template instance
```

C2921 může dojít také při použití obecných typů.

```
// C2921b.cpp
// compile with: /clr /c
generic <class T> ref struct GC2 {};
typedef int GC2;   // C2921
// try the following line instead
// typedef ref struct GC2<int> x;
```