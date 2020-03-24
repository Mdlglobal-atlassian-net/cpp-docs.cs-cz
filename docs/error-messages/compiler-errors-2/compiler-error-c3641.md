---
title: Chyba kompilátoru C3641
ms.date: 11/04/2016
f1_keywords:
- C3641
helpviewer_keywords:
- C3641
ms.assetid: e8d3613e-5e8d-46fe-a516-eb7d1de7cd21
ms.openlocfilehash: 44356fb1a1818a02102d23e6b308457f2f39506b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200509"
---
# <a name="compiler-error-c3641"></a>Chyba kompilátoru C3641

> '*Function*': Neplatná konvence volání ' calling_convention ' pro funkci zkompilovanou pomocí/CLR: pure nebo/CLR: Safe

## <a name="remarks"></a>Poznámky

Možnosti **/clr: Pure** a **/clr: Safe** jsou zastaralé v aplikaci Visual Studio 2015 a nejsou podporovány v aplikaci Visual Studio 2017.

Pouze konvence volání [__clrcall](../../cpp/clrcall.md) je povolena s možností [/clr: Pure](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3641:

```cpp
// C3641.cpp
// compile with: /clr:pure /c
void __cdecl f() {}   // C3641
```
