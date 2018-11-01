---
title: Chyba kompilátoru C3389
ms.date: 11/04/2016
f1_keywords:
- C3389
helpviewer_keywords:
- C3389
ms.assetid: eaaffe17-23f2-413c-b1ad-f7220cfa1334
ms.openlocfilehash: 6a9568f3c3be88438eae1f28e12dc780301ead0b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50584298"
---
# <a name="compiler-error-c3389"></a>Chyba kompilátoru C3389

> __declspec (*– klíčové slovo*) nelze použít s/clr: pure nebo/CLR: safe

## <a name="remarks"></a>Poznámky

**/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015 a není podporována v sadě Visual Studio 2017.

A [__declspec](../../cpp/declspec.md) předpokládá modifikátor použít stav procesu.  [/ CLR: pure](../../build/reference/clr-common-language-runtime-compilation.md) znamená za [appdomain](../../cpp/appdomain.md) stavu.  Proto deklarace proměnné s `keyword` **__declspec** modifikátor a kompilace s **/CLR: pure** není povolený.

## <a name="example"></a>Příklad

Následující ukázka generuje C3389:

```cpp
// C3389.cpp
// compile with: /clr:pure /c
__declspec(dllexport) int g2 = 0;   // C3389
```