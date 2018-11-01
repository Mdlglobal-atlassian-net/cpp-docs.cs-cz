---
title: _locking
ms.date: 11/04/2016
apiname:
- _locking
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
- _locking
helpviewer_keywords:
- locking function
- bytes [C++], locking file
- files [C++], locking bytes
- files [C++], locking
- _locking function
ms.assetid: 099aaac1-d4ca-4827-aed6-24dff9844150
ms.openlocfilehash: 1309d99d8e7040626384e38324c1e910e4731295
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523801"
---
# <a name="locking"></a>_locking

Uzamyká nebo odemyká bajtů do souboru.

## <a name="syntax"></a>Syntaxe

```C
int _locking(
   int fd,
   int mode,
   long nbytes
);
```

### <a name="parameters"></a>Parametry

*FD*<br/>
Popisovač souboru.

*Režim*<br/>
Uzamčení akce k provedení.

*nbytes*<br/>
Počet bajtů, které mají zamknout.

## <a name="return-value"></a>Návratová hodnota

**_locking –** v případě úspěchu vrátí hodnotu 0. Návratová hodnota-1 označuje chybu, v takovém případě [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) nastavena na jednu z následujících hodnot.

|Hodnota errno|Podmínka|
|-|-|
**EACCES**|Uzamčení porušení (soubor již zamčený nebo odemčený).
**EBADF**|Popisovač souboru je neplatná.
**EDEADLOCK**|Narušení uzamčení. Vrátí, když **_LK_LOCK** nebo **_LK_RLCK** příznak zadán a nelze jej uzamknout soubor po 10 pokusech.
**EINVAL**|Byl zadán neplatný argument **_locking –**.

Pokud selže z důvodu chybný parametr, jako je například neplatného popisovače souboru, vyvolán obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md).

## <a name="remarks"></a>Poznámky

**_Locking –** funkce uzamyká nebo odemyká *nbytes* bajtů do souboru určeného parametrem *fd*. Zamykací bajty v souboru brání v přístupu k těmto bajtů s jinými procesy. Všechny blokování a odblokování začne na aktuální pozici ukazatele souboru a pokračuje ještě *nbytes* bajtů. Je možné zamykací bajty za koncem souboru.

*režim* musí být jedna z následujících konstant manifestu, které jsou definovány v Locking.h.

|*režim* hodnota|Efekt|
|-|-|
**_LK_LOCK**|Zamkne zadaný počet bajtů. Pokud nelze uzamknout počet bajtů, program okamžitě pokusí znovu za 1 sekundu. Pokud po 10 pokusech, nelze uzamknout počet bajtů, konstanta vrátí chybu.
**_LK_NBLCK**|Zamkne zadaný počet bajtů. Pokud nelze uzamknout počet bajtů, konstanta vrátí chybu.
**_LK_NBRLCK**|Stejné jako **_LK_NBLCK**.
**_LK_RLCK**|Stejné jako **_LK_LOCK**.
**_LK_UNLCK**|Odemkne zadané bajtů, které musí mít dříve uzamčen.

Jde zamknout souboru více oblastí, které se nepřekrývají. Oblast odemykají musí být dříve uzamčeny. **_locking –** nemá sloučení sousední oblasti; pokud jsou dvě oblasti uzamčené vedle sebe, každou oblast, musí být odemčený samostatně. Oblastí by měl uzamknou jen krátce a by měl být odemknout před zavřením souboru nebo standardním ukončením programu.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_locking**|\<IO.h > a \<sys/locking.h >|\<errno.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Příklad

```C
// crt_locking.c
/* This program opens a file with sharing. It locks
* some bytes before reading them, then unlocks them. Note that the
* program works correctly only if the file exists.
*/

#include <sys/types.h>
#include <sys/stat.h>
#include <sys/locking.h>
#include <share.h>
#include <fcntl.h>
#include <stdio.h>
#include <stdlib.h>
#include <io.h>

int main( void )
{
   int  fh, numread;
   char buffer[40];

   /* Quit if can't open file or system doesn't
    * support sharing.
    */
   errno_t err = _sopen_s( &fh, "crt_locking.txt", _O_RDONLY, _SH_DENYNO,
                          _S_IREAD | _S_IWRITE );
   printf( "%d %d\n", err, fh );
   if( err != 0 )
      exit( 1 );

   /* Lock some bytes and read them. Then unlock. */
   if( _locking( fh, LK_NBLCK, 30L ) != -1 )
   {
      long lseek_ret;
      printf( "No one can change these bytes while I'm reading them\n" );
      numread = _read( fh, buffer, 30 );
      buffer[30] = '\0';
      printf( "%d bytes read: %.30s\n", numread, buffer );
      lseek_ret = _lseek( fh, 0L, SEEK_SET );
      _locking( fh, LK_UNLCK, 30L );
      printf( "Now I'm done. Do what you will with them\n" );
   }
   else
      perror( "Locking failed\n" );

   _close( fh );
}
```

### <a name="input-crtlockingtxt"></a>Vstup: crt_locking.txt

```Input
The first thirty bytes of this file will be locked.
```

## <a name="sample-output"></a>Vzorový výstup

```Output
No one can change these bytes while I'm reading them
30 bytes read: The first thirty bytes of this
Now I'm done. Do what you will with them
```

## <a name="see-also"></a>Viz také:

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
