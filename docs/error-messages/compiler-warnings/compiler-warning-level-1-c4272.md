---
title: Upozornění kompilátoru (úroveň 1) C4272
ms.date: 11/04/2016
f1_keywords:
- C4272
helpviewer_keywords:
- C4272
ms.assetid: 0d6c1de4-2eef-42c4-b861-c221f8b495ef
ms.openlocfilehash: 13c56c2261cd069e7edec63921c198e2bee56c95
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626702"
---
# <a name="compiler-warning-level-1-c4272"></a>Upozornění kompilátoru (úroveň 1) C4272

' function ': je označen jako __declspec (dllimport); Při importu funkce je nutné zadat nativní konvenci volání.

Pokud se pokusíte importovat funkci označenou jako `__clrcall`, jedná se o chybu při exportování funkce označené konvencí volání [__clrcall](../../cpp/clrcall.md) a kompilátor vydá toto upozornění.

Následující ukázka generuje C4272:

```cpp
// C4272.cpp
// compile with: /c /W1 /clr
__declspec(dllimport) void __clrcall Test();   // C4272
__declspec(dllimport) void Test2();   // OK
```