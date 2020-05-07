---
title: putchar, putwchar
ms.date: 4/2/2020
api_name:
- putchar
- putwchar
- _o_putchar
- _o_putwchar
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
- putchar
- putwchar
- _puttchar
helpviewer_keywords:
- putchar function
- _puttchar function
- characters, writing
- standard output, writing to
- putwchar function
ms.assetid: 93657c7f-cca1-4032-8e3a-cd6ab6193748
ms.openlocfilehash: f8b6573b2907ec8fffa5ff4d3d76b8430748f60a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918895"
---
# <a name="putchar-putwchar"></a>putchar, putwchar

Zapíše znak do **stdout**.

## <a name="syntax"></a>Syntaxe

```C
int putchar(
   int c
);
wint_t putwchar(
   wchar_t c
);
```

### <a name="parameters"></a>Parametry

*r*<br/>
Znak, který se má zapsat

## <a name="return-value"></a>Návratová hodnota

Vrátí napsaný znak. Chcete-li určit chybu nebo stav konce souboru, **putc** a **putchar** vrátí znak **EOF**; **putwc** a **putwchar** vrátí **WEOF**. Pro všechny čtyři rutiny [použijte příkaz](ferror.md) ' nebo [feof](feof.md) ' pro kontrolu chyby nebo konce souboru. Pokud byl předán ukazatel s hodnotou null pro *datový proud*, tyto funkce generují výjimku neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí **EOF** nebo **WEOF** a nastaví **errno** na **EINVAL**.

Další informace o těchto a dalších chybových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

## <a name="remarks"></a>Poznámky

Rutina **putc** zapisuje jeden znak *c* do výstupního *proudu* na aktuální pozici. Do **putc**lze předat libovolné celé číslo, ale pouze dolních 8 bitů je zapsáno. Rutina **putchar** je shodná s `putc( c, stdout )`. Pro každou rutinu, pokud dojde k chybě čtení, je nastaven indikátor chyby pro datový proud. **putc** a **putchar** jsou podobné jako **fputc** a **_fputchar**, ale jsou implementovány jako funkce i jako makra (viz [Volba mezi funkcemi a makry](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md)). **putwc** a **putwchar** jsou verze s velkým znakem **putc** a **putchar**, v uvedeném pořadí.

Verze s příponou **_nolock** jsou stejné s tím rozdílem, že nejsou chráněny před rušením jinými vlákny. Můžou být rychlejší, protože neúčtují režii na uzamykání jiných vláken. Tyto funkce použijte pouze v kontextech bezpečných pro přístup z více vláken, jako jsou například aplikace s jedním vláknem nebo kde volající obor již zpracovává izolaci vlákna.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_puttchar**|**putchar**|**putchar**|**putwchar**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**putchar**|\<stdio. h>|
|**putwchar**|\<stdio. h> nebo \<WCHAR. h>|

Konzola není v aplikacích Univerzální platforma Windows (UWP) podporována. Standardní popisovače streamů, které jsou spojeny s konzolou, **stdin**, **stdout**a **stderr**, musí být přesměrované před tím, než je funkce modulu runtime jazyka C můžou použít v aplikacích pro UWP. Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Příklad

```C
// crt_putchar.c
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

   for( p = buffer; (ch != EOF) && (*p != '\0'); p++ )
      ch = putchar( *p );
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
