---
title: _flushall
ms.date: 11/04/2016
api_name:
- _flushall
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _flushall
helpviewer_keywords:
- flushall function
- flushing streams
- streams, flushing
- _flushall function
ms.assetid: 2cd73562-6d00-4ca2-b13c-80d0ae7870b5
ms.openlocfilehash: dce7412ccc19d4870494851d366c059ff01de16a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957142"
---
# <a name="_flushall"></a>_flushall

Vyprázdní všechny streamy; Vymaže všechny vyrovnávací paměti.

## <a name="syntax"></a>Syntaxe

```C
int _flushall( void );
```

## <a name="return-value"></a>Návratová hodnota

**_flushall** vrátí počet otevřených datových proudů (vstup a výstup). Nevrátila se žádná chybová zpráva.

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení funkce **_flushall** zapisuje do příslušných souborů obsah všech vyrovnávacích pamětí přidružených k otevřeným výstupním proudům. Všechny vyrovnávací paměti přidružené k otevřeným vstupním proudům jsou vymazány z aktuálního obsahu. (Tyto vyrovnávací paměti jsou obvykle udržovány operačním systémem, který určuje optimální čas pro automatické zápis dat na disk: Pokud je vyrovnávací paměť plná, když je datový proud uzavřený nebo když se program ukončí normálně bez zavírání datových proudů.)

Pokud čtení následuje za voláním **_flushall**, jsou nová data čtena ze vstupních souborů do vyrovnávací paměti. Všechny datové proudy zůstanou otevřené po volání **_flushall**.

Funkce Commit-to-disk v běhové knihovně vám umožní zajistit, aby byla kritická data zapisována přímo na disk, nikoli do vyrovnávací paměti operačního systému. Bez přepisu stávajícího programu můžete tuto funkci povolit propojením souborů objektů programu pomocí Commode. obj. Ve výsledném spustitelném souboru volání **_flushall** zapisují obsah všech vyrovnávacích pamětí na disk. Commode. obj má vliv pouze na **_flushall** a [fflush](fflush.md) .

Informace o řízení funkce potvrzení na disk najdete v tématu [streamování I/O](../../c-runtime-library/stream-i-o.md), [fopen](fopen-wfopen.md)a [_fdopen](fdopen-wfdopen.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_flushall**|\<stdio.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_flushall.c
// This program uses _flushall
// to flush all open buffers.

#include <stdio.h>

int main( void )
{
   int numflushed;

   numflushed = _flushall();
   printf( "There were %d streams flushed\n", numflushed );
}
```

```Output
There were 3 streams flushed
```

## <a name="see-also"></a>Viz také:

[Vstup/výstup datového proudu](../../c-runtime-library/stream-i-o.md)<br/>
[_commit](commit.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[fflush](fflush.md)<br/>
[setvbuf](setvbuf.md)<br/>
