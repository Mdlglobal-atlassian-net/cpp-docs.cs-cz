---
title: Chyba kompilátoru C2434
ms.date: 11/04/2016
f1_keywords:
- C2434
helpviewer_keywords:
- C2434
ms.assetid: 01329e26-7c74-4219-b74f-69e3a40c9738
ms.openlocfilehash: 869db3b49075fa477860e045e59306e22a381ca4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205460"
---
# <a name="compiler-error-c2434"></a>Chyba kompilátoru C2434

> *symbol*: symbol deklarovaný pomocí __declspec (Process) se nedá dynamicky inicializovat v režimu/CLR: Pure.

## <a name="remarks"></a>Poznámky

Možnosti **/clr: Pure** a **/clr: Safe** jsou zastaralé v aplikaci Visual Studio 2015 a nejsou podporovány v aplikaci Visual Studio 2017.

Není možné dynamicky inicializovat proměnnou pro proces v rámci **/clr: Pure**. Další informace naleznete v tématu [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) a [Process](../../cpp/process.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C2434. Chcete-li tento problém vyřešit, použijte k inicializaci `process` proměnných konstanty.

```cpp
// C2434.cpp
// compile with: /clr:pure /c
int f() { return 0; }
__declspec(process) int i = f();   // C2434
__declspec(process) int i2 = 0;   // OK
```
