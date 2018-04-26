---
title: _chsize – | Microsoft Docs
ms.custom: ''
ms.date: 03/29/2018
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _chsize
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
- _chsize
dev_langs:
- C++
helpviewer_keywords:
- size
- _chsize function
- size, changing file
- files [C++], changing size
- chsize function
ms.assetid: b3e881c5-7b27-4837-a3d4-c51591ab10ff
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 818051fba093c83d695afcad103865b4114673d0
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="chsize"></a>_chsize

Změní velikost souboru. Bezpečnější verze je k dispozici. v tématu [_chsize_s –](chsize-s.md).

## <a name="syntax"></a>Syntaxe

```C
int _chsize(
   int fd,
   long size
);
```

### <a name="parameters"></a>Parametry

*FD*<br/>
Odkaz na soubor otevřený popisovač souboru.

*Velikost*<br/>
Nové délka souboru v bajtech.

## <a name="return-value"></a>Návratová hodnota

**_chsize –** vrátí hodnotu 0, pokud velikost souboru je úspěšně změnit. Vrácená hodnota -1 označuje chybu: **errno** je nastaven na **eacces –** Pokud zadaný soubor je jen pro čtení nebo je zadaný soubor uzamčen před přístupem, na **ebadf –** Pokud Popisovač je neplatná, **enospc –** Pokud žádné místa v zařízení, nebo **einval –** Pokud *velikost* je menší než nula.

V tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o těchto a dalších návratové kódy.

## <a name="remarks"></a>Poznámky

**_Chsize –** funkce rozšiřuje nebo zkrátí soubor přidružený k *fd* na délku určeného *velikost*. Soubor musí být otevřený v režimu, která umožňuje zápis. Znaky Null (\0) jsou připojeny, pokud je soubor rozšířeno. Soubor se zkrátí, dojde ke ztrátě všech dat od konce souboru zkrácená na původní délku souboru.

Tato funkce ověří jeho parametry. Pokud *velikost* je menší než nula nebo *fd* popisovač chybného souboru, je vyvolána obslužná rutina neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|
|-------------|---------------------|---------------------|
|**_chsize**|\<IO.h >|\<errno.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_chsize.c
// This program uses _filelength to report the size
// of a file before and after modifying it with _chsize.

#include <io.h>
#include <fcntl.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <stdio.h>
#include <share.h>

int main( void )
{
   int fh, result;
   unsigned int nbytes = BUFSIZ;

   // Open a file
   if( _sopen_s( &fh, "data", _O_RDWR | _O_CREAT, _SH_DENYNO,
                 _S_IREAD | _S_IWRITE ) == 0 )
   {
      printf( "File length before: %ld\n", _filelength( fh ) );
      if( ( result = _chsize( fh, 329678 ) ) == 0 )
         printf( "Size successfully changed\n" );
      else
         printf( "Problem in changing the size\n" );
      printf( "File length after:  %ld\n", _filelength( fh ) );
      _close( fh );
   }
}
```

```Output
File length before: 0
Size successfully changed
File length after:  329678
```

## <a name="see-also"></a>Viz také

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[_close](close.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
