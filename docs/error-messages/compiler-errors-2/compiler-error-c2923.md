---
title: Chyba kompilátoru C2923 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2923
dev_langs:
- C++
helpviewer_keywords:
- C2923
ms.assetid: 6b92933b-13ef-4124-99d9-b89f9fdae030
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e8bcf4a16681c725240f052921dfa9efb8dde8ad
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106154"
---
# <a name="compiler-error-c2923"></a>Chyba kompilátoru C2923

'type': 'identifikátor' není platnou šablonu argument typu pro parametr 'param'

Seznam argumentů chybí typ potřebné k vytvoření instance šablona nebo obecná hodnota. Zkontrolujte šablona nebo obecná deklarace.

Následující ukázka generuje C2923:

```
// C2923.cpp
template <class T> struct TC {};
int x;
int main() {
   TC<x>* tc2;   // C2923
   TC<int>* tc2;   // OK
}
```

C2923 může dojít také při použití obecných typů:

```
// C2923b.cpp
// compile with: /clr /c
generic <class T> ref struct GC {};

int x;

int main() {
   GC<x>^ gc2;   // C2923
   GC<int>^ gc2;   // OK
}
```