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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 09ad53a7f4e953da05d7eafd6662bf250731b5d6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333130"
---
# <a name="putchar-putwchar"></a>putchar, putwchar

Zapíše znak **stdout**.

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

*C*<br/>
Znak, který má být napsán.

## <a name="return-value"></a>Návratová hodnota

Vrátí napsaný znak. Chcete-li označit chybu nebo podmínku konce souboru, **putc** a **putchar** vrátí **EOF**; **putwc** a **putwchar** návrat **WEOF**. Pro všechny čtyři rutiny použijte [ferror](ferror.md) nebo [feof](feof.md) ke kontrole chyby nebo konce souboru. Pokud je předán ukazatel null pro *datový proud*, tyto funkce generovat neplatný parametr výjimku, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Je-li exekuci dovoleno pokračovat, vrátí **EOF** nebo **WEOF** a nastaví **errno** na **EINVAL**.

Další informace o těchto a dalších kódech chyb naleznete v [_doserrno, errno, _sys_errlist a _sys_nerr.](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)

## <a name="remarks"></a>Poznámky

**Putc** rutina zapíše jeden znak *c* do výstupního *datového proudu* na aktuální pozici. Libovolné celé číslo může být předáno **putc**, ale jsou zapsány pouze dolní 8 bitů. **Putchar** rutina je `putc( c, stdout )`totožný s . Pro každou rutinu, pokud dojde k chybě čtení, je nastaven indikátor chyby pro datový proud. **putc** a **putchar** jsou podobné **fputc** a **_fputchar**, ale jsou implementovány jak jako funkce, tak jako makra (viz [Volba mezi funkcemi a makra](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md)). **putwc** a **putwchar** jsou široké verze **putc** a **putchar**, resp.

Verze s **příponou _nolock** jsou identické s tím rozdílem, že nejsou chráněny před rušením jinými vlákny. Mohou být rychlejší, protože jim nevznikají režie uzamčení jiných vláken. Tyto funkce používejte pouze v kontextech bezpečných pro přístup z více vláken, jako jsou aplikace s jedním vláknem nebo kde již volající obor zpracovává izolaci vlákna.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_puttchar**|**putchar**|**putchar**|**putwchar**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**putchar**|\<stdio.h>|
|**putwchar**|\<stdio.h> \<nebo wchar.h>|

Konzola není podporována v aplikacích univerzální platformy Windows (UPW). Standardní popisovače datového proudu, které jsou přidruženy ke **konzole, stdin**, **stdout**a **stderr**, musí být přesměrovány před c run-time funkce je možné použít v aplikacích UPW. Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven c run-time](../../c-runtime-library/crt-library-features.md).

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
