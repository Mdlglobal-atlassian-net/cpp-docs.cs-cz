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
ms.openlocfilehash: a86c0c1a0b70613c6e7749c78f58f6dfb3602d4d
ms.sourcegitcommit: 878a164fe6d550ca81ab87d8425c8d3cd52fe384
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2019
ms.locfileid: "68376276"
---
# <a name="translation-mode-constants"></a>Konstanty režimu posunutí

## <a name="syntax"></a>Syntaxe

```
#include <fcntl.h>
```

## <a name="remarks"></a>Poznámky

`_open` `_setmode` `_sopen`Konstanty manifestu `_O_TEXT`aurčují režim překladu souborů (a) nebo režim překladu datových proudů (). `_O_BINARY`

Povolené hodnoty jsou následující:

|||
|-|-|
`_O_TEXT`  | Otevře soubor v textovém (přeloženém) režimu. Kombinace návratového kanálu návratového řádku (CR-LF) jsou přeloženy do jednoduchého řádku (LF) na vstupu. Znaky kanálu čáry se ve výstupu překládají na kombinace znaků CR-LF. Příkaz CTRL+Z je na vstupu interpretován jako znak konce souboru. V souborech otevřených pro čtení a pro čtení a zápis `fopen` kontroluje klávesovou zkratku CTRL + Z na konci souboru a pokud je to možné, odstraní se. K tomu je potřeba, protože `fseek` použití `ftell` funkcí a k přesunu v rámci souboru končícího klávesami CTRL `fseek` + Z může způsobit nesprávné chování na konci souboru.
`_O_BINARY`  | Otevře soubor v binárním (nepřeloženém) režimu. Výše uvedené překlady jsou potlačeny.
`_O_RAW`  | Stejné jako `_O_BINARY`. Podporováno pro kompatibilitu s C 2,0.

Další informace naleznete v části [vstupně-výstupní operace souboru v textovém a binárním režimu](../c-runtime-library/text-and-binary-mode-file-i-o.md) a [Překlad souborů](../c-runtime-library/file-translation-constants.md).

## <a name="see-also"></a>Viz také:

[_open, _wopen](../c-runtime-library/reference/open-wopen.md)<br/>
[_pipe](../c-runtime-library/reference/pipe.md)<br/>
[_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md)<br/>
[_setmode](../c-runtime-library/reference/setmode.md)<br/>
[Globální konstanty](../c-runtime-library/global-constants.md)
