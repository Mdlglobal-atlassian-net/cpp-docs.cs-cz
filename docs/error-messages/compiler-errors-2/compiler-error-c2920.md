---
title: Chyba kompilátoru C2920 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2920
dev_langs:
- C++
helpviewer_keywords:
- C2920
ms.assetid: 0a4cb2de-00a0-4209-8160-c7ce6ed7d9ab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cd8d28cf0f201b3042fe3d7a13d28e56150c976e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46021600"
---
# <a name="compiler-error-c2920"></a>Chyba kompilátoru C2920

Předefinování: 'class': Třída šablona nebo obecná hodnota již byl deklarován jako 'type'

Třída rozvrhy generic nebo šablony má více deklarací, které nejsou ekvivalentní. Chcete-li vyřešit tuto chybu, použijte jiné názvy pro různé typy nebo odeberte předefinování název typu.

Následující ukázka generuje C2920 a ukazuje, jak ho opravit:

```
// C2920.cpp
// compile with: /c
typedef int TC1;
template <class T>
struct TC1 {};   // C2920
struct TC2 {};   // OK - fix by using a different name
```

C2920 může dojít také při použití obecných typů:

```
// C2920b.cpp
// compile with: /clr /c
typedef int GC1;
generic <class T>
ref struct GC1 {};   // C2920
ref struct GC2 {};   // OK - fix by using a different name
```