---
title: _locking
ms.date: 4/2/2020
api_name:
- _locking
- _o__locking
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _locking
helpviewer_keywords:
- locking function
- bytes [C++], locking file
- files [C++], locking bytes
- files [C++], locking
- _locking function
ms.assetid: 099aaac1-d4ca-4827-aed6-24dff9844150
ms.openlocfilehash: c1c211ffaa63a0e4711374b01b0530ed8db20dfb
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82911540"
---
# <a name="_locking"></a>_locking

Zamkne nebo odemkne bajty souboru.

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

*Mode*<br/>
Akce zamykání, která se má provést

*nbytes*<br/>
Počet bajtů, které mají být zamčeny.

## <a name="return-value"></a>Návratová hodnota

**_locking** vrátí 0, pokud bylo úspěšné. Návratová hodnota-1 označuje chybu, v takovém případě je [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) nastavena na jednu z následujících hodnot.

|hodnota errno|Podmínka|
|-|-|
| **EACCES** | Narušení uzamčení (soubor je už uzamčený nebo odemčený). |
| **EBADF** | Neplatný popisovač souboru |
| **EDEADLOCK** | Narušení zámku. Vrátí se, když je zadaný příznak **_LK_LOCK** nebo **_LK_RLCK** a soubor se nedá uzamknout po 10 pokusech. |
| **EINVAL** | **_Locking**byl zadán neplatný argument. |

Pokud je selhání způsobeno chybným parametrem, jako je neplatný popisovač souboru, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md).

## <a name="remarks"></a>Poznámky

Funkce **_locking** zamkne nebo odemkne *nBytes* bajtů souboru zadaného parametrem *FD*. Uzamykání bajtů v souboru brání v přístupu k těmto bajtům jiným procesům. Všechna uzamknutí nebo odemknutí začíná na aktuální pozici ukazatele souboru a pokračuje pro další *nBytes* bajty. Je možné zamknout bajty za konec souboru.

*režim* musí být jedna z následujících konstant manifestu, které jsou definovány v uzamykání. h.

|hodnota *režimu*|Účinek|
|-|-|
| **_LK_LOCK** | Zamkne zadané bajty. Pokud bajty nelze zamknout, program se hned po 1 sekundách pokusí znovu. Pokud po 10 pokusech nelze bajty uzamknout, vrátí konstanta chybu. |
| **_LK_NBLCK** | Zamkne zadané bajty. Pokud bajty nelze uzamknout, vrátí konstanta chybu. |
| **_LK_NBRLCK** | Stejné jako **_LK_NBLCK**. |
| **_LK_RLCK** | Stejné jako **_LK_LOCK**. |
| **_LK_UNLCK** | Odemkne zadané bajty, které se musí dřív uzamknout. |

Více oblastí souboru, které se nepřekrývají, lze uzamknout. Odemknutá oblast musí být dříve uzamčena. **_locking** neslučuje sousední oblasti; Pokud se dvě uzamčené oblasti sousedí, je nutné každou oblast odemknout samostatně. Oblasti by se měly uzamknout jenom krátce a před zavřením souboru nebo ukončením programu by se měly odemknout.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_locking**|\<IO. h> a \<sys/uzamykání. h>|\<errno. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md).

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

### <a name="input-crt_lockingtxt"></a>Vstup: crt_locking. txt

```Input
The first thirty bytes of this file will be locked.
```

## <a name="sample-output"></a>Vzorový výstup

```Output
No one can change these bytes while I'm reading them
30 bytes read: The first thirty bytes of this
Now I'm done. Do what you will with them
```

## <a name="see-also"></a>Viz také

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
