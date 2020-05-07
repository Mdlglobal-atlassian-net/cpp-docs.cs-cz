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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 2a30302a72d228d709cd16d25d7b62d9ce64a8ba
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918912"
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

*r*<br/>
Znak, který se má zapsat

*Stream*<br/>
Ukazatel na strukturu **souborů** .

## <a name="return-value"></a>Návratová hodnota

Vrátí napsaný znak. Chcete-li určit chybu nebo stav konce souboru, **putc** a **putchar** vrátí znak **EOF**; **putwc** a **putwchar** vrátí **WEOF**. Pro všechny čtyři rutiny [použijte příkaz](ferror.md) ' nebo [feof](feof.md) ' pro kontrolu chyby nebo konce souboru. Pokud byl předán ukazatel s hodnotou null pro *datový proud*, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tyto funkce vrátí **EOF** nebo **WEOF** a nastaví **errno** na **EINVAL**.

Další informace o těchto a dalších chybových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

## <a name="remarks"></a>Poznámky

Rutina **putc** zapisuje jeden znak *c* do výstupního *proudu* na aktuální pozici. Do **putc**lze předat libovolné celé číslo, ale pouze dolních 8 bitů je zapsáno. Rutina **putchar** je shodná s `putc( c, stdout )`. Pro každou rutinu, pokud dojde k chybě čtení, je nastaven indikátor chyby pro datový proud. **putc** a **putchar** jsou podobné jako **fputc** a **_fputchar**, ale jsou implementovány jako funkce i jako makra (viz [Volba mezi funkcemi a makry](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md)). **putwc** a **putwchar** jsou verze s velkým znakem **putc** a **putchar**, v uvedeném pořadí. **putwc** a **putc** se chovají stejně, pokud je datový proud otevřen v režimu ANSI. **putc** v současné době nepodporuje výstup do datového proudu Unicode.

Verze s příponou **_nolock** jsou stejné s tím rozdílem, že nejsou chráněny před rušením jinými vlákny. Další informace najdete v tématu **_putc_nolock _putwc_nolock**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_puttc**|**putc**|**putc**|**putwc**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**putc**|\<stdio. h>|
|**putwc**|\<stdio. h> nebo \<WCHAR. h>|

Konzola není v aplikacích Univerzální platforma Windows (UWP) podporována. Standardní popisovače streamů, které jsou spojeny s konzolou, **stdin**, **stdout**a **stderr**, musí být přesměrované před tím, než je funkce modulu runtime jazyka C můžou použít v aplikacích pro UWP. Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md).

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
