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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 2c6ee763a1491a744b25cbb517886e9354ca6152
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342052"
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

*Fd*<br/>
Popisovač souboru.

*Režimu*<br/>
Akce uzamčení provést.

*nbajtů*<br/>
Počet bajtů, které chcete zamknout.

## <a name="return-value"></a>Návratová hodnota

**_locking** vrátí hodnotu 0, pokud bude úspěšná. Vrácená hodnota -1 označuje selhání, v takovém případě [je chybné číslo](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) nastaveno na jednu z následujících hodnot.

|hodnota errno|Podmínka|
|-|-|
| **ACCACCES** | Narušení uzamčení (soubor již uzamčen nebo odemčen). |
| **EBADF** | Neplatný popisovač souboru. |
| **EDEADLOCK** | Zamykání porušení. Vráceno, pokud je zadán **příznak _LK_LOCK** nebo **_LK_RLCK** a soubor nelze uzamknout po 10 pokusech. |
| **EINVAL** | Byl **_locking**dán neplatný argument . |

Pokud je chyba způsobena chybným parametrem, například neplatným popisovanem souboru, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md).

## <a name="remarks"></a>Poznámky

Funkce **_locking** uzamkne nebo odemkne *bajty nbajtů* souboru určeného *fd*. Zamykání bajtů v souboru zabraňuje přístupu k těmto bajtům jinými procesy. Všechny zamykání nebo odemykání začíná na aktuální pozici ukazatele souboru a pokračuje pro další *nbytes* bajty. Je možné zamknout bajty za koncem souboru.

*musí* být jedna z následujících konstant manifestu, které jsou definovány v Locking.h.

|hodnota *režimu*|Účinek|
|-|-|
| **_LK_LOCK** | Zamkne zadané bajty. Pokud bajty nelze uzamknout, program se okamžitě pokusí znovu po 1 sekundě. Pokud po 10 pokusech nelze uzamknout bajty, konstanta vrátí chybu. |
| **_LK_NBLCK** | Zamkne zadané bajty. Pokud bajty nelze uzamknout, konstanta vrátí chybu. |
| **_LK_NBRLCK** | Stejné jako **_LK_NBLCK**. |
| **_LK_RLCK** | Stejné jako **_LK_LOCK**. |
| **_LK_UNLCK** | Odemkne zadané bajty, které musí být dříve uzamčeny. |

Více oblastí souboru, které se nepřekrývají, lze uzamknout. Odemčená oblast musí být dříve uzamčena. **_locking** neslučuje sousední oblasti; Pokud sousedí dvě uzamčené oblasti, musí být každá oblast odemčena samostatně. Oblasti by měly být uzamčeny pouze krátce a měly by být odemčeny před zavřením souboru nebo ukončením programu.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelná hlavička|
|-------------|---------------------|---------------------|
|**_locking**|\<io.h> \<a sys/locking.h>|\<errno.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven c run-time](../../c-runtime-library/crt-library-features.md).

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

### <a name="input-crt_lockingtxt"></a>Vstup: crt_locking.txt

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
