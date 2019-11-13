---
title: Upozornění kompilátoru (úroveň 1) C4545
ms.date: 11/04/2016
f1_keywords:
- C4545
helpviewer_keywords:
- C4545
ms.assetid: 43f8f34f-ed46-4661-95c0-c588c577ff73
ms.openlocfilehash: 39770a8c7ad5241ed625575c94dc19bf91e3b5bd
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966431"
---
# <a name="compiler-warning-level-1-c4545"></a>Upozornění kompilátoru (úroveň 1) C4545

výraz před čárkou vyhodnocuje na funkci, která nemá k dispozici seznam argumentů

Kompilátor zjistil výraz čárky ve formátu nesprávně vytvořeného výrazu.

Toto upozornění je ve výchozím nastavení vypnuté. Další informace najdete v tématu [Upozornění kompilátoru, která jsou ve výchozím nastavení vypnutá](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

Následující ukázka generuje C4545:

```cpp
// C4545.cpp
// compile with: /W1
#pragma warning (default : 4545)

void f() { }

int main()
{
   *(&f), 10;   // C4545
   // try the following line instead
   // (*(&f))(), 10;
}
```