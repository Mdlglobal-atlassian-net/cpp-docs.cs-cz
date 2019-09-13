---
title: _chsize
ms.date: 03/29/2018
api_name:
- _chsize
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
- _chsize
helpviewer_keywords:
- size
- _chsize function
- size, changing file
- files [C++], changing size
- chsize function
ms.assetid: b3e881c5-7b27-4837-a3d4-c51591ab10ff
ms.openlocfilehash: 7fe07b2261396be491b833ff52186024edd0b919
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942967"
---
# <a name="_chsize"></a>_chsize

Změní velikost souboru. Je k dispozici bezpečnější verze; viz [_chsize_s](chsize-s.md).

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

*hodnota*<br/>
Nová délka souboru v bajtech

## <a name="return-value"></a>Návratová hodnota

**_chsize** vrací hodnotu 0, pokud je velikost souboru úspěšně změněna. Návratová hodnota-1 označuje chybu: **errno** je nastavená na **EACCES** , pokud je zadaný soubor jen pro čtení, nebo je zadaný soubor uzamčený proti přístupu, aby **EBADF** v případě, že je popisovač neplatný, **ENOSPC** , pokud na zařízení není žádné místo, nebo **EINVAL** , pokud je *Velikost* menší než nula.

Další informace o těchto a dalších návratových kódech naleznete v tématech [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

## <a name="remarks"></a>Poznámky

Funkce **_chsize** rozšiřuje nebo zkrátí soubor přidružený k *FD* na délku určenou *velikostí*. Soubor musí být otevřen v režimu, který povoluje zápis. Pokud je soubor rozšířený, připojí se znaky null (' \ 0 '). Pokud je soubor zkrácený, ztratí se všechna data z konce zkráceného souboru do původní délky souboru.

Tato funkce ověří své parametry. Pokud je *Velikost* menší než nula nebo *FD* je chybný popisovač souboru, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_chsize**|\<io.h>|\<errno.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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
