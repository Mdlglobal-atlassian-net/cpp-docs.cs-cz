---
title: Chyba kompilátoru C3862
ms.date: 11/04/2016
f1_keywords:
- C3862
helpviewer_keywords:
- C3862
ms.assetid: ba547366-4189-4077-8c00-ab45e08a9533
ms.openlocfilehash: 0b9c1e1213949d7d700094caa6687232df881ce6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165480"
---
# <a name="compiler-error-c3862"></a>Chyba kompilátoru C3862

> '*Function*': nespravovanou funkci nelze zkompilovat s možností/CLR: pure nebo/CLR: Safe

## <a name="remarks"></a>Poznámky

Možnosti **/clr: Pure** a **/clr: Safe** jsou zastaralé v aplikaci Visual Studio 2015 a nejsou podporovány v aplikaci Visual Studio 2017.

Kompilace s možností **/clr: Pure** nebo **/clr: Safe** vytvoří obrázek pouze v jazyce MSIL, obrázek bez nativního (nespravovaného) kódu.  Proto nemůžete použít direktivu pragma `unmanaged` v kompilaci **/clr: Pure** nebo **/clr: Safe** .

Další informace naleznete v tématu [/CLR (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md) a [Managed, unmanaged](../../preprocessor/managed-unmanaged.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3862:

```cpp
// C3862.cpp
// compile with: /clr:pure /c
#pragma unmanaged
void f() {}   // C3862
```
