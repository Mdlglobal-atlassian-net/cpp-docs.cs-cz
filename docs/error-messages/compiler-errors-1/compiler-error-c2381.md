---
title: Chyba kompilátoru C2381 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2381
dev_langs:
- C++
helpviewer_keywords:
- C2381
ms.assetid: cc765f67-64ac-406f-93ef-ae7d548d58d7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6f09cd8c16eeb5ec797643cb6653d069df41b136
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076941"
---
# <a name="compiler-error-c2381"></a>Chyba kompilátoru C2381

'function': předefinování; __declspec(noreturn) se liší.

Funkce byla deklarována a potom definované ale definice použitá [noreturn](../../cpp/noreturn.md) `__declspec` modifikátor. Použití `noreturn` nová definice funkce se považuje za; deklarace a definice musí shodnout na použití `noreturn`.

Následující ukázka generuje C2381:

```
// C2381.cpp
// compile with: /c
void f1();
void __declspec(noreturn) f1() {}   // C2381
void __declspec(noreturn) f2() {}   // OK
```