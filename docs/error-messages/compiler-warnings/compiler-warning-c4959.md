---
title: Upozornění kompilátoru C4959
ms.date: 11/04/2016
f1_keywords:
- C4959
helpviewer_keywords:
- C4959
ms.assetid: 3a128f3e-4d8a-4565-ba1a-5d32fdeb5982
ms.openlocfilehash: 646347dec7bc2bac7fa73c8f754d2f9549cb2ba6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50473655"
---
# <a name="compiler-warning-c4959"></a>Upozornění kompilátoru C4959

> nejde definovat nespravovaný struct '*typ*"v/CLR: safe vzhledem k tomu, že přístup k jeho členům vrací neověřitelný kód

## <a name="remarks"></a>Poznámky

Přístup ke členovi nespravovaným typem vytvoří bitovou kopii nelze ověřit (peverify.exe).

Další informace najdete v tématu [prázdná a ověřitelný kód (C + +/ CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

**/CLR: safe** – možnost kompilátoru je zastaralé v sadě Visual Studio 2015 a není podporována v sadě Visual Studio 2017.

Toto upozornění je vyvoláno jako chyba a pomocí se dají zakázat [upozornění](../../preprocessor/warning.md) – Direktiva pragma nebo [/wd](../../build/reference/compiler-option-warning-level.md) – možnost kompilátoru.

## <a name="example"></a>Příklad

Následující ukázka generuje C4959:

```cpp
// C4959.cpp
// compile with: /clr:safe

// Uncomment the following line to resolve.
// #pragma warning( disable : 4959 )
struct X {
   int data;
};

int main() {
   X x;
   x.data = 10;   // C4959
}
```