---
title: _eof – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _eof
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
- _eof
dev_langs:
- C++
helpviewer_keywords:
- eof function
- end of file, testing for
- _eof function
- files [C++], end of
- testing, for end-of-file
- end of file
ms.assetid: 265703f4-d07e-4005-abf3-b1d0cdd9e0b0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: da7ccad98491762d30db2741f8c3d9fe0d784dc6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32395121"
---
# <a name="eof"></a>_eof

Testy pro konec souboru (EOF).

## <a name="syntax"></a>Syntaxe

```C
int _eof(
   int fd
);
```

### <a name="parameters"></a>Parametry

*FD*<br/>
Popisovače souborů na otevření souboru.

## <a name="return-value"></a>Návratová hodnota

**_eof –** vrátí hodnotu 1, pokud aktuální pozice konce souboru, nebo 0, pokud není. Vrácená hodnota -1 označuje chybu; v takovém případě je volána obslužná rutina neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění **errno** je nastaven na **ebadf –**, což naznačuje popisovač souboru je neplatný.

## <a name="remarks"></a>Poznámky

**_Eof –** funkce určuje, zda konec souboru přidružené *fd* byl dosažen.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|
|--------------|---------------------|---------------------|
|**_eof**|\<IO.h >|\<errno.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_eof.c
// This program reads data from a file
// ten bytes at a time until the end of the
// file is reached or an error is encountered.
//
#include <io.h>
#include <fcntl.h>
#include <stdio.h>
#include <stdlib.h>
#include <share.h>

int main( void )
{
   int  fh, count, total = 0;
   char buf[10];
   if( _sopen_s( &fh, "crt_eof.txt", _O_RDONLY, _SH_DENYNO, 0 ) )
   {
        perror( "Open failed");
        exit( 1 );
   }
   // Cycle until end of file reached:
   while( !_eof( fh ) )
   {
      // Attempt to read in 10 bytes:
      if( (count = _read( fh, buf, 10 )) == -1 )
      {
         perror( "Read error" );
         break;
      }
      // Total actual bytes read
      total += count;
   }
   printf( "Number of bytes read = %d\n", total );
   _close( fh );
}
```

### <a name="input-crteoftxt"></a>Vstup: crt_eof.txt

```Input
This file contains some text.
```

### <a name="output"></a>Výstup

```Output
Number of bytes read = 29
```

## <a name="see-also"></a>Viz také

[Zpracování chyb](../../c-runtime-library/error-handling-crt.md)<br/>
[I/O nízké úrovně](../../c-runtime-library/low-level-i-o.md)<br/>
[clearerr](clearerr.md)<br/>
[feof](feof.md)<br/>
[ferror](ferror.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>
