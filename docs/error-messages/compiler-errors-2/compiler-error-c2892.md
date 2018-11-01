---
title: Chyba kompilátoru C2892
ms.date: 11/04/2016
f1_keywords:
- C2892
helpviewer_keywords:
- C2892
ms.assetid: c22a5084-2f50-42c2-a56b-6dfe5442edc9
ms.openlocfilehash: 296224532b19d9ff85c8644aa653b6d842205213
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50622817"
---
# <a name="compiler-error-c2892"></a>Chyba kompilátoru C2892

lokální třída Local nebude mít šablony členů

Šablony členské funkce nejsou platné ve třídě, který je definován ve funkci.

Následující ukázka generuje C2892:

```
// C2892.cpp
int main() {
   struct local {
      template<class T>   // C2892
      void f() {}
   };
}
```