---
title: Chyba kompilátoru C2939 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2939
dev_langs:
- C++
helpviewer_keywords:
- C2939
ms.assetid: 455b050b-f2dc-4b5b-bd6a-e1f81d3d1644
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b7d397eff2cfe561ace6f29b00601941779ef2b2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053145"
---
# <a name="compiler-error-c2939"></a>Chyba kompilátoru C2939

'class': typ třídy id se předefinovalo jako místní datová proměnná

Rozvrhy generic nebo šablony třídy nelze použít jako proměnná místní data.

Tato chyba může nastat, pokud jsou nesprávně odpovídající složené závorky.

Následující ukázka generuje C2939:

```
// C2939.cpp
template<class T>
struct TC { };
int main() {
   int TC<int>;   // C2939
   int TC;   // OK
}
```

C2939 může dojít také při použití obecných typů:

```
// C2939b.cpp
// compile with: /clr
generic<class T>
ref struct GC { };

int main() {
   int GC<int>;   // C2939
   int GC;   // OK
}
```