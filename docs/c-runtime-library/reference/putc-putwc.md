---
title: putc, putwc
ms.date: 11/04/2016
api_name:
- putwc
- putc
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
ms.openlocfilehash: 2fcd0ea2263cd858b0b4ce855f96c0389956ccc3
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70950099"
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

*c*<br/>
Znak, který se má zapsat

*stream*<br/>
Ukazatel na strukturu **souborů** .

## <a name="return-value"></a>Návratová hodnota

Vrátí napsaný znak. Chcete-li určit chybu nebo stav konce souboru, **putc** a **putchar** vrátí znak **EOF**; **putwc** a **putwchar** vrátí **WEOF**. Pro všechny čtyři rutiny [použijte příkaz](ferror.md) ' nebo [feof](feof.md) ' pro kontrolu chyby nebo konce souboru. Pokud byl předán ukazatel s hodnotou null pro *datový proud*, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tyto funkce vrátí **EOF** nebo **WEOF** a nastaví **errno** na **EINVAL**.

Další informace o těchto a dalších chybových kódech naleznete v tématech [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

## <a name="remarks"></a>Poznámky

Rutina **putc** zapisuje jeden znak *c* do výstupního *proudu* na aktuální pozici. Do **putc**lze předat libovolné celé číslo, ale pouze dolních 8 bitů je zapsáno. Rutina **putchar** je shodná s `putc( c, stdout )`. Pro každou rutinu, pokud dojde k chybě čtení, je nastaven indikátor chyby pro datový proud. **putc** a **putchar** jsou podobné jako **fputc** a **_fputchar**, ale jsou implementovány jako funkce i jako makra (viz [Volba mezi funkcemi a makry](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md)). **putwc** a **putwchar** jsou verze s velkým znakem **putc** a **putchar**, v uvedeném pořadí. **putwc** a **putc** se chovají stejně, pokud je datový proud otevřen v režimu ANSI. **putc** v současné době nepodporuje výstup do datového proudu Unicode.

Verze s příponou **_nolock** jsou stejné s tím rozdílem, že nejsou chráněny před rušením jinými vlákny. Další informace najdete v tématu **_putc_nolock, _putwc_nolock**.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_puttc**|**putc**|**putc**|**putwc**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**putc**|\<stdio.h>|
|**putwc**|\<stdio. h > nebo \<WCHAR. h >|

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

## <a name="see-also"></a>Viz také:

[Vstup/výstup datového proudu](../../c-runtime-library/stream-i-o.md)<br/>
[fputc, fputwc](fputc-fputwc.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
