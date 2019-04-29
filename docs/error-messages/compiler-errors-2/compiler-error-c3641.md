---
title: Chyba kompilátoru C3641
ms.date: 11/04/2016
f1_keywords:
- C3641
helpviewer_keywords:
- C3641
ms.assetid: e8d3613e-5e8d-46fe-a516-eb7d1de7cd21
ms.openlocfilehash: f6c27067e4f07c89b4226cf4d26adf2afb0b07ee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385651"
---
# <a name="compiler-error-c3641"></a>Chyba kompilátoru C3641

> "*funkce*': Neplatná konvence volání 'calling_convention' pro funkci zkompilovanou pomocí/clr: pure nebo/CLR: safe

## <a name="remarks"></a>Poznámky

**/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015 a není podporována v sadě Visual Studio 2017.

Pouze [__clrcall](../../cpp/clrcall.md) konvence volání je povoleno s [/CLR: pure](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3641:

```cpp
// C3641.cpp
// compile with: /clr:pure /c
void __cdecl f() {}   // C3641
```