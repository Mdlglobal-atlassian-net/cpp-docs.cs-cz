---
title: fgetc, fgetwc
ms.date: 4/2/2020
api_name:
- fgetwc
- fgetc
- _o_fgetc
- _o_fgetwc
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
ms.openlocfilehash: c1589c64127b47f4dd2a1147f2b4d549601db4fc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347014"
---
# <a name="fgetc-fgetwc"></a>fgetc, fgetwc

Čtení znaku z datového proudu.

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

*Proudu*<br/>
Ukazatel na **strukturu FILE.**

## <a name="return-value"></a>Návratová hodnota

**fgetc** vrátí znak přečtený jako **int** nebo vrátí **EOF** označující chybu nebo konec souboru. **fgetwc** vrátí jako [wint_t](../../c-runtime-library/standard-types.md)široký znak, který odpovídá znaku číst nebo vrátí **WEOF** k označení chyby nebo konce souboru. Pro obě funkce použijte **feof** nebo **ferror** k rozlišení mezi chybou a podmínkou konce souboru. Pokud dojde k chybě čtení, je nastaven indikátor chyby pro datový proud. Pokud je *datový proud* **NULL**, **fgetc** a **fgetwc** vyvolávají neplatnou obslužnou rutinu parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, tyto funkce nastavit **errno** **eINVAL** a vrátit **EOF**.

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí přečte jeden znak z aktuální pozice souboru přidruženého k *datovému proudu*. Funkce pak navýhne přidružený ukazatel souboru (pokud je definován) tak, aby ukazoval na další znak. Pokud je datový proud na konci souboru, je nastaven indikátor konce souboru pro datový proud.

**fgetc** je ekvivalentní **getc**, ale je implementován pouze jako funkce, nikoli jako funkce a makro.

**fgetwc** je širokoznaková verze **fgetc**; přečte **c** jako vícebajtový znak nebo široký znak podle toho, zda je *datový proud* otevřen v textovém nebo binárním režimu.

Verze s **příponou _nolock** jsou identické s tím rozdílem, že nejsou chráněny před rušením jinými vlákny.

Další informace o zpracování širokých znaků a vícebajtových znaků v textovém a binárním režimu naleznete [v tématu Unicode Stream I/O v režimech Text a Binární režimy](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fgettc**|**fgetc**|**fgetc**|**fgetwc**|

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fgetc**|\<stdio.h>|
|**fgetwc**|\<stdio.h> \<nebo wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

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

## <a name="input-crt_fgetctxt"></a>Vstup: crt_fgetc.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Výstup

```Output
Line one.
Line two.
```

## <a name="see-also"></a>Viz také

[I/O proudu](../../c-runtime-library/stream-i-o.md)<br/>
[fputc, fputwc](fputc-fputwc.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
