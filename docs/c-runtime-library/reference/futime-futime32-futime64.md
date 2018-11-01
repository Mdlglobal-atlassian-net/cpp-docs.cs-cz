---
title: _futime, _futime32, _futime64
ms.date: 11/04/2016
apiname:
- _futime64
- _futime32
- _futime
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
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: f21e394acdcc7fbf8a91c5450a4c04daa050db21
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50652501"
---
# <a name="futime-futime32-futime64"></a>_futime, _futime32, _futime64

Nastaví čas změny na otevřený soubor.

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

*FD*<br/>
Popisovač souboru pro otevření souboru.

*FileTime –*<br/>
Ukazatel na strukturu obsahující nové datum změny.

## <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, vrátí 0. Pokud dojde k chybě, vyvolán obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, vrátí funkce hodnotu -1 a **errno** je nastavena na **EBADF**, určující popisovač souboru je neplatná nebo **EINVAL**, určující neplatný parametr.

## <a name="remarks"></a>Poznámky

**_Futime** rutina nastaví datum změny a čas přístupu na otevřený soubor přidružený k *fd*. **_futime** je stejný jako [_utime](utime-utime32-utime64-wutime-wutime32-wutime64.md), s tím rozdílem, že její argument je popisovač souboru otevřený soubor, nikoli název souboru nebo cesta k souboru. **_Utimbuf –** struktura obsahuje pole pro nové změny datum a čas přístupu. Obě pole musí obsahovat platné hodnoty. **_utimbuf32** a **_utimbuf64** jsou stejné jako **_utimbuf –** s výjimkou použití typů 32bitové a 64bitové čas v uvedeném pořadí. **_futime** a **_utimbuf –** použít 64-bit čas a **_futime** je stejný jako v chování **_futime64**. Pokud potřebujete vynutit staré chování, definovat **_USE_32BIT_TIME_T**. To způsobí, že to **_futime** mít identickou chování **_futime32** a způsobí, že **_utimbuf –** strukturu chcete použít typ času 32-bit, díky tomu je ekvivalentní k **__utimbuf32**.

**_futime64**, který používá **__utimbuf64 –** struktury, může číst a upravovat data souboru do 23:59:59, 31 prosince 3000 UTC, zatímco volání **_futime32** selže, pokud je datum v souboru nejpozději do 23:59:59 18. ledna 2038 UTC. Půlnoc 1. ledna 1970 je dolní mez rozsahu kalendářních dat pro tyto funkce.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|--------------|---------------------|---------------------|
|**_futime**|\<SYS/utime.h >|\<errno.h>|
|**_futime32**|\<SYS/utime.h >|\<errno.h>|
|**_futime64**|\<SYS/utime.h >|\<errno.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

### <a name="input-crtfutimecinput"></a>Vstup: crt_futime.c_input

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

## <a name="see-also"></a>Viz také:

[Správa času](../../c-runtime-library/time-management.md)<br/>
