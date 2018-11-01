---
title: Upozornění linkerů LNK4224
ms.date: 11/04/2016
f1_keywords:
- LNK4224
helpviewer_keywords:
- LNK4224
ms.assetid: 8624b70e-0b93-43cf-b457-834d38632d0b
ms.openlocfilehash: eb0a019cc80e5218a52697b8bcd5e91b811d04d3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50465322"
---
# <a name="linker-tools-warning-lnk4224"></a>Upozornění linkerů LNK4224

> *možnost* se už nepodporuje. ignoruje

## <a name="remarks"></a>Poznámky

– Možnost linkeru neplatný, zastaralé byl zadán a ignorován.

Například LNK4224 může dojít, pokud Comment direktiva se zobrazí ve. Knihovna Comment – direktiva by byly přidané prostřednictvím [komentáře (C/C++)](../../preprocessor/comment-c-cpp.md) – Direktiva pragma, pomocí možnosti exestr zastaralé. Pomocí dumpbin [/ALL](../../build/reference/all.md) zobrazíte linkeru direktivy v souboru .obj.

Pokud je to možné upravte zdroj .obj a odebrat direktivy pragma. Pokud toto upozornění ignorovat, je možné, že .executable zkompilovaná **/CLR: pure** nebude fungovat podle očekávání. **/CLR: pure** – možnost kompilátoru je zastaralé v sadě Visual Studio 2015 a není podporována v sadě Visual Studio 2017.

## <a name="example"></a>Příklad

Následující ukázka generuje LNK4224.

```cpp
// LNK4224.cpp
// compile with: /c /Zi
// post-build command: link LNK4224.obj /debug /debugtype:map
int main () {
   return 0;
}
```