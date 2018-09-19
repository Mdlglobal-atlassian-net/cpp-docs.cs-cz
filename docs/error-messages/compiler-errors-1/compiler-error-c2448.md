---
title: Chyba kompilátoru C2448 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2448
dev_langs:
- C++
helpviewer_keywords:
- C2448
ms.assetid: e255df3c-f861-4b4d-a193-8768cef061a5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b5d3de3b8d4d5d184bb33214679842c557aadf7d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46135980"
---
# <a name="compiler-error-c2448"></a>Chyba kompilátoru C2448

'identifier': inicializátor function-style se zdá být definicí funkce.

Definice funkce je nesprávný.

Tuto chybu může způsobovat formální seznam ve starém stylu jazyka C.

Následující ukázka generuje C2448:

```
// C2448.cpp
void func(c)
   int c;
{}   // C2448
```