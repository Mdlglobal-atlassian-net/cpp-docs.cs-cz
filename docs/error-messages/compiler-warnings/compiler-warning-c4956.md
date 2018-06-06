---
title: C4956 upozornění kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4956
dev_langs:
- C++
helpviewer_keywords:
- C4956
ms.assetid: 9154f2d1-d49f-4e07-90d2-0e9bc028011a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: be92eb948e31a0a5367f92f5c2ed59baac2bd39b
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34703701"
---
# <a name="compiler-warning-c4956"></a>C4956 upozornění kompilátoru

> '*typ*': Tento typ není ověřitelný

## <a name="remarks"></a>Poznámky

Toto upozornění je generováno při [/CLR: safe](../../build/reference/clr-common-language-runtime-compilation.md) je zadán a váš kód obsahuje typ, který není ověřitelný. **/CLR: safe** – možnost kompilátoru je zastaralé v sadě Visual Studio 2015 a nepodporované v Visual Studio 2017.

Další informace najdete v tématu [prázdná a ověřitelný kód (C + +/ CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

Toto upozornění se objeví jako chybu a můžete je třeba zakázat pomocí [upozornění](../../preprocessor/warning.md) – Direktiva pragma nebo [/wd](../../build/reference/compiler-option-warning-level.md) – možnost kompilátoru.

## <a name="example"></a>Příklad

Následující ukázka generuje C4956:

```cpp
// C4956.cpp
// compile with: /clr:safe
int* p;   // C4956
```