---
title: Chyba kompilátoru C2434
ms.date: 11/04/2016
f1_keywords:
- C2434
helpviewer_keywords:
- C2434
ms.assetid: 01329e26-7c74-4219-b74f-69e3a40c9738
ms.openlocfilehash: c73a8d4fcde945ddf2495cc2d0d7dc47216f2db3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166331"
---
# <a name="compiler-error-c2434"></a>Chyba kompilátoru C2434

> "*symbol*': symbol deklarovaný s: __declspec(process) se nedá dynamicky inicializovat v/CLR: pure režimu

## <a name="remarks"></a>Poznámky

**/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015 a není podporována v sadě Visual Studio 2017.

Není možné dynamicky inicializovat proměnnou na úrovni jednotlivého procesu v rámci **/CLR: pure**. Další informace najdete v tématu [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) a [procesu](../../cpp/process.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C2434. Chcete-li vyřešit tento problém, použijte k inicializaci konstanty `process` proměnné.

```cpp
// C2434.cpp
// compile with: /clr:pure /c
int f() { return 0; }
__declspec(process) int i = f();   // C2434
__declspec(process) int i2 = 0;   // OK
```