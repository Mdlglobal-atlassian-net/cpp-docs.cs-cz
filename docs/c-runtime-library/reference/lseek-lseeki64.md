---
title: _lseek, _lseeki64
ms.date: 11/04/2016
api_name:
- _lseeki64
- _lseek
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
- _lseeki64
- _lseek
- lseeki64
helpviewer_keywords:
- lseek function
- _lseek function
- _lseeki64 function
- lseeki64 function
- file pointers [C++], moving
- seek file pointers
ms.assetid: aba8a768-d40e-48c3-b38e-473dbd782f93
ms.openlocfilehash: 67bcce2a9936cd09973e8ddf1828704944866439
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952977"
---
# <a name="_lseek-_lseeki64"></a>_lseek, _lseeki64

Přesune ukazatel na soubor do zadaného umístění.

## <a name="syntax"></a>Syntaxe

```C
long _lseek(
   int fd,
   long offset,
   int origin
);
__int64 _lseeki64(
   int fd,
   __int64 offset,
   int origin
);
```

### <a name="parameters"></a>Parametry

*fd*<br/>
Popisovač souboru odkazující na otevřený soubor.

*polohy*<br/>
Počet bajtů od *počátku*

*zdroji*<br/>
Počáteční pozice.

## <a name="return-value"></a>Návratová hodnota

**_lseek** vrátí posunutí nové pozice od začátku souboru v bajtech. **_lseeki64** vrací posun v 64 celé číslo. Funkce vrátí-1L k indikaci chyby. Pokud byl předán neplatný parametr, jako je například Chybný popisovač souboru, nebo hodnota pro *počátek* je neplatná nebo je pozice určená *posunem* před začátkem souboru, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [parametru. Ověřování](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tyto funkce nastaví **errno** na **EBADF** a vrátí-1l. U zařízení, která neumožňují hledání (například terminálů a tiskáren), není návratová hodnota definována.

Další informace o těchto a dalších chybových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **_lseek** přesune ukazatel na soubor přidružený k *FD* do nového umístění, které má *posunutí* bajtů od *počátku*. Následující operace se souborem probíhá v novém umístění. Argument *Origin* musí být jedna z následujících konstant, které jsou definovány v stdio. h.

|hodnota *počátku*||
|-|-|
| **SEEK_SET** | Začátek souboru. |
| **SEEK_CUR** | Aktuální pozice ukazatele na soubor. |
| **SEEK_END** | Konec souboru |

Můžete použít **_lseek** k přemístění ukazatele na libovolné místo v souboru nebo za konec souboru.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_lseek**|\<io.h>|
|**_lseeki64**|\<io.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Příklad

```C
// crt_lseek.c
/* This program first opens a file named lseek.txt.
* It then uses _lseek to find the beginning of the file,
* to find the current position in the file, and to find
* the end of the file.
*/

#include <io.h>
#include <fcntl.h>
#include <stdlib.h>
#include <stdio.h>
#include <share.h>

int main( void )
{
   int fh;
   long pos;               /* Position of file pointer */
   char buffer[10];

   _sopen_s( &fh, "crt_lseek.c_input", _O_RDONLY, _SH_DENYNO, 0 );

   /* Seek the beginning of the file: */
   pos = _lseek( fh, 0L, SEEK_SET );
   if( pos == -1L )
      perror( "_lseek to beginning failed" );
   else
      printf( "Position for beginning of file seek = %ld\n", pos );

   /* Move file pointer a little */
    _read( fh, buffer, 10 );

   /* Find current position: */
   pos = _lseek( fh, 0L, SEEK_CUR );
   if( pos == -1L )
      perror( "_lseek to current position failed" );
   else
      printf( "Position for current position seek = %ld\n", pos );

   /* Set the end of the file: */
   pos = _lseek( fh, 0L, SEEK_END );
   if( pos == -1L )
      perror( "_lseek to end failed" );
   else
      printf( "Position for end of file seek = %ld\n", pos );

   _close( fh );
}
```

### <a name="input-crt_lseekc_input"></a>Vstup: crt_lseek. c_input

```Input
Line one.
Line two.
Line three.
Line four.
Line five.
```

### <a name="output"></a>Výstup

```Output
Position for beginning of file seek = 0
Position for current position seek = 10
Position for end of file seek = 57
```

## <a name="see-also"></a>Viz také:

[I/O nízké úrovně](../../c-runtime-library/low-level-i-o.md)<br/>
[fseek, _fseeki64](fseek-fseeki64.md)<br/>
[_tell, _telli64](tell-telli64.md)<br/>
