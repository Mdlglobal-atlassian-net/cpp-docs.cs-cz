---
title: Upozornění kompilátoru C4956
ms.date: 11/04/2016
f1_keywords:
- C4956
helpviewer_keywords:
- C4956
ms.assetid: 9154f2d1-d49f-4e07-90d2-0e9bc028011a
ms.openlocfilehash: c15de8b22f56a2555cc763a45153139b1df01a31
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62280838"
---
# <a name="compiler-warning-c4956"></a>Upozornění kompilátoru C4956

> "*typ*': Tento typ není ověřitelný

## <a name="remarks"></a>Poznámky

Toto upozornění je generováno při [/CLR: safe](../../build/reference/clr-common-language-runtime-compilation.md) určena a váš kód obsahuje typ, který není možné ověřit. **/CLR: safe** – možnost kompilátoru je zastaralé v sadě Visual Studio 2015 a není podporována v sadě Visual Studio 2017.

Další informace najdete v tématu [prázdná a ověřitelný kód (C++vyhodnocovací)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

Toto upozornění je vyvoláno jako chyba a pomocí se dají zakázat [upozornění](../../preprocessor/warning.md) – Direktiva pragma nebo [/wd](../../build/reference/compiler-option-warning-level.md) – možnost kompilátoru.

## <a name="example"></a>Příklad

Následující ukázka generuje C4956:

```cpp
// C4956.cpp
// compile with: /clr:safe
int* p;   // C4956
```