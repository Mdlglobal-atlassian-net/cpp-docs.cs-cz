---
title: Upozornění kompilátoru (úroveň 4) C4001
ms.date: 11/04/2016
f1_keywords:
- C4001
helpviewer_keywords:
- C4001
ms.assetid: 414a47fe-d597-425e-9374-6a569231dc0a
ms.openlocfilehash: fc4ae55c5d25719e930a7435e0f9bf3ee2071a21
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541630"
---
# <a name="compiler-warning-level-4-c4001"></a>Upozornění kompilátoru (úroveň 4) C4001

nestandardní rozšíření: použil se Jednořádkový komentář.

> [!NOTE]
> Toto upozornění je odebráno v aplikaci Visual Studio 2017 verze 15,5, protože jednořádkové komentáře jsou standardně v C99.

Jednořádkové komentáře jsou standardní v C++ jazyce a Standard jazyka C počínaje C99.
V rámci striktní kompatibility ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)), soubory C, které obsahují Jednořádkový komentář, vygenerujte C4001 z důvodu použití nestandardního rozšíření. Vzhledem k tomu, že víceřádkové komentáře C++jsou standardní v, soubory C obsahující Jednořádkový komentář nevytváří C4001 při kompilování s rozšířeními Microsoft (/ze).

## <a name="example"></a>Příklad

Chcete-li zakázat upozornění, odkomentujte [#pragma upozornění (zakázat: 4001)](../../preprocessor/warning.md).

```cpp
// C4001.cpp
// compile with: /W4 /Za /TC
// #pragma warning(disable:4001)
int main()
{
   // single-line comment in main
   // C4001
}
```