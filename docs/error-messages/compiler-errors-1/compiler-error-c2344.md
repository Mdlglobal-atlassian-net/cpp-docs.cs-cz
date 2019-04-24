---
title: Compiler Error C2344
ms.date: 11/04/2016
f1_keywords:
- C2344
helpviewer_keywords:
- C2344
ms.assetid: a84c7b37-c84e-4345-8691-c23abb2dc193
ms.openlocfilehash: d1ba3a0f975dbc96c9c6ca51a8dac89b5a614572
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188169"
---
# <a name="compiler-error-c2344"></a>Compiler Error C2344

align(#): zarovnání musí být mocninou čísla 2

Při použití [zarovnat](../../cpp/align-cpp.md) – klíčové slovo, předáte hodnotu musí být mocninou čísla 2.

Například následující kód vygeneruje C2344 protože 3 není mocninou čísla 2:

```
// C2344.cpp
// compile with: /c
__declspec(align(3)) int a;   // C2344
__declspec(align(4)) int b;   // OK
```