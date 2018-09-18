---
title: Upozornění kompilátoru C4335 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4335
dev_langs:
- C++
helpviewer_keywords:
- C4335
ms.assetid: e66467ad-a10b-4438-8c7c-e8e8d11d39bb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d2b28909d0c4b663fffeacbec58ad694131bb008
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036576"
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