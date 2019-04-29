---
title: Compiler Error C2180
ms.date: 11/04/2016
f1_keywords:
- C2180
helpviewer_keywords:
- C2180
ms.assetid: ea71b39e-b977-48a7-b7bd-af68ef5e263b
ms.openlocfilehash: 16fcf15eb29743f74bbf2edcb1016f2e15228e5a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385911"
---
# <a name="compiler-error-c2180"></a>Compiler Error C2180

řídicí výraz má typ 'type'

Řídicí výraz v `if`, `while`, `for`, nebo `do` příkaz je výraz přetypovaný na `void`. Chcete tento problém vyřešit, změňte řídicí výraz, který vytváří `bool` nebo typ, který lze převést na `bool`.

Následující ukázka generuje C2180:

```
// C2180.c

int main() {
   while ((void)1)   // C2180
      return 1;
   while (1)         // OK
      return 0;
}
```