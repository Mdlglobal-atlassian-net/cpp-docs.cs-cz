---
title: Upozornění (úroveň 4) C4001 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4001
dev_langs:
- C++
helpviewer_keywords:
- C4001
ms.assetid: 414a47fe-d597-425e-9374-6a569231dc0a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c325656b9e61ee324a3b9f171413f1020440f9ab
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025409"
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