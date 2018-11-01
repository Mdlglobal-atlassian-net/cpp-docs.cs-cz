---
title: ungetc, ungetwc
ms.date: 11/04/2016
apiname:
- ungetwc
- ungetc
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
- _ungettc
- ungetwc
- ungetc
helpviewer_keywords:
- ungetwc function
- ungettc function
- characters, pushing back onto stream
- _ungettc function
- ungetc function
ms.assetid: e0754f3a-b4c6-408f-90c7-e6387b830d84
ms.openlocfilehash: 95d2160ba4d008ab67f443d4e9dda7180d62b590
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50633581"
---
# <a name="ungetc-ungetwc"></a>ungetc, ungetwc

Posune znak zpět do datového proudu.

## <a name="syntax"></a>Syntaxe

```C
int ungetc(
   int c,
   FILE *stream
);
wint_t ungetwc(
   wint_t c,
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*c*<br/>
Znak k posunutí.

*Stream*<br/>
Ukazatel na **souboru** struktury.

## <a name="return-value"></a>Návratová hodnota

Pokud úspěšná, každá z těchto funkcí vrátí argument znaku *c*. Pokud *c* nemůže být posunut zpět nebo pokud byl načten žádný znak, vstupního datového proudu je beze změny a **ungetc –** vrátí ** EOF`; **ungetwc` vrátí **WEOF**. Pokud *stream* je **NULL**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, **EOF** nebo **WEOF** je vrácena a **errno** je nastavena na **EINVAL**.

Informace o těchto a dalších chybových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**Ungetc –** funkce posune znak *c* zpět do *stream* a vymaže indikátor konce souboru. Datový proud musí být otevřen pro čtení. Následná operace čtení na *stream* začíná *c*. Pokus posunout **EOF** na datový proud pomocí **ungetc –** se ignoruje.

Znaky umístěny v datovém proudu podle **ungetc –** mohou být vymazány, pokud **fflush –**, [fseek](fseek-fseeki64.md), **fsetpos**, nebo [rewind](rewind.md) je volána před čtením znaku z datového proudu. Indikátor pozice v souboru bude mít hodnotu, kterou měl před zpětným posunutím znaků. Externí úložiště odpovídající datovému proudu je beze změny. Při úspěšném **ungetc –** volání proti textovému proudu Indikátor pozice v souboru není zadána, dokud všechny znaky posunuté zpět přečteny nebo zahozeny. Na každém úspěšném **ungetc –** volání proti binárnímu datovému proudu Indikátor pozice v souboru snížen; Pokud byla jeho hodnota 0 před voláním, hodnota je po volání nedefinovaná.

Výsledky nepředvídatelné Pokud **ungetc –** je volána dvakrát bez operace umístění v souboru mezi dvěma voláními nebo čtení. Po volání **fscanf –**, volání **ungetc –** může selhat, pokud jiná operace čtení (například **getc**) byla provedena. Důvodem je, že **fscanf –** sama volá **ungetc –**.

**ungetwc –** je verze širokého znaku **ungetc –**. Ale na každém úspěšném **ungetwc –** volání proti textovému nebo binárnímu proudu, hodnota indikátoru pozice v souboru není zadán dokud všechny znaky posunuté zpět přečteny nebo zahozeny.

Tyto funkce jsou bezpečné na vlákno a zamykají citlivá data při spuštění. Nezamykací verzi naleznete v tématu [_ungetc_nolock – _ungetwc_nolock –](ungetc-nolock-ungetwc-nolock.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ungettc –**|**ungetc –**|**ungetc –**|**ungetwc –**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**ungetc –**|\<stdio.h>|
|**ungetwc –**|\<stdio.h > nebo \<wchar.h >|

Konzole není podporována v aplikacích pro univerzální platformu Windows (UPW). Standardní datový proud popisovačů, které jsou spojeny s konzolou, **stdin**, **stdout**, a **stderr**, musí být přesměrován před funkcí jazyka C za běhu můžete použít v aplikacích pro UWP . Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_ungetc.c
// This program first converts a character
// representation of an unsigned integer to an integer. If
// the program encounters a character that is not a digit,
// the program uses ungetc to replace it in the  stream.
//

#include <stdio.h>
#include <ctype.h>

int main( void )
{
   int ch;
   int result = 0;

   // Read in and convert number:
   while( ((ch = getchar()) != EOF) && isdigit( ch ) )
      result = result * 10 + ch - '0';    // Use digit.
   if( ch != EOF )
      ungetc( ch, stdin );                // Put nondigit back.
   printf( "Number = %d\nNext character in stream = '%c'",
            result, getchar() );
}
```

```Output

      521aNumber = 521
Next character in stream = 'a'
```

## <a name="see-also"></a>Viz také:

[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
[putc, putwc](putc-putwc.md)<br/>
