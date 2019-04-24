---
title: Konstanty přístupu pro čtení a zápis do souboru
ms.date: 11/04/2016
f1_keywords:
- c.constants.file
helpviewer_keywords:
- read/write access constants
- write access constants
- access constants for file read/write
- constants [C++], file attributes
- file read/write access constants
ms.assetid: 56cd1d22-39a5-4fcf-bea2-7046d249e8ee
ms.openlocfilehash: 0dfbc925c5252724cbb1caad58470849915242a9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62289894"
---
# <a name="file-readwrite-access-constants"></a>Konstanty přístupu pro čtení a zápis do souboru

## <a name="syntax"></a>Syntaxe

```
#include <stdio.h>
```

## <a name="remarks"></a>Poznámky

Tyto konstanty zadejte typ přístupu ("a", "r" nebo "w") požadované pro soubor. Oba [režim překladu](../c-runtime-library/file-translation-constants.md) ("b" nebo "t") a [potvrzení na disku režimu](../c-runtime-library/commit-to-disk-constants.md) ("c" nebo "n") je možné zadat při typ přístupu.

Typy přístup jsou popsané v této tabulce:

|Typ přístupu.|Popis|
|----------|----------------|
|**"r"**|Otevře pro čtení. Pokud soubor neexistuje nebo nebyl nalezen, volání k otevření souboru se nezdaří.|
|**"w"**|Otevře prázdný soubor pro zápis. Pokud daný soubor existuje, jeho obsah zničen.|
|**"a"**|Otevře se pro zápis na konci souboru (připojením); soubor nejdříve vytvoří, pokud neexistuje. Všechny zápisy operací dojít na konci souboru. Přestože lze ukazatel na soubor přesunout pomocí `fseek` nebo `rewind`, to je vždy přesunut na konec souboru před jakékoli zápisu operace provádí. |
|**"r +"**|Otevře pro čtení i zápis. Pokud soubor neexistuje nebo nebyl nalezen, volání k otevření souboru se nezdaří.|
|**"w +"**|Otevře prázdný soubor pro čtení i zápis. Pokud daný soubor existuje, jeho obsah zničen.|
|**"a +"**|Stejné jako **"a"** , ale také umožňuje čtení.|

Pokud je zadán do "r +", "w +" nebo "a +" typu, budou moct čtení i zápis (Tento soubor říká, že je otevřen pro "úpravy"). Ale při přepínání mezi čtení a zápis, musí existovat podílející `fflush`, `fsetpos`, `fseek`, nebo `rewind` operace. Aktuální pozici, je možné zadat pro `fsetpos` nebo `fseek` operace.

## <a name="see-also"></a>Viz také:

[_fdopen, _wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)<br/>
[fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md)<br/>
[freopen, _wfreopen](../c-runtime-library/reference/freopen-wfreopen.md)<br/>
[_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)<br/>
[_popen, _wpopen](../c-runtime-library/reference/popen-wpopen.md)<br/>
[Globální konstanty](../c-runtime-library/global-constants.md)
