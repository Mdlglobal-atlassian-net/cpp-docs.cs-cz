---
title: putc, putwc
ms.date: 4/2/2020
api_name:
- putwc
- putc
- _o_putc
- _o_putwc
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
- _puttc
- putwc
- putc
helpviewer_keywords:
- streams, writing characters to
- characters, writing
- putwc function
- putc function
- _puttc function
- puttc function
ms.assetid: a37b2e82-9d88-4565-8190-ff8d04c0ddb9
ms.openlocfilehash: 8809595c90c48976d9f28ffa659714f5b9d919c9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338462"
---
# <a name="putc-putwc"></a>putc, putwc

Zapíše znak do datového proudu.

## <a name="syntax"></a>Syntaxe

```C
int putc(
   int c,
   FILE *stream
);
wint_t putwc(
   wchar_t c,
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*C*<br/>
Znak, který má být napsán.

*Proudu*<br/>
Ukazatel na **strukturu FILE.**

## <a name="return-value"></a>Návratová hodnota

Vrátí napsaný znak. Chcete-li označit chybu nebo podmínku konce souboru, **putc** a **putchar** vrátí **EOF**; **putwc** a **putwchar** návrat **WEOF**. Pro všechny čtyři rutiny použijte [ferror](ferror.md) nebo [feof](feof.md) ke kontrole chyby nebo konce souboru. Pokud je předán ukazatel null pro *datový proud*, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, tyto funkce vrátí **EOF** nebo **WEOF** a nastaví **errno** na **EINVAL**.

Další informace o těchto a dalších kódech chyb naleznete v [_doserrno, errno, _sys_errlist a _sys_nerr.](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)

## <a name="remarks"></a>Poznámky

**Putc** rutina zapíše jeden znak *c* do výstupního *datového proudu* na aktuální pozici. Libovolné celé číslo může být předáno **putc**, ale jsou zapsány pouze dolní 8 bitů. **Putchar** rutina je `putc( c, stdout )`totožný s . Pro každou rutinu, pokud dojde k chybě čtení, je nastaven indikátor chyby pro datový proud. **putc** a **putchar** jsou podobné **fputc** a **_fputchar**, ale jsou implementovány jak jako funkce, tak jako makra (viz [Volba mezi funkcemi a makra](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md)). **putwc** a **putwchar** jsou široké verze **putc** a **putchar**, resp. **putwc** a **putc** se chovají stejně, pokud je datový proud otevřen v režimu ANSI. **putc** v současné době nepodporuje výstup do datového proudu UNICODE.

Verze s **příponou _nolock** jsou identické s tím rozdílem, že nejsou chráněny před rušením jinými vlákny. Další informace naleznete **v tématu _putc_nolock, _putwc_nolock**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_puttc**|**putc**|**putc**|**putwc**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**putc**|\<stdio.h>|
|**putwc**|\<stdio.h> \<nebo wchar.h>|

Konzola není podporována v aplikacích univerzální platformy Windows (UPW). Standardní popisovače datového proudu, které jsou přidruženy ke **konzole, stdin**, **stdout**a **stderr**, musí být přesměrovány před c run-time funkce je možné použít v aplikacích UPW. Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven c run-time](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Příklad

```C
// crt_putc.c
/* This program uses putc to write buffer
* to a stream. If an error occurs, the program
* stops before writing the entire buffer.
*/

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char *p, buffer[] = "This is the line of output\n";
   int  ch;

   ch = 0;
   /* Make standard out the stream and write to it. */
   stream = stdout;
   for( p = buffer; (ch != EOF) && (*p != '\0'); p++ )
      ch = putc( *p, stream );
}
```

### <a name="output"></a>Výstup

```Output
This is the line of output
```

## <a name="see-also"></a>Viz také

[I/O proudu](../../c-runtime-library/stream-i-o.md)<br/>
[fputc, fputwc](fputc-fputwc.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
