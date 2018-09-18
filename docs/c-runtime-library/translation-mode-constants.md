---
title: Konstanty režimu posunutí | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _O_BINARY
- _O_TEXT
- _O_RAW
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7c2eff59c8f766b96c1abaeaa2eb9b369720cc75
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46015948"
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