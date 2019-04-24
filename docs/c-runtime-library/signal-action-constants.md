---
title: signal – konstanty akce
ms.date: 11/04/2016
f1_keywords:
- SIG_IGN
- SIG_DFL
helpviewer_keywords:
- signal action constants
- SIG_IGN constant
- SIG_DFL constant
ms.assetid: c3cb4f15-d39e-4d9d-84f9-0d33e3eb5993
ms.openlocfilehash: 4ff79626d576a05744336d36f99caf95d9b9902d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62267986"
---
# <a name="signal-action-constants"></a>signal – konstanty akce

Akce provedená při přijetí signál přerušení závisí na hodnotu `func`.

## <a name="syntax"></a>Syntaxe

```
#include <signal.h>
```

## <a name="remarks"></a>Poznámky

`func` Argument musí být adresa funkce nebo jednu z konstant manifestu uvedené níže a podle SIGNÁLU. H.

|||
|-|-|
| `SIG_DFL`  | Použije výchozí systémové nastavení odpověď. Pokud volající program používá vstupně-výstupní datový proud, nejsou vyprázdní vyrovnávací paměti vytvořené pomocí knihovny run-time.  |
| `SIG_IGN`  | Ignoruje signál přerušení. Tato hodnota by měly mít nikdy pro `SIGFPE`, protože je ponecháno stav s plovoucí desetinnou čárkou procesu nedefinovaný.  |
| `SIG_SGE`  | Označuje, že signál, který se stala chyba.  |
| `SIG_ACK`  | Označuje, že bylo přijato potvrzení.  |
| `SIG_ERR`  | Návratový typ z signál udávající chybu došlo k chybě.  |

## <a name="see-also"></a>Viz také:

[signal](../c-runtime-library/reference/signal.md)<br/>
[Globální konstanty](../c-runtime-library/global-constants.md)
