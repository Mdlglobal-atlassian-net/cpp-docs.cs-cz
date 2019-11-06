---
title: Upozornění kompilátoru C4335
ms.date: 11/04/2016
f1_keywords:
- C4335
helpviewer_keywords:
- C4335
ms.assetid: e66467ad-a10b-4438-8c7c-e8e8d11d39bb
ms.openlocfilehash: ccb00118d0c6895eee84976bb01472ea2f98353d
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627125"
---
# <a name="compiler-warning-c4335"></a>Upozornění kompilátoru C4335

Zjistil se formát souboru Mac: Převeďte prosím zdrojový soubor na formát DOS nebo UNIX.

Znak ukončení řádku prvního řádku zdrojového souboru je stylem Macintosh ("\r") na rozdíl od UNIXu (\n) nebo DOS ("\r\n").

Toto upozornění je vždy vyvoláno jako chyba.  Informace o tom, jak toto upozornění zakázat, naleznete v tématu [Upozornění](../../preprocessor/warning.md) pragma.  Toto upozornění je také vydáváno pouze jednou za kompilantu. Proto pokud existuje více direktiv `#include`, které určují soubory ve formátu počítače Macintosh, C4335 se vydá jenom jednou.

Jedním ze způsobů, jak generovat soubory ve formátu systému Macintosh, je použití **možností upřesnění Uložit** (v nabídce **soubor** ) v aplikaci Visual Studio.

## <a name="example"></a>Příklad

Následující ukázka generuje C4335.

```cpp
// C4335 expected
#include "c4335.h"   // assume both include files are in Macintosh format
#include "c4335_2.h"
```
