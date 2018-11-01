---
title: signal – konstanty
ms.date: 11/04/2016
f1_keywords:
- SIGTERM
- SIGFPE
- SIGABRT
- SIGILL
- SIGINT
- SIGSEGV
helpviewer_keywords:
- SIGTERM constant
- SIGABRT constant
- SIGSEGV constant
- SIGFPE constant
- SIGINT constant
- signal constants
- SIGILL constant
ms.assetid: a3b39281-dae7-4e44-8d68-e6a610c669dd
ms.openlocfilehash: 1046a12fa0f250b348e6ff171c8865e3eb5ff4b3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50482657"
---
# <a name="signal-constants"></a>signal – konstanty

## <a name="syntax"></a>Syntaxe

```
#include <signal.h>
```

## <a name="remarks"></a>Poznámky

`sig` Argument musí být jednou z konstant manifestu uvedené níže (definovaná v SIGNÁL. H).

|||
|-|-|
|SIGABRT|Abnormální ukončení. Výchozí akce ukončí volající program s ukončovacím kódem 3.  |
|SIGABRT_COMPAT|Stejné jako SIGABRT. Z důvodu kompatibility s jinými platformami.  |
|SIGFPE|Chyba s plovoucí desetinnou čárkou, například přetečení, dělení nulou či neplatná operace. Výchozí akce ukončí volající program.  |
|SIGILL|Neplatná instrukce. Výchozí akce ukončí volající program.  |
|SIGINT|Přerušení CTRL + C. Výchozí akce ukončí volající program s ukončovacím kódem 3.  |
|SIGSEGV|Neplatný přístup k úložišti. Výchozí akce ukončí volající program.  |
|SIGTERM|Žádost o ukončení odeslána programu. Výchozí akce ukončí volající program s ukončovacím kódem 3.  |
|SIG_ERR|Návratový typ z signál udávající chybu došlo k chybě.  |

## <a name="see-also"></a>Viz také

[signal](../c-runtime-library/reference/signal.md)<br/>
[raise](../c-runtime-library/reference/raise.md)<br/>
[Globální konstanty](../c-runtime-library/global-constants.md)