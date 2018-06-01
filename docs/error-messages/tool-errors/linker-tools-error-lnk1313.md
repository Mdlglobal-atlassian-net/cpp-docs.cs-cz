---
title: Chyba linkerů Lnk1313 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1313
dev_langs:
- C++
helpviewer_keywords:
- LNK1313
ms.assetid: 5df0b72e-bb3f-428c-8d84-6084238f9827
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d6a896c8ba012c69755c5292475b2d155ad92066
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34705085"
---
# <a name="linker-tools-error-lnk1313"></a>Chyba linkerů LNK1313

> IJW nebo nativního modulu došlo k detekci; nelze propojit s čistě moduly

## <a name="remarks"></a>Poznámky

Aktuální verze Visual C++ nepodporuje propojování nativní nebo smíšené spravované/nativní .obj soubory s soubory .obj kompilovat s **/CLR: pure**.

**/CLR: pure** – možnost kompilátoru je zastaralé v sadě Visual Studio 2015 a nepodporované v Visual Studio 2017.

## <a name="example"></a>Příklad

```cpp
// LNK1313.cpp
// compile with: /c /clr:pure
// a pure module
int main() {}
```

## <a name="example"></a>Příklad

```cpp
// LNK1313_b.cpp
// compile with: /c /clr
// an IJW module
void test(){}
```

## <a name="example"></a>Příklad

Následující příklad vytvoří LNK1313.

```cpp
// LNK1313_c.cpp
// compile with: /link LNK1313.obj LNK1313_b.obj
// LNK1313 warning expected
```