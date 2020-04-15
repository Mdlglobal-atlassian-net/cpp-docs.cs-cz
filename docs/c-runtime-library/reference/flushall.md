---
title: _flushall
ms.date: 4/2/2020
api_name:
- _flushall
- _o__flushall
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 93181c0fe941a1c5e259e706771495666329bcb3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346622"
---
# <a name="_flushall"></a>_flushall

Vypláchne všechny proudy; vymaže všechny vyrovnávací paměti.

## <a name="syntax"></a>Syntaxe

```C
int _flushall( void );
```

## <a name="return-value"></a>Návratová hodnota

**_flushall** vrátí počet otevřených datových proudů (vstup a výstup). Neexistuje žádná chyba vrátit.

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení **_flushall** funkce zapisuje do příslušných souborů obsah všech vyrovnávacích pamětí přidružených k otevřeným výstupním datovým proudům. Všechny vyrovnávací paměti přidružené k otevřeným vstupním datovým proudům jsou vymazány z jejich aktuálního obsahu. (Tyto vyrovnávací paměti jsou obvykle udržovány operačním systémem, který určuje optimální čas pro automatické zápis dat na disk: když je vyrovnávací paměť plná, když je datový proud uzavřen nebo když program ukončí normálně bez zavření datových proudů.)

Pokud čtení následuje volání **_flushall**, nová data jsou čtena ze vstupních souborů do vyrovnávacích pamětí. Všechny datové proudy zůstanou otevřené i po volání **_flushall**.

Funkce potvrzení na disk v knihovně za běhu umožňuje zajistit, aby byla důležitá data zapsána přímo na disk, nikoli do vyrovnávacích pamětí operačního systému. Bez přepisování existujícího programu můžete tuto funkci povolit propojením souborů objektů programu s souborem Commode.obj. Ve výsledném spustitelném souboru volání **_flushall** zapsat obsah všech vyrovnávacích pamětí na disk. Commode.obj se týká pouze **_flushall** a [fflush.](fflush.md)

Informace o řízení funkce potvrzení na disk naleznete v [tématu Stream I/O](../../c-runtime-library/stream-i-o.md), [fopen](fopen-wfopen.md)a [_fdopen](fdopen-wfdopen.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_flushall**|\<stdio.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také

[I/O proudu](../../c-runtime-library/stream-i-o.md)<br/>
[_commit](commit.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[fflush](fflush.md)<br/>
[setvbuf](setvbuf.md)<br/>
