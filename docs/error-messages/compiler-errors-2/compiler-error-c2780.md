---
title: Chyba kompilátoru C2780
ms.date: 11/04/2016
f1_keywords:
- C2780
helpviewer_keywords:
- C2780
ms.assetid: 423793d8-a3b2-4f35-85f8-ae1d043e2b69
ms.openlocfilehash: 9a427bbd79570a2646447d5326e034035306fac6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62257449"
---
# <a name="compiler-error-c2780"></a>Chyba kompilátoru C2780

"deklarace": očekává argumenty N - M k dispozici

Šablona funkce obsahuje příliš málo nebo příliš mnoho argumentů.

Následující ukázka generuje C2780 a ukazuje, jak ho opravit:

```
// C2780.cpp
template<typename T>
void f(T, T){}

int main() {
   f(1);  // C2780
   // try the following line instead
   // f(1,2);
}
```