---
title: Chyba kompilátoru C2070 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2070
dev_langs:
- C++
helpviewer_keywords:
- C2070
ms.assetid: 4c8dea63-1227-4aba-be26-2462537f86fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b23daf8a8c25e132aa0717715a742352537010c8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044077"
---
# <a name="compiler-error-c2070"></a>Chyba kompilátoru C2070

'type': Neplatný operand sizeof

[Sizeof](../../cpp/sizeof-operator.md) operátor vyžaduje výraz nebo zadejte název.

Následující ukázka generuje C2070:

```
// C2070.cpp
void func() {}
int main() {
   int a;
   a = sizeof(func);   // C2070
}
```

Možná řešení:

```
// C2070b.cpp
void func() {}
int main() {
   int a;
   a = sizeof(a);
}
```