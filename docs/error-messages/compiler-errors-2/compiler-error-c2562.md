---
title: Chyba kompilátoru C2562 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2562
dev_langs:
- C++
helpviewer_keywords:
- C2562
ms.assetid: 2c41e511-9952-4b98-9976-6b1523613e1b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 69151b71de84c678c09ecafe099344a08d28a8a8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46114225"
---
# <a name="compiler-error-c2562"></a>Chyba kompilátoru C2562

'identifier': "void" funkce vrací hodnotu

Funkce je deklarována jako `void` , ale vrací hodnotu.

Tuto chybu může způsobovat prototypu nesprávná funkce.

Tato chyba může být stanovena, pokud zadáte návratový typ v deklaraci funkce.

Následující ukázka generuje C2562:

```
// C2562.cpp
// compile with: /c
void testfunc() {
   int i;
   return i;   // C2562 delete the return to resolve
}
```