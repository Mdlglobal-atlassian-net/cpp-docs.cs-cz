---
title: _flushall – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- flushall function
- flushing streams
- streams, flushing
- _flushall function
ms.assetid: 2cd73562-6d00-4ca2-b13c-80d0ae7870b5
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 936a0c4c18b36c490f0edfeefa651e21c017e1fc
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="flushall"></a>_flushall

Počet vyprázdnění všechny datové proudy; Vymaže všechny vyrovnávací paměti.

## <a name="syntax"></a>Syntaxe

```C
int _flushall( void );
```

## <a name="return-value"></a>Návratová hodnota

**_flushall –** vrátí počet otevřete datových proudů (vstup a výstup). Neexistuje žádný návratový chyby.

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení **_flushall –** funkce zapisuje do příslušné soubory obsahu vyrovnávacích pamětí všechny přidružené otevřít výstupní datové proudy. Všechny vyrovnávací paměti přidružené otevřete vstupní datové proudy vyjmuty z jejich aktuálního obsahu. (Tyto vyrovnávací paměti se obvykle spravuje podle operačního systému, která určuje optimální čas automaticky zapsat data na disk: Pokud vyrovnávací paměť je plná, když datový proud je uzavřen nebo když program ukončí normálně bez zavření datové proudy.)

Pokud pro čtení a následně **_flushall –**, nová data načítají z vstupní soubory do vyrovnávací paměti. Všechny datové proudy zůstanou otevřené po zavolání **_flushall –**.

Funkce běhové knihovny k potvrzení na disku umožňuje Ujistěte se, že je důležitá data zapsána přímo na disku, nikoli do vyrovnávací paměti operačního systému. Bez přepisování existujícího programu, můžete povolit tuto funkci pomocí propojení objektu soubory programu s Commode.obj. Ve výsledném spustitelného souboru, volá, aby se **_flushall –** zapisovat obsah všech vyrovnávací paměti na disk. Pouze **_flushall –** a [fflush –](fflush.md) jsou ovlivněné Commode.obj.

Informace o řízení funkce potvrzení na disku naleznete v tématu [vstupně-výstupní datový proud](../../c-runtime-library/stream-i-o.md), [fopen –](fopen-wfopen.md), a [_fdopen –](fdopen-wfdopen.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_flushall**|\<stdio.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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

[Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[_commit](commit.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[fflush](fflush.md)<br/>
[setvbuf](setvbuf.md)<br/>
