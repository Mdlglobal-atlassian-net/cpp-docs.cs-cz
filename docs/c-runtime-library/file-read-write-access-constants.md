---
title: Konstanty přístupu pro čtení a zápis souborů
ms.date: 11/04/2016
helpviewer_keywords:
- read/write access constants
- write access constants
- access constants for file read/write
- constants [C++], file attributes
- file read/write access constants
ms.assetid: 56cd1d22-39a5-4fcf-bea2-7046d249e8ee
ms.openlocfilehash: 96d146b2e2f0ed82cbdc52b11d92c049da50e2cb
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438395"
---
# <a name="file-readwrite-access-constants"></a>Konstanty přístupu pro čtení a zápis do souboru

## <a name="syntax"></a>Syntaxe

```
#include <stdio.h>
```

## <a name="remarks"></a>Poznámky

Tyto konstanty určují typ přístupu ("a", "r" nebo "w") požadovaný pro soubor. Pro typ přístupu lze zadat jak [režim překladu](../c-runtime-library/file-translation-constants.md) ("b", "t") a [režim potvrzení na disk](../c-runtime-library/commit-to-disk-constants.md) ("c" nebo "n").

Typy přístupu jsou popsány v této tabulce:

|Typ přístupu|Popis|
|----------|----------------|
|**í**|Otevře se pro čtení. Pokud soubor neexistuje nebo nebyl nalezen, volání pro otevření souboru se nezdařilo.|
|**w**|Otevře prázdný soubor pro zápis. Pokud daný soubor existuje, jeho obsah je zničen.|
|**určitého**|Otevře se pro zápis na konci souboru (přidávání); Vytvoří soubor jako první, pokud neexistuje. Všechny operace zápisu se vyskytují na konci souboru. I když lze ukazatel na soubor přesunout pomocí `fseek` nebo `rewind`, je vždy přesunut zpět na konec souboru před provedením jakékoli operace zápisu. |
|**"r +"**|Otevře se pro čtení i zápis. Pokud soubor neexistuje nebo nebyl nalezen, volání pro otevření souboru se nezdařilo.|
|**"w +"**|Otevře prázdný soubor pro čtení i zápis. Pokud daný soubor existuje, jeho obsah je zničen.|
|**"a +"**|Totéž jako **"a"** , ale také umožňuje čtení.|

Je-li zadán typ "r +", "w +" nebo "a +", jsou povoleny čtení i zápis (soubor je označován jako otevřený pro "aktualizaci"). Když ale přepínáte mezi čtením a zápisem, musí se jednat o `fflush`, `fsetpos`, `fseek`nebo `rewind` operace. Aktuální pozici lze zadat pro operaci `fsetpos` nebo `fseek`.

## <a name="see-also"></a>Viz také

[_fdopen, _wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)<br/>
[fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md)<br/>
[freopen, _wfreopen](../c-runtime-library/reference/freopen-wfreopen.md)<br/>
[_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)<br/>
[_popen, _wpopen](../c-runtime-library/reference/popen-wpopen.md)<br/>
[Globální konstanty](../c-runtime-library/global-constants.md)
