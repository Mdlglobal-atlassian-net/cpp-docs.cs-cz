---
title: Konstanty posunutí souboru
ms.date: 11/04/2016
f1_keywords:
- c.constants.file
helpviewer_keywords:
- translation constants
- file translation [C++], constants
- translation, file translation constants
- translation, constants
- constants [C++], file translation mode
- file translation [C++]
ms.assetid: 49b13bf3-442e-4d19-878b-bd1029fa666a
ms.openlocfilehash: ef9b986753de05c45b3071e55f9b163fa5a6a7da
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57743330"
---
# <a name="file-translation-constants"></a>Konstanty posunutí souboru

## <a name="syntax"></a>Syntaxe

```
#include <stdio.h>
```

## <a name="remarks"></a>Poznámky

Tyto konstanty určení režimu překladu (**"b"** nebo **"t"**). Režim je součástí řetězce, který specifikuje typ přístupu (**"r"**, **"w"**, **"a"**, **"r +"**, **"w +"**, **"a +"**).

Režimy překladu jsou následující:

- **t**

   Otevře se v textovém (přeloženém) režimu. V tomto režimu kombinace návrat na začátek řádku return nebo odřádkování (CR-LF) jsou přeloženy (LF) na vstupu a znaků LF jsou přeloženy do na výstupu jako kombinace CR-LF. Příkaz CTRL+Z je na vstupu interpretován jako znak konce souboru. V souborech otevřených pro čtení nebo čtení/zápis `fopen` vyhledává CTRL + Z na konci souboru a odstraní ji, pokud je to možné. Toto je provedeno z důvodu použití `fseek` a `ftell` může způsobit, že funkce pro přesun v rámci souboru končí CTRL + Z `fseek` nesprávné chování na konci souboru.

   > [!NOTE]
   > **t** možnost není součástí standardu ANSI `fopen` a `freopen`. Je rozšířením společnosti Microsoft a neměl by se používat, kde je žádoucí přenositelnost ANSI.

- **b**

   Otevře se v binárním (nepřeloženém) režimu. Překlady uvedené výše jsou potlačeny.

Pokud **t** nebo **b** není uveden v *režimu*, režim překladu definován proměnnou výchozího režimu [_fmode](../c-runtime-library/fmode.md). Další informace o používání textovém a binárním režimu najdete v tématu [textového a binárního režimu souboru vstupně-výstupních operací](../c-runtime-library/text-and-binary-mode-file-i-o.md).

## <a name="see-also"></a>Viz také:

[_fdopen, _wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)<br/>
[fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md)<br/>
[freopen, _wfreopen](../c-runtime-library/reference/freopen-wfreopen.md)<br/>
[_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)<br/>
[Globální konstanty](../c-runtime-library/global-constants.md)
