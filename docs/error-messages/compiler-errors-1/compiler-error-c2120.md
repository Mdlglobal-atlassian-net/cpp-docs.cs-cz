---
title: Compiler Error C2120
ms.date: 11/04/2016
f1_keywords:
- C2120
helpviewer_keywords:
- C2120
ms.assetid: b0f3f66c-6cd2-4f48-9ea3-c270b53c2b8c
ms.openlocfilehash: 699a80b2cdb1de175c78efb918ba9389ec3695f4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182857"
---
# <a name="compiler-error-c2120"></a>Compiler Error C2120

void neplatná se všemi typy

`void` Typ se používá v deklaraci jiného typu.

Následující ukázka generuje C2120:

```
// C2120.cpp
int main() {
   void int i;   // C2120
   int j;   // OK
}
```