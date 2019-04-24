---
title: fgetc, fgetwc
ms.date: 11/04/2016
apiname:
- fgetwc
- fgetc
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
ms.openlocfilehash: a853a46fc43106c9ea57be84b37fb46a18041ba8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62334005"
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

*stream*<br/>
Ukazatel na **souboru** struktury.

## <a name="return-value"></a>Návratová hodnota

**fgetc –** vrátí znak čtený jako **int** nebo vrátí **EOF** k označení chyby nebo konce souboru. **fgetwc –** vrátí, jako [wint_t](../../c-runtime-library/standard-types.md), široký znak, který odpovídá znaku číst nebo vrátí **WEOF** k označení chyby nebo konce souboru. Pro obě funkce použijte **feof** nebo **ferror** k rozlišení mezi chybou a podmínkou end souboru. Pokud dojde k chybě čtení, je nastaven indikátor chyby pro datový proud. Pokud *stream* je **NULL**, **fgetc –** a **fgetwc –** vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v [parametr Ověření](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, tyto funkce nastaví **errno** k **EINVAL** a vrátit **EOF**.

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí načte jeden znak z aktuální pozice soubor přidružený k *stream*. Funkce potom zvýší přidružený ukazatel na soubor (je-li definován) tak, aby odkazoval na další znak. Pokud je datový proud na konci souboru, je nastaven indikátor konce souboru pro datový proud.

**fgetc –** je ekvivalentní **getc**, ale je implementována pouze jako funkce, nikoli jako funkce a makro.

**fgetwc –** je verze širokého znaku **fgetc –**; načte **c** jako vícebajtový znak nebo široký znak podle toho, zda *stream* je otevřen v textovém nebo binárním režimu.

Verze s **_nolock** přípona jsou stejné s tím rozdílem, že nejsou chráněny před rušením jinými vlákny.

Další informace o zpracování širokých znaků a vícebajtových znaků v textovém a binárním režimu najdete v tématu [vstupně-výstupní Stream kódování Unicode v textovém a binárním režimu](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fgettc**|**fgetc –**|**fgetc –**|**fgetwc**|

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fgetc –**|\<stdio.h>|
|**fgetwc**|\<stdio.h > nebo \<wchar.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="input-crtfgetctxt"></a>Vstup: crt_fgetc.txt

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

[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[fputc, fputwc](fputc-fputwc.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
