---
title: putc, putwc | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- putwc
- putc
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _puttc
- putwc
- putc
dev_langs:
- C++
helpviewer_keywords:
- streams, writing characters to
- characters, writing
- putwc function
- putc function
- _puttc function
- puttc function
ms.assetid: a37b2e82-9d88-4565-8190-ff8d04c0ddb9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: af5c6987f88238398a00e9da7f0d769f246ffc54
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211066"
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
Znak k zapsání.

*Stream*<br/>
Ukazatel na **souboru** struktury.

## <a name="return-value"></a>Návratová hodnota

Vrátí zapsaný znak. K označení chyby nebo stavu ukončení souboru **putc** a **putchar** vrátit ** EOF`; **putwc` a **putwchar** vrátit **WEOF**. Pro všechny čtyři rutiny použijte [ferror](ferror.md) nebo [feof](feof.md) zkontrolovat chyby nebo konce souboru. Je-li předán ukazatel s hodnotou null *stream*, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí tyto funkce **EOF** nebo **WEOF** a nastavte **errno** k **EINVAL**.

Zobrazit [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o těchto a dalších chybových kódech.

## <a name="remarks"></a>Poznámky

**Putc** rutina zapíše jeden znak *c* do výstupu *stream* na aktuální pozici. Libovolné celé číslo může být předán **putc**, ale jsou zapsány pouze nižší 8bity. **Putchar** rutiny je stejný jako `putc( c, stdout )`. Pro každou rutinu je pokud dojde k chybě čtení, nastaven indikátor chyby pro datový proud. **putc** a **putchar** jsou podobné **fputc** a **_fputchar**v uvedeném pořadí, ale jsou implementovány jako funkce i makra (viz [ Volba mezi funkcemi a makry](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md)). **putwc** a **putwchar** jsou širokoznaké verze **putc** a **putchar**v uvedeném pořadí. **putwc** a **putc** chovají stejně jako v případě, že datový proud je otevřen v režimu ANSI. **putc** aktuálně nepodporuje výstup do datového proudu UNICODE.

Verze s **_nolock** přípona jsou stejné s tím rozdílem, že nejsou chráněny před rušením jinými vlákny. Další informace najdete v tématu **_putc_nolock _putwc_nolock**.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_puttc –**|**putc**|**putc**|**putwc**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**putc**|\<stdio.h>|
|**putwc**|\<stdio.h > nebo \<wchar.h >|

Konzole není podporována v aplikacích pro univerzální platformu Windows (UPW). Standardní datový proud popisovačů, které jsou spojeny s konzolou, **stdin**, **stdout**, a **stderr**, musí být přesměrován před funkcí jazyka C za běhu můžete použít v aplikacích pro UWP . Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md).

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

[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[fputc, fputwc](fputc-fputwc.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
