---
title: _flushall
ms.date: 11/04/2016
apiname:
- _flushall
apilocation:
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
apitype: DLLExport
f1_keywords:
- _flushall
helpviewer_keywords:
- flushall function
- flushing streams
- streams, flushing
- _flushall function
ms.assetid: 2cd73562-6d00-4ca2-b13c-80d0ae7870b5
ms.openlocfilehash: de8caf30568816f41441f5d9487293c346d2bff1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62333531"
---
# <a name="flushall"></a>_flushall

Vyprázdní všechny datové proudy; Vymaže všechny vyrovnávací paměti.

## <a name="syntax"></a>Syntaxe

```C
int _flushall( void );
```

## <a name="return-value"></a>Návratová hodnota

**_flushall –** vrátí počet otevřených datových proudů (vstup a výstup). Není vrácena žádná chyba.

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení **_flushall –** funkce zapíše do příslušné soubory obsah všech vyrovnávacích pamětí přidružený otevřený výstupní datové proudy. Zrušte zaškrtnutí všech vyrovnávacích pamětí přidružený otevřený vstupní datové proudy jejich aktuální obsah. (Tyto vyrovnávací paměti jsou obvykle udržuje operačního systému, který určuje optimální čas automaticky zapisovat data na disk: Pokud vyrovnávací paměť je plná, když datový proud je uzavřen nebo když program skončí obvykle bez zavření datové proudy.)

Pokud se čtení následuje volání **_flushall –**, je nová data číst ze vstupních souborů do vyrovnávací paměti. Všechny datové proudy zůstaly otevřené po volání **_flushall –**.

Funkce potvrzení na disku knihovny run-time umožňuje zajistit, že důležitá data se zapisují přímo na disk, nikoli do vyrovnávací paměti operačního systému. Bez přepsání existující program, můžete povolit tuto funkci tak propojování souborů objektů programu s Commode.obj. Výsledný spustitelný soubor volá do **_flushall –** zapisovat obsah všech vyrovnávací paměti na disk. Pouze **_flushall –** a [fflush –](fflush.md) jsou ovlivněny Commode.obj.

Informace o řízení funkce potvrzení na disku naleznete v tématu [vstupně-výstupní operace Stream](../../c-runtime-library/stream-i-o.md), [fopen](fopen-wfopen.md), a [_fdopen –](fdopen-wfdopen.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_flushall**|\<stdio.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[_commit](commit.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[fflush](fflush.md)<br/>
[setvbuf](setvbuf.md)<br/>
