---
title: Chyba kompilátoru C3519
ms.date: 11/04/2016
f1_keywords:
- C3519
helpviewer_keywords:
- C3519
ms.assetid: ca24b2bc-7e90-4448-ae84-3fedddf9bca7
ms.openlocfilehash: 7e56ff814b1a2dd6ec3cb41db2cbcc21d7dcf2d9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750166"
---
# <a name="compiler-error-c3519"></a>Chyba kompilátoru C3519

' invalid_param ': neplatný parametr pro embedded_idl atributu

Parametr byl předán do atributu `embedded_idl` [#import](../../preprocessor/hash-import-directive-cpp.md), ale kompilátor nerozpoznal parametr.

Jediným parametrům, které jsou povoleny pro `embedded_idl`, jsou `emitidl` a `no_emitidl`.

Následující ukázka generuje C3519:

```cpp
// C3519.cpp
// compile with: /LD
[module(name="MyLib2")];
#import "C:\testdir\bin\importlib.tlb" embedded_idl("no_emitidcl")
// C3519
#import "C:\testdir\bin\importlib.tlb" embedded_idl("no_emitidl")
// OK
```
