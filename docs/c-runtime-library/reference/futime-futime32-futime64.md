---
title: _futime, _futime32, _futime64
ms.date: 4/2/2020
api_name:
- _futime64
- _futime32
- _futime
- _o__futime32
- _o__futime64
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
- api-ms-win-crt-time-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- futime
- _futime
- futime64
- _futime64
helpviewer_keywords:
- _futime function
- futime32 function
- futime64 function
- file modification time [C++]
- _futime64 function
- futime function
- _futime32 function
ms.assetid: b942ce8f-5cc7-4fa8-ab47-de5965eded53
ms.openlocfilehash: 1f60bb3b366c48e3d53368f81ebc2528694794f3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345507"
---
# <a name="_futime-_futime32-_futime64"></a>_futime, _futime32, _futime64

Nastaví čas změny v otevřeném souboru.

## <a name="syntax"></a>Syntaxe

```C
int _futime(
   int fd,
   struct _utimbuf *filetime
);
int _futime32(
   int fd,
   struct __utimbuf32 *filetime
);
int _futime64(
   int fd,
   struct __utimbuf64 *filetime
);
```

### <a name="parameters"></a>Parametry

*Fd*<br/>
Popisovač souboru do otevřeného souboru.

*soubor*<br/>
Ukazatel na strukturu obsahující nové datum změny.

## <a name="return-value"></a>Návratová hodnota

Vrátit 0 v případě úspěchu. Pokud dojde k chybě, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, funkce vrátí -1 a **errno** je nastavena na **EBADF**, označující neplatný popisovač souboru nebo **EINVAL**, označující neplatný parametr.

## <a name="remarks"></a>Poznámky

Rutina **_futime** nastaví datum změny a čas přístupu na otevřený soubor přidružený k *fd*. **_futime** je totožný s [_utime](utime-utime32-utime64-wutime-wutime32-wutime64.md), s tím rozdílem, že jeho argumentem je popisovač souboru otevřeného souboru, nikoli název souboru nebo cesty k souboru. Struktura **_utimbuf** obsahuje pole pro nové datum změny a přístupový čas. Obě pole musí obsahovat platné hodnoty. **_utimbuf32** a **_utimbuf64** jsou shodné s **_utimbuf** s výjimkou použití 32bitových a 64bitových časových typů. **_futime** a **_utimbuf** použít 64bitový typ času a **_futime** je v chování shodné s **_futime64**. Pokud potřebujete vynutit staré chování, definujte **_USE_32BIT_TIME_T**. To **způsobí, že _futime** být identické chování **_futime32** a **způsobí,** že struktura _utimbuf použít 32bitový časový typ, takže je ekvivalentní **__utimbuf32**.

**_futime64**, který používá **__utimbuf64** strukturu, může číst a upravovat data souborů přes 23:59:59, prosinec 31, 3000, UTC; vzhledem k tomu, že volání **_futime32** se nezdaří, pokud je datum v souboru pozdější než 23:59:59 Leden 18, 2038, UTC. Půlnoc 1.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|Volitelná hlavička|
|--------------|---------------------|---------------------|
|**_futime**|\<sys/utime.h>|\<errno.h>|
|**_futime32**|\<sys/utime.h>|\<errno.h>|
|**_futime64**|\<sys/utime.h>|\<errno.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_futime.c
// This program uses _futime to set the
// file-modification time to the current time.

#include <stdio.h>
#include <stdlib.h>
#include <fcntl.h>
#include <io.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <sys/utime.h>
#include <share.h>

int main( void )
{
   int hFile;

   // Show file time before and after.
   system( "dir crt_futime.c_input" );

   _sopen_s( &hFile, "crt_futime.c_input", _O_RDWR, _SH_DENYNO, 0 );

   if( _futime( hFile, NULL ) == -1 )
      perror( "_futime failed\n" );
   else
      printf( "File time modified\n" );

   _close (hFile);

   system( "dir crt_futime.c_input" );
}
```

### <a name="input-crt_futimec_input"></a>Vstup: crt_futime.c_input

```Input
Arbitrary file contents.
```

### <a name="sample-output"></a>Vzorový výstup

```Output
Volume in drive Z has no label.
Volume Serial Number is 5C68-57C1

Directory of Z:\crt

03/25/2004  10:40 AM                24 crt_futime.c_input
               1 File(s)             24 bytes
               0 Dir(s)  24,268,476,416 bytes free
Volume in drive Z has no label.
Volume Serial Number is 5C68-57C1

Directory of Z:\crt

03/25/2004  10:41 AM                24 crt_futime.c_input
               1 File(s)             24 bytes
               0 Dir(s)  24,268,476,416 bytes free
File time modified
```

## <a name="see-also"></a>Viz také

[Časová správa](../../c-runtime-library/time-management.md)<br/>
