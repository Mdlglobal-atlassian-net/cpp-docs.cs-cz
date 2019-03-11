---
title: stdin, stdout, stderr
ms.date: 10/23/2018
f1_keywords:
- stdin
- stderr
- stdout
helpviewer_keywords:
- stdout function
- standard output stream
- standard error stream
- stdin function
- standard input stream
- stderr function
ms.assetid: badd4735-596d-4498-857c-ec8b7e670e4c
ms.openlocfilehash: 5de1ff01282f30ad133f909cb87f5d7c8d521ae5
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57741941"
---
# <a name="stdin-stdout-stderr"></a>stdin, stdout, stderr

## <a name="syntax"></a>Syntaxe

```
FILE *stdin;
FILE *stdout;
FILE *stderr;
#include <stdio.h>
```

## <a name="remarks"></a>Poznámky

Jedná se o standardních datových proudů pro vstupní, výstupní a chybový výstup.

Ve výchozím nastavení je standardní vstup přečtený z klávesnice, zatímco standardní výstup a chyby jsou zobrazeny na obrazovce.

Následující ukazatele datového proudu jsou k dispozici pro přístup z více vláken standardní:

|Ukazatel|Stream|
|-------------|------------|
|`stdin`|Standardní vstup|
|`stdout`|Standardní výstup|
|`stderr`|Standardní chyba|

Tyto ukazatele lze použít jako argumenty funkce. Některé funkce, jako například [getchar](../c-runtime-library/reference/getchar-getwchar.md) a [putchar](../c-runtime-library/reference/putchar-putwchar.md), použijte `stdin` a `stdout` automaticky.

Tyto ukazatele jsou konstanty a nelze jí přiřadit nové hodnoty. [Freopen](../c-runtime-library/reference/freopen-wfreopen.md) funkce lze přesměrovat datové proudy souborů na disku nebo s jinými zařízeními. Operační systém můžete přesměrovat standardní vstupní a výstupní na úrovni příkazu programu.

## <a name="see-also"></a>Viz také:

[Stream vstupně-výstupních operací](../c-runtime-library/stream-i-o.md)<br/>
[Globální konstanty](../c-runtime-library/global-constants.md)
