---
title: Upozornění kompilátoru C4957
ms.date: 11/04/2016
f1_keywords:
- C4957
helpviewer_keywords:
- C4957
ms.assetid: a18c52d4-23e2-44f1-b4b5-f7fa5a7f3987
ms.openlocfilehash: 9afdd213baadd907afacde0ff7f14f3c78bc60a5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528255"
---
# <a name="compiler-warning-c4957"></a>Upozornění kompilátoru C4957

> "*přetypování*': explicitní přetypování z typu '*cast_from*"do"*cast_to*" nejde ověřit

## <a name="remarks"></a>Poznámky

Přetypování způsobí bitovou kopii nelze ověřit.

Některá přetypování je bezpečné (například `static_cast` , který aktivuje uživatelem definované převody a `const_cast`). A [safe_cast](../../windows/safe-cast-cpp-component-extensions.md) je zaručeno, že vytvoří ověřitelný kód.

Další informace najdete v tématu [prázdná a ověřitelný kód (C + +/ CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

**/CLR: safe** – možnost kompilátoru je zastaralé v sadě Visual Studio 2015 a není podporována v sadě Visual Studio 2017.

Toto upozornění je vyvoláno jako chyba a pomocí se dají zakázat [upozornění](../../preprocessor/warning.md) – Direktiva pragma nebo [/wd](../../build/reference/compiler-option-warning-level.md) – možnost kompilátoru.

## <a name="example"></a>Příklad

Následující ukázka generuje C4957:

```cpp
// C4957.cpp
// compile with: /clr:safe
// #pragma warning( disable : 4957 )
using namespace System;
int main() {
   Object ^ o = "Hello, World!";
   String ^ s = static_cast<String^>(o);   // C4957
   String ^ s2 = safe_cast<String^>(o);   // OK
}
```