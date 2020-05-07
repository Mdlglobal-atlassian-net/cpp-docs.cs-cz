---
title: perror, _wperror
ms.date: 4/2/2020
api_name:
- _wperror
- perror
- _o__wperror
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 64b9abe6313cc13e1e20f8f66ba486cdeb3e4892
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919325"
---
# <a name="perror-_wperror"></a>perror, _wperror

Vytiskne chybovou zprávu.

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

*Zpráva*<br/>
Zpráva řetězce k vytištění

## <a name="remarks"></a>Poznámky

Funkce **pError** vytiskne chybovou zprávu do **stderr**. **_wperror** je verze **_perror**s velkým znakem; Argument *zprávy* , který je **_wperror** , je řetězec s velkým znakem. **_wperror** a **_perror** se chovají identicky jinak.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tperror**|**pError**|**pError**|**_wperror**|

*zpráva* je vytištěna jako první, za kterou následuje dvojtečka, potom chybovou zprávou systému pro poslední volání knihovny, které vytvořilo chybu, a nakonec pomocí znaku nového řádku. Pokud je *zpráva* ukazatel s hodnotou null nebo ukazatelem na řetězec s hodnotou null, **pError** vytiskne pouze systémovou chybovou zprávu.

Číslo chyby je uloženo v proměnné [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) (definováno v errno. H). K systémovým chybovým zprávám se dostanete prostřednictvím proměnné [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md), což je pole zpráv seřazené podle čísla chyby. **pError** vytiskne příslušnou chybovou zprávu pomocí hodnoty **errno** jako indexu pro **_sys_errlist**. Hodnota proměnné [_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) je definována jako maximální počet prvků v poli **_sys_errlist** .

Pro přesné výsledky volejte **pError** ihned poté, co rutina knihovny vrátí chybu. V opačném případě mohou další volání přepsat hodnotu **errno** .

V operačním systému Windows některé hodnoty **errno** jsou uvedené v errno. H se nepoužívá. Tyto hodnoty jsou vyhrazené pro použití v operačním systému UNIX. Seznam hodnot **errno** používaných operačním systémem Windows najdete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) . **pError** vytiskne prázdný řetězec pro všechny **errno** hodnoty, které tyto platformy nepoužívají.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**pError**|\<stdio. h> nebo \<Stdlib. h>|
|**_wperror**|\<stdio. h> nebo \<WCHAR. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md).

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
[strerror –, _strerror _wcserror, \__wcserror](strerror-strerror-wcserror-wcserror.md)<br/>
