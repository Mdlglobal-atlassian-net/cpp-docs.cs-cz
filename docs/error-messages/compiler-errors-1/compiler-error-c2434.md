---
title: C2434 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2434
dev_langs:
- C++
helpviewer_keywords:
- C2434
ms.assetid: 01329e26-7c74-4219-b74f-69e3a40c9738
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 45f9ccdef84713883c53dab0e7caf3b1519628de
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704224"
---
# <a name="compiler-error-c2434"></a>C2434 chyby kompilátoru

> '*symbol*': symbol deklarovat s __declspec(process) nelze inicializovat dynamicky v/CLR: pure režimu

## <a name="remarks"></a>Poznámky

**/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015 a nepodporované v Visual Studio 2017.

Není možné dynamicky inicializovat proměnnou na proces pod **/CLR: pure**. Další informace najdete v tématu [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) a [proces](../../cpp/process.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C2434. Chcete-li tento problém vyřešit, použijte k chybě při inicializaci konstanty `process` proměnné.

```cpp
// C2434.cpp
// compile with: /clr:pure /c
int f() { return 0; }
__declspec(process) int i = f();   // C2434
__declspec(process) int i2 = 0;   // OK
```