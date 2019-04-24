---
title: Upozornění kompilátoru C4335
ms.date: 11/04/2016
f1_keywords:
- C4335
helpviewer_keywords:
- C4335
ms.assetid: e66467ad-a10b-4438-8c7c-e8e8d11d39bb
ms.openlocfilehash: 43c2f5d9092cdbad14e429349bd7d04e236b75e4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62151848"
---
# <a name="compiler-warning-c4335"></a>Upozornění kompilátoru C4335

Zjistil se formát souborů Mac: převeďte prosím zdrojový soubor do formátu DOS nebo UNIX

Znak ukončení řádku prvního řádku zdrojového souboru je styl Macintosh ('\r;) na rozdíl od systému UNIX ('\n') nebo DOS ("\r\n").

Toto upozornění je vždy vyvoláno jako chyby.  Zobrazit [upozornění](../../preprocessor/warning.md) direktivu pragma pro informace o tom, jak toto upozornění vypněte.  Navíc se objeví toto upozornění pouze jednou za kompilace. Proto pokud existuje více `#include` direktivy, které určují soubory ve formátu Macintosh C4335 se vystavit pouze jednou.

Jeden způsob, jak vygenerovat soubory ve formátu Macintosh je použít **pokročilé nastavení uložení** (na **souboru** nabídky) v sadě Visual Studio.

## <a name="example"></a>Příklad

Následující ukázka generuje C4335.

```
// C4335 expected
#include "c4335.h"   // assume both include files are in Macintosh format
#include "c4335_2.h"
```