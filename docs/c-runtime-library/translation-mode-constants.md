---
title: Konstanty režimu posunutí
ms.date: 11/04/2016
f1_keywords:
- _O_BINARY
- _O_TEXT
- _O_RAW
helpviewer_keywords:
- O_BINARY constant
- O_TEXT constant
- O_RAW constant
- _O_TEXT constant
- _O_RAW constant
- translation constants
- _O_BINARY constant
- translation, constants
- translation, modes
- translation modes (file I/O)
ms.assetid: a5993bf4-7e7a-47f9-83c3-e46332b85579
ms.openlocfilehash: 25588758e682409bad0a6cb2723304275f00c25e
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2018
ms.locfileid: "51519721"
---
# <a name="translation-mode-constants"></a>Konstanty režimu posunutí

## <a name="syntax"></a>Syntaxe

```

#include <fcntl.h>
```

## <a name="remarks"></a>Poznámky

`_O_BINARY` a `_O_TEXT` konstant manifestu určení režimu překladu pro soubory (`_open` a `_sopen`) nebo režim překladu pro datové proudy (`_setmode`).

Povolené hodnoty jsou následující:

|||
|-|-|
`_O_TEXT`  | Otevře soubor v textovém (přeloženém) režimu. Návrat na začátek – kombinace odřádkování (CR-LF) jsou přeloženy do jednoho konce řádku (LF) na vstupu. Znaky odřádkování jsou přeloženy do na výstupu jako kombinace CR-LF. Příkaz CTRL+Z je na vstupu interpretován jako znak konce souboru. V souborech otevřených pro čtení a čtení/zápis `fopen` vyhledává CTRL + Z na konci souboru a odstraní ji, pokud je to možné. Toto je provedeno z důvodu použití `fseek` a `ftell` může způsobit, že funkce pro přesun v rámci souboru končí CTRL + Z `fseek` nesprávné chování na konci souboru.
`_O_BINARY`  | Otevře soubor v binárním (nepřeloženém) režimu. Překlady uvedené výše jsou potlačeny.
`_O_RAW`  | Stejné jako `_O_BINARY`. Nepodporuje z důvodu kompatibility C 2.0.

Další informace najdete v tématu [textového a binárního režimu souboru vstupně-výstupních operací](../c-runtime-library/text-and-binary-mode-file-i-o.md) a [překladu souboru](../c-runtime-library/file-translation-constants.md).

## <a name="see-also"></a>Viz také

[_open, _wopen](../c-runtime-library/reference/open-wopen.md)<br/>
[_pipe](../c-runtime-library/reference/pipe.md)<br/>
[_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md)<br/>
[_setmode](../c-runtime-library/reference/setmode.md)<br/>
[Globální konstanty](../c-runtime-library/global-constants.md)