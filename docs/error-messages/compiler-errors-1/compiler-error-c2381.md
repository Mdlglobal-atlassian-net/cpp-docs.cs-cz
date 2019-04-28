---
title: Chyba kompilátoru C2381
ms.date: 11/04/2016
f1_keywords:
- C2381
helpviewer_keywords:
- C2381
ms.assetid: cc765f67-64ac-406f-93ef-ae7d548d58d7
ms.openlocfilehash: b29f7dac6c6d71e12eb0f003cdfc151dd2c349a7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62347896"
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