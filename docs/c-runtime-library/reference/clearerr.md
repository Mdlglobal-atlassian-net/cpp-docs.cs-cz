---
title: clearerr
ms.date: 4/2/2020
api_name:
- clearerr
- _o_clearerr
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
- clearerr
helpviewer_keywords:
- error indicator for streams
- resetting stream error indicator
- clearerr function
ms.assetid: a9711cd4-3335-43d4-a018-87bbac5b3bac
ms.openlocfilehash: 174c94136cdc8b603416ff1dd239703489925bae
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350022"
---
# <a name="clearerr"></a>clearerr

Obnoví indikátor chyby pro datový proud. K dispozici je bezpečnější verze této funkce. viz [clearerr_s](clearerr-s.md).

## <a name="syntax"></a>Syntaxe

```C
void clearerr(
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*Proudu*<br/>
Ukazatel na **strukturu FILE.**

## <a name="remarks"></a>Poznámky

Funkce **jasnější resetuje** indikátor chyby a indikátor konce souboru pro *stream*. Indikátory chyb nejsou automaticky vymazány. po nastavení indikátoru chyby pro zadaný datový proud operace na tomto datovém proudu nadále vracet chybovou hodnotu, dokud **clearr**, [fseek](fseek-fseeki64.md), **fsetpos**nebo [převinout zpět](rewind.md) je volána.

Pokud je *datový proud* **NULL**, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v části [Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, tato funkce nastaví **errno** na **EINVAL** a vrátí. Další informace o **chybových** kódech a chybových kódech naleznete [v tématu errno Constants](../../c-runtime-library/errno-constants.md).

K dispozici je bezpečnější verze této funkce. viz [clearerr_s](clearerr-s.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**clearerr**|\<stdio.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_clearerr.c
// This program creates an error
// on the standard input stream, then clears
// it so that future reads won't fail.

#include <stdio.h>

int main( void )
{
   int c;
   // Create an error by writing to standard input.
   putc( 'c', stdin );
   if( ferror( stdin ) )
   {
      perror( "Write error" );
      clearerr( stdin );
   }

   // See if read causes an error.
   printf( "Will input cause an error? " );
   c = getc( stdin );
   if( ferror( stdin ) )
   {
      perror( "Read error" );
      clearerr( stdin );
   }
   else
      printf( "No read error\n" );
}
```

### <a name="input"></a>Vstup

```Input
n
```

### <a name="output"></a>Výstup

```Output
Write error: No error
Will input cause an error? n
No read error
```

## <a name="see-also"></a>Viz také

[Zpracování chyb](../../c-runtime-library/error-handling-crt.md)<br/>
[I/O proudu](../../c-runtime-library/stream-i-o.md)<br/>
[_eof](eof.md)<br/>
[feof](feof.md)<br/>
[ferror](ferror.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>
