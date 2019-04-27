---
title: _chsize
ms.date: 03/29/2018
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
helpviewer_keywords:
- size
- _chsize function
- size, changing file
- files [C++], changing size
- chsize function
ms.assetid: b3e881c5-7b27-4837-a3d4-c51591ab10ff
ms.openlocfilehash: 5c60f3aa08a405eb9a83dc6ba8636cd316a32925
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62340323"
---
# <a name="chsize"></a>_chsize

Změní velikost souboru. Bezpečnější verze je k dispozici. Zobrazit [_chsize_s –](chsize-s.md).

## <a name="syntax"></a>Syntaxe

```C
int _chsize(
   int fd,
   long size
);
```

### <a name="parameters"></a>Parametry

*fd*<br/>
Popisovač souboru odkazující na otevřený soubor.

*Velikost*<br/>
Novou velikost souboru v bajtech.

## <a name="return-value"></a>Návratová hodnota

**_chsize –** vrací hodnotu 0, pokud je úspěšně změněna velikost souboru. Návratová hodnota-1 označuje chybu: **errno** je nastavena na **EACCES** Pokud zadaný soubor je jen pro čtení nebo zadaný soubor je uzamčen před přístupem, do **EBADF** Pokud Popisovač je neplatný, **ENOSPC** Pokud již není místo na zařízení, nebo **EINVAL** Pokud *velikost* je menší než nula.

Zobrazit [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o těchto a dalších návratových kódů.

## <a name="remarks"></a>Poznámky

**_Chsize –** rozšiřuje funkce nebo zkrátí soubor přidružený k *fd* délce určené *velikost*. Soubor musí být otevřen v režimu, který umožňuje zápis. Znaky s hodnotou Null ('\0') se připojují, pokud je soubor rozšířeno. Soubor je zkrácen, dojde ke ztrátě všech dat od konce zkrácený soubor původní délku souboru.

Tato funkce ověřuje své parametry. Pokud *velikost* je menší než nula nebo *fd* je popisovače souborů, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_chsize**|\<io.h>|\<errno.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také:

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[_close](close.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
