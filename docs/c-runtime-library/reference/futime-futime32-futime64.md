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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 615e436abf9d763e73d26db61d9063d5e586232b
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82909916"
---
# <a name="_futime-_futime32-_futime64"></a>_futime, _futime32, _futime64

Nastaví čas změny otevřeného souboru.

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
Popisovač souboru do otevřeného souboru

*FILETIME –*<br/>
Ukazatel na strukturu obsahující nové datum úpravy.

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí hodnotu 0. Pokud dojde k chybě, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, funkce vrátí hodnotu-1 a **errno** je nastavena na **EBADF**, což značí neplatný popisovač souboru nebo **EINVAL**, což značí neplatný parametr.

## <a name="remarks"></a>Poznámky

Rutina **_futime** nastaví datum úpravy a dobu přístupu k otevřenému souboru přidruženému ke *FD*. **_futime** je stejný jako [_utime](utime-utime32-utime64-wutime-wutime32-wutime64.md), s tím rozdílem, že jeho argument je popisovačem souboru otevřeného souboru, nikoli název souboru nebo cesta k souboru. Struktura **_utimbuf** obsahuje pole pro nové datum a čas přístupu pro úpravu. Obě pole musí obsahovat platné hodnoty. **_utimbuf32** a **_utimbuf64** jsou stejné jako **_utimbuf** s výjimkou použití typů 32 a 64 bitového času, v uvedeném pořadí. **_futime** a **_utimbuf** používají typ času 64 a **_futime** se shodují s chováním **_futime64**. Pokud potřebujete vynutit staré chování, definujte **_USE_32BIT_TIME_T**. To způsobí, že **_futime** být identické v chování pro **_futime32** a způsobí, že struktura **_utimbuf** používá typ času 32-bit, takže to odpovídá **__utimbuf32**.

**_futime64**, která používá strukturu **__utimbuf64** , může číst a upravovat data souborů až 23:59:59, 31. prosince 3000, UTC; v případě, že se volání **_futime32** nezdařilo, je-li datum souboru pozdější než 23:59:59 18. ledna 2038, UTC. Půlnoc, 1. ledna 1970, je dolní mez rozsahu kalendářních dat pro tyto funkce.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|--------------|---------------------|---------------------|
|**_futime**|\<sys/UTIME. h>|\<errno. h>|
|**_futime32**|\<sys/UTIME. h>|\<errno. h>|
|**_futime64**|\<sys/UTIME. h>|\<errno. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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

### <a name="input-crt_futimec_input"></a>Vstup: crt_futime. c_input

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
