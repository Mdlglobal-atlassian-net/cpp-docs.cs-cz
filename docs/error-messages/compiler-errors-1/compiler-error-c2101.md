---
title: Chyba kompilátoru C2101 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2101
dev_langs:
- C++
helpviewer_keywords:
- C2101
ms.assetid: 42f0136f-8cc1-4f2b-be1c-721ec9278e66
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 247bd168e1ea82d4533c794ae5c14d34a49064d0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46041360"
---
# <a name="compiler-error-c2101"></a>Chyba kompilátoru C2101

' &' na – konstanta

Operátor address-of ( `&` ) musí být l hodnotou jako operand.

Následující ukázka generuje C2101:

```
// C2101.cpp
int main() {
   char test;
   test = &'a';   // C2101
   test = 'a';   // OK
}
```