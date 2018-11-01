---
title: Upozornění kompilátoru C4936
ms.date: 11/04/2016
f1_keywords:
- C4936
helpviewer_keywords:
- C4936
ms.assetid: 6676de35-bf1b-4d0b-a70f-b5734130336c
ms.openlocfilehash: bbb69cccbf93be6e97d13db5008780f57e63f9da
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50537563"
---
# <a name="compiler-warning-c4936"></a>Upozornění kompilátoru C4936

> Tato možnost __declspec je podporovaná jenom při kompilaci s parametrem/CLR nebo/CLR: pure

## <a name="remarks"></a>Poznámky

**/CLR: pure** – možnost kompilátoru je zastaralé v sadě Visual Studio 2015 a není podporována v sadě Visual Studio 2017.

A `__declspec` ale, že byl použit modifikátor `__declspec` modifikátor platí jenom při kompilaci s jedním z [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) možnosti.

Další informace najdete v tématu [appdomain](../../cpp/appdomain.md) a [procesu](../../cpp/process.md).

C4936 je vždy vyvoláno jako chyba.  Můžete zakázat C4936 s [upozornění](../../preprocessor/warning.md) direktivy pragma.

## <a name="example"></a>Příklad

Následující ukázka generuje C4936:

```cpp
// C4936.cpp
// compile with: /c
// #pragma warning (disable : 4936)
__declspec(process) int i;   // C4936
__declspec(appdomain) int j;   // C4936
```