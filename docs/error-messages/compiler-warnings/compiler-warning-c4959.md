---
title: C4959 upozornění kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4959
dev_langs:
- C++
helpviewer_keywords:
- C4959
ms.assetid: 3a128f3e-4d8a-4565-ba1a-5d32fdeb5982
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2819664fa94ca777339156dc9a31da17b991c6da
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34705161"
---
# <a name="compiler-warning-c4959"></a>C4959 upozornění kompilátoru

> nelze definovat nespravované struktura '*typu*, v/CLR: safe vzhledem k tomu, že přístup k jeho členy vypočítá neověřitelný kód

## <a name="remarks"></a>Poznámky

Přístup k členem nespravovaný typ vytvoří bitovou kopii neověřitelný (peverify.exe).

Další informace najdete v tématu [prázdná a ověřitelný kód (C + +/ CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

**/CLR: safe** – možnost kompilátoru je zastaralé v sadě Visual Studio 2015 a nepodporované v Visual Studio 2017.

Toto upozornění se objeví jako chybu a můžete je třeba zakázat pomocí [upozornění](../../preprocessor/warning.md) – Direktiva pragma nebo [/wd](../../build/reference/compiler-option-warning-level.md) – možnost kompilátoru.

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