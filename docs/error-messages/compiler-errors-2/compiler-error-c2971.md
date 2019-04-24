---
title: Chyba kompilátoru C2971
ms.date: 11/04/2016
f1_keywords:
- C2971
helpviewer_keywords:
- C2971
ms.assetid: fdb5467b-9a41-41ef-ac20-2e9428d5a4fc
ms.openlocfilehash: 09f3578bff5806fc32a3b5599dcfa8caa3696974
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62256320"
---
# <a name="compiler-error-c2971"></a>Chyba kompilátoru C2971

'class': parametr šablony 'param': 'arg': místní proměnné nelze použít jako beztypový argument

Název nebo adresu lokální proměnné nelze použít jako argument šablony.

Následující ukázka generuje C2971:

```
// C2971.cpp
template <int *pi>
class Y {};

int global_var = 0;

int main() {
   int local_var = 0;
   Y<&local_var> aY;   // C2971
   // try the following line instead
   // Y<&global_var> aY;
}
```