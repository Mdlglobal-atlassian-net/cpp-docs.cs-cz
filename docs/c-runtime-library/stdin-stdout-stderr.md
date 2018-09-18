---
title: stdin, stdout, stderr | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- stdin
- stderr
- stdout
dev_langs:
- C++
helpviewer_keywords:
- stdout function
- standard output stream
- standard error stream
- stdin function
- standard input stream
- stderr function
ms.assetid: badd4735-596d-4498-857c-ec8b7e670e4c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a36d5fd60a19222e6f802e5a14037fb01ff865f5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46071975"
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
|**STDOUT**|Standardní výstup|
|`stderr`|Standardní chyba|

Tyto ukazatele lze použít jako argumenty funkce. Některé funkce, jako například **getchar** a `putchar`, použijte `stdin` a **stdout** automaticky.

Tyto ukazatele jsou konstanty a nelze jí přiřadit nové hodnoty. `freopen` Funkce lze přesměrovat datové proudy souborů na disku nebo s jinými zařízeními. Operační systém můžete přesměrovat standardní vstupní a výstupní na úrovni příkazu programu.

## <a name="see-also"></a>Viz také

[Stream vstupně-výstupních operací](../c-runtime-library/stream-i-o.md)<br/>
[Globální konstanty](../c-runtime-library/global-constants.md)