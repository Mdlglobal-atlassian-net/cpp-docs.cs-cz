---
title: fgetc, fgetwc
ms.date: 11/04/2016
api_name:
- fgetwc
- fgetc
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
- _fgettc
- fgetwc
- fgetc
helpviewer_keywords:
- fgettc function
- characters, reading
- _fgettc function
- fgetc function
- streams, reading characters from
- reading characters from streams
- fgetwc function
ms.assetid: 13348b7b-dc86-421c-9d6c-611ca79c8338
ms.openlocfilehash: 92f44c65802f3baed37078574577bf108bbcd09a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940896"
---
# <a name="fgetc-fgetwc"></a>fgetc, fgetwc

Načtení znaku z datového proudu.

## <a name="syntax"></a>Syntaxe

```C
int fgetc(
   FILE *stream
);
wint_t fgetwc(
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*stream*<br/>
Ukazatel na strukturu **souborů** .

## <a name="return-value"></a>Návratová hodnota

**fgetc** vrátí znak načtený jako **int** nebo vrátí **EOF** , aby označoval chybu nebo konec souboru. **fgetwc** vrátí jako [wint_t](../../c-runtime-library/standard-types.md), což je celý znak, který odpovídá znaku Read nebo vrátí **WEOF** k označení chyby nebo konce souboru. U obou funkcí použijte **feof** nebo **trajekt** k rozlišení mezi chybou a stavem konce souboru. Pokud dojde k chybě čtení, je nastaven indikátor chyby pro datový proud. Pokud má *datový proud* **hodnotu null**, **fgetc** a **fgetwc** vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tyto funkce nastaví **errno** na **EINVAL** a vrátí **EOF**.

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí čte jeden znak z aktuální pozice souboru přidruženého ke *streamu*. Funkce poté zvýší přidružený ukazatel na soubor (je-li definován), aby ukazoval na další znak. Pokud je datový proud na konci souboru, je nastaven indikátor konce souboru pro datový proud.

**fgetc** je ekvivalentem **getc –** , ale je implementována pouze jako funkce, nikoli jako funkce a makro.

**fgetwc** je **fgetc**verze s velkým znakem; čte **c** jako vícebajtový znak nebo jako velký znak v závislosti na tom, zda je *datový proud* otevřen v textovém režimu nebo v binárním režimu.

Verze s příponou **_nolock** jsou stejné s tím rozdílem, že nejsou chráněny před rušením jinými vlákny.

Další informace o zpracování velkých a vícebajtových znaků v textovém a binárním režimu najdete v tématu [vstupně-výstupní operace streamu Unicode v textovém a binárním režimu](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fgettc**|**fgetc**|**fgetc**|**fgetwc**|

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fgetc**|\<stdio.h>|
|**fgetwc**|\<stdio. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_fgetc.c
// This program uses getc to read the first
// 80 input characters (or until the end of input)
// and place them into a string named buffer.

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   FILE *stream;
   char buffer[81];
   int  i, ch;

   // Open file to read line from:
   fopen_s( &stream, "crt_fgetc.txt", "r" );
   if( stream == NULL )
      exit( 0 );

   // Read in first 80 characters and place them in "buffer":
   ch = fgetc( stream );
   for( i=0; (i < 80 ) && ( feof( stream ) == 0 ); i++ )
   {
      buffer[i] = (char)ch;
      ch = fgetc( stream );
   }

   // Add null to end string
   buffer[i] = '\0';
   printf( "%s\n", buffer );
   fclose( stream );
}
```

## <a name="input-crt_fgetctxt"></a>Vstup: crt_fgetc. txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Výstup

```Output
Line one.
Line two.
```

## <a name="see-also"></a>Viz také:

[Vstup/výstup datového proudu](../../c-runtime-library/stream-i-o.md)<br/>
[fputc, fputwc](fputc-fputwc.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
