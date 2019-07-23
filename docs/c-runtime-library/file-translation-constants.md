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
ms.openlocfilehash: ed2fae935850837ebace880d78c206754b3061bd
ms.sourcegitcommit: 878a164fe6d550ca81ab87d8425c8d3cd52fe384
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2019
ms.locfileid: "68375915"
---
# <a name="file-translation-constants"></a>Konstanty posunutí souboru

## <a name="syntax"></a>Syntaxe

```
#include <stdio.h>
```

## <a name="remarks"></a>Poznámky

Tyto konstanty určují režim překladu ( **"b"** nebo **"t"** ). Tento režim je součástí řetězce určujícího typ přístupu ( **"r"** , **"w"** , **"a"** , **"r +"** , **"w +** ", **"a +"** ).

Režimy překladu jsou následující:

- **t**

   Otevře se v textovém (přeloženém) režimu. V tomto režimu jsou kombinace pro návrat vozíku (CR-LF) přeloženy do jednoduchých čar (LF) na vstupu a znaky LF jsou přeloženy na výstup do kombinací znaků CR-LF. Příkaz CTRL+Z je na vstupu interpretován jako znak konce souboru. V souborech otevřených pro čtení nebo čtení a zápis `fopen` vyhledá klávesovou zkratku CTRL + Z na konci souboru a pokud je to možné, odebere ji. K tomu je potřeba, protože `fseek` použití `ftell` funkcí a k přesunu v rámci souboru končícího klávesami CTRL `fseek` + Z může způsobit nesprávné chování na konci souboru.

   > [!NOTE]
   > Možnost **t** není součástí standardu ANSI pro `fopen` a. `freopen` Je to rozšíření Microsoftu a nemělo by se používat tam, kde je žádoucí přenositelnost ANSI.

- **b**

   Otevře se v binárním (nepřeloženém) režimu. Výše uvedené překlady jsou potlačeny.

Pokud **t** nebo **b** není uveden v *režimu*, je režim překladu definován pomocí proměnné ve výchozím režimu [_fmode](../c-runtime-library/fmode.md). Další informace o používání textových a binárních režimů najdete v tématu [vstupně-výstupní operace se soubory v textovém a binárním režimu](../c-runtime-library/text-and-binary-mode-file-i-o.md).

## <a name="see-also"></a>Viz také:

[_fdopen, _wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)<br/>
[fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md)<br/>
[freopen, _wfreopen](../c-runtime-library/reference/freopen-wfreopen.md)<br/>
[_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)<br/>
[Globální konstanty](../c-runtime-library/global-constants.md)
