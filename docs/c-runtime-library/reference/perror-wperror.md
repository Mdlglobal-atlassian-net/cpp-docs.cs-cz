---
title: perror, _wperror – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _tperror function
- tperror function
- wperror function
- error messages, printing
- printing error messages
- _wperror function
- perror function
ms.assetid: 34fce792-16fd-4673-9849-cd88b54b6cd5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 455bf63cdac425217c40068853b302edefb94f16
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="perror-wperror"></a>perror, _wperror

Tisk chybovou zprávu.

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

*zpráva* řetězce zprávy k vytištění.

## <a name="remarks"></a>Poznámky

**Perror** funkce zobrazí chybovou zprávu do **stderr**. **_wperror –** je verze široká charakterová **_perror**; *zpráva* argument **_wperror –** je široká charakterová řetězec. **_wperror –** a **_perror** chovat jinak shodně.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tperror –**|**perror**|**perror**|**_wperror**|

*zpráva* se vytiskne, a potom dvojtečkou a pak zprávy o chybách systému pro posledního volání knihovny, které vytváří v chybě a v neposlední řadě znak nového řádku. Pokud *zpráva* ukazatele null nebo je ukazatel na hodnotu null. řetězec **perror** vytiskne pouze zprávy o systémové chybě.

Číslo chyby je uložené v proměnné [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) (definovanou v kód chyby. H). Systém chybové zprávy, které jsou přístupné prostřednictvím proměnnou [_sys_errlist –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md), což je pole zpráv, které jsou seřazené podle číslo chyby. **perror** vytiskne odpovídající chybovou zprávu pomocí **errno** hodnotu jako index pro **_sys_errlist –**. Hodnota proměnné [_sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) je definován jako maximální počet elementů v **_sys_errlist –** pole.

Pro přesné výsledky volání **perror** ihned po rutiny knihovny vrátí chybu. Jinak můžete přepsat následující volání **errno** hodnotu.

V systému Windows operační systém, některé **errno** hodnoty uvedené v kód chyby. H se nepoužívá. Tyto hodnoty jsou vyhrazené pro použití v operačním systému UNIX. V tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) seznam **errno** hodnoty používané v operačním systému Windows. **perror** vytiskne prázdný řetězec pro žádné **errno** hodnotu, která nepoužívá tyto platformy.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**perror**|\<stdio.h > nebo \<stdlib.h >|
|**_wperror**|\<stdio.h > nebo \<wchar.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).

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

## <a name="see-also"></a>Viz také

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[clearerr](clearerr.md)<br/>
[ferror](ferror.md)<br/>
[strerror – _strerror –, _wcserror –, \__wcserror –](strerror-strerror-wcserror-wcserror.md)<br/>
