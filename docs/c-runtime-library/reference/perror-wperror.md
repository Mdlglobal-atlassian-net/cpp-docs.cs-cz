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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 0c50e77863b4b136ac59b6f79d8e529691032609
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338537"
---
# <a name="perror-_wperror"></a>perror, _wperror

Vytisknout chybovou zprávu.

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

*Zprávu*<br/>
Zpráva řetězce k tisku.

## <a name="remarks"></a>Poznámky

Funkce **perror** vytiskne chybovou zprávu **společnosti stderr**. **_wperror** je širokoznaková verze **_perror**; argument *zprávy* **_wperror** je řetězec s širokým znakem. **_wperror** a **_perror** se chovají stejně jinak.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tperror**|**pchyba**|**pchyba**|**_wperror**|

*zpráva* je vytištěna jako první, následovaná dvojtečkou, potom chybovou zprávou systému pro poslední volání knihovny, které chybu vytvořilo, a nakonec znakem nového řádku. Pokud *je zpráva* ukazatel null nebo ukazatel na nulový řetězec, **perror** vytiskne pouze systémovou chybovou zprávu.

Číslo chyby je uloženo v proměnné [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) (definované v ERRNO. H). Systémové chybové zprávy jsou přístupné prostřednictvím proměnné [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md), což je pole zpráv seřazených podle čísla chyby. **perror** vytiskne příslušnou chybovou zprávu pomocí hodnoty **errno** jako indexu, který **má _sys_errlist**. Hodnota proměnné [_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) je definována jako maximální počet prvků v **poli _sys_errlist.**

Pro přesné výsledky volání **perror** ihned po knihovny rutina vrátí s chybou. V opačném případě mohou následná volání přepsat hodnotu **errno.**

V operačním systému Windows některé hodnoty **errno** uvedené v ERRNO. H jsou nevyužité. Tyto hodnoty jsou vyhrazeny pro použití operačním systémem UNIX. Seznam hodnot **errno** používaných operačním systémem Windows naleznete v [_doserrno, errno, _sys_errlist a _sys_nerr.](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) **perror** vytiskne prázdný řetězec pro všechny **hodnoty errno,** které tyto platformy nepoužívají.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**pchyba**|\<stdio.h> \<nebo stdlib.h>|
|**_wperror**|\<stdio.h> \<nebo wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven c run-time](../../c-runtime-library/crt-library-features.md).

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
[strerror, _strerror, \__wcserror, _wcserror](strerror-strerror-wcserror-wcserror.md)<br/>
