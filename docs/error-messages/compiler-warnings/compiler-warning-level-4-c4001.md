---
title: Kompilátor upozornění (úroveň 4) C4001
ms.date: 11/04/2016
f1_keywords:
- C4001
helpviewer_keywords:
- C4001
ms.assetid: 414a47fe-d597-425e-9374-6a569231dc0a
ms.openlocfilehash: dd18dc27ee13eab05ea0253c8ebcc990105c15c9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401485"
---
# <a name="compiler-warning-level-4-c4001"></a>Kompilátor upozornění (úroveň 4) C4001

používá se nestandardní rozšíření 'jednořádkový komentář' byl použit.

> [!NOTE]
> Toto upozornění je v sadě Visual Studio 2017 verze 15.5 odebrat, protože standard v C99 jsou Jednořádkové komentáře.

Jednořádkové komentáře jsou standard v jazyce C++ a standardní při zahajování C s normou C99.
V části striktní kompatibility ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)), soubory jazyka C, které obsahují Jednořádkové komentáře, generovat C4001 z důvodu použití používá se nestandardní rozšíření. Protože jsou v jazyce C++ standardní Jednořádkové komentáře, soubory jazyka C, které obsahují Jednořádkové komentáře neposkytují C4001 při kompilaci s rozšířeními společnosti Microsoft (/Ze).

## <a name="example"></a>Příklad

Chcete-li upozornění vypněte, Odkomentujte [#pragma warning(disable:4001)](../../preprocessor/warning.md).

```
// C4001.cpp
// compile with: /W4 /Za /TC
// #pragma warning(disable:4001)
int main()
{
   // single-line comment in main
   // C4001
}
```