---
title: perror, _wperror
ms.date: 11/04/2016
apiname:
- _wperror
- perror
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _wperror
- _tperror
- perror
helpviewer_keywords:
- _tperror function
- tperror function
- wperror function
- error messages, printing
- printing error messages
- _wperror function
- perror function
ms.assetid: 34fce792-16fd-4673-9849-cd88b54b6cd5
ms.openlocfilehash: c9026a96ecc74640eb2bcd7004d5d1e0fc287e38
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156097"
---
# <a name="perror-wperror"></a>perror, _wperror

Tisk chybové zprávy.

## <a name="syntax"></a>Syntaxe

```C
void perror(
   const char *message
);
void _wperror(
   const wchar_t *message
);
```

### <a name="parameters"></a>Parametry

*message*<br/>
Řetězcovou zprávu pro tisk.

## <a name="remarks"></a>Poznámky

**Perror** funkce zobrazí chybovou zprávu do **stderr**. **_wperror –** je verze širokého znaku **_perror**; *zpráva* argument **_wperror –** je širokoznaký řetězec. **_wperror –** a **_perror** se jinak chovají stejně.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tperror**|**perror**|**perror**|**_wperror**|

*zpráva* vytiskne se nejprve, následovaný dvojtečkou a pak podle chybovou zprávu systému pro poslední volání knihovny, který vytvořil chybu a nakonec znakem nového řádku. Pokud *zpráva* je ukazatel s hodnotou null nebo ukazatel na řetězec null **perror** vytiskne pouze chybovou zprávu systému.

Číslo chyby je uložen v proměnné [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) (definované v ERRNO. H). Chybové zprávy systému jsou přístupné prostřednictvím proměnné [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md), což je pole zpráv seřazené podle čísla chyby. **perror** vytiskne příslušnou chybovou zprávu pomocí **errno** hodnotu jako index tak, aby **_sys_errlist**. Hodnota proměnné [_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) je definována jako maximální počet prvků v **_sys_errlist** pole.

Pro přesné výsledky zavolejte **perror** ihned poté, co knihovní rutina vrátí chybu. V opačném případě můžete přepsat následných voláních **errno** hodnotu.

V Windows operační systém, některé **errno** hodnoty uvedené v ERRNO. H se nepoužívají. Tyto hodnoty jsou vyhrazené pro použití v operačním systému UNIX. V tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) seznam **errno** hodnot použitých v operačním systému Windows. **perror** vytiskne prázdný řetězec pro všechny **errno** hodnotu nepoužívá tyto platformy.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**perror**|\<stdio.h > nebo \<stdlib.h >|
|**_wperror**|\<stdio.h > nebo \<wchar.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Příklad

```C
// crt_perror.c
// compile with: /W3
/* This program attempts to open a file named
* NOSUCHF.ILE. Because this file probably doesn't exist,
* an error message is displayed. The same message is
* created using perror, strerror, and _strerror.
*/

#include <fcntl.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <io.h>
#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <share.h>

int main( void )
{
   int  fh;

   if( _sopen_s( &fh, "NOSUCHF.ILE", _O_RDONLY, _SH_DENYNO, 0 ) != 0 )
   {
      /* Three ways to create error message: */
      perror( "perror says open failed" );
      printf( "strerror says open failed: %s\n",
         strerror( errno ) ); // C4996
      printf( _strerror( "_strerror says open failed" ) ); // C4996
      // Note: strerror and _strerror are deprecated; consider
      // using strerror_s and _strerror_s instead.
   }
   else
   {
      printf( "open succeeded on input file\n" );
      _close( fh );
   }
}
```

```Output
perror says open failed: No such file or directory
strerror says open failed: No such file or directory
_strerror says open failed: No such file or directory
```

## <a name="see-also"></a>Viz také:

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[clearerr](clearerr.md)<br/>
[ferror](ferror.md)<br/>
[strerror, _strerror, _wcserror, \__wcserror](strerror-strerror-wcserror-wcserror.md)<br/>
