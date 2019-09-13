---
title: _fgetchar, _fgetwchar
ms.date: 11/04/2016
api_name:
- _fgetchar
- _fgetwchar
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
- fgetwchar
- _fgettchar
- _fgetchar
- _fgetwchar
- fgettchar
helpviewer_keywords:
- fgetwchar function
- _fgetchar function
- fgettchar function
- _fgetwchar function
- _fgettchar function
- standard input, reading from
- fgetchar function
ms.assetid: 8bce874c-701a-41a3-b1b2-feff266fb5b9
ms.openlocfilehash: 90a97308b8c60776d52e58feb84c5398456f26d5
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940867"
---
# <a name="_fgetchar-_fgetwchar"></a>_fgetchar, _fgetwchar

Přečte znak ze **standardního vstupu**.

## <a name="syntax"></a>Syntaxe

```C
int _fgetchar( void );
wint_t _fgetwchar( void );
```

## <a name="return-value"></a>Návratová hodnota

fgetchar vrátí znak načtený jako **int** nebo vrátí `EOF` k označení chyby nebo konce souboru.  **\_** fgetwchar vrátí jako [wint_t](../../c-runtime-library/standard-types.md), což je celý znak, který odpovídá znaku Read nebo vrátí `WEOF` k označení chyby nebo konce souboru.  **\_** U obou funkcí použijte **feof** nebo **trajekt** k rozlišení mezi chybou a stavem konce souboru.

## <a name="remarks"></a>Poznámky

Tyto funkce čtou jeden znak ze **standardního vstupu**. Funkce poté zvýší přidružený ukazatel na soubor (je-li definován), aby ukazoval na další znak. Pokud je datový proud na konci souboru, je nastaven indikátor konce souboru pro datový proud.

**_fgetchar** je ekvivalentem `fgetc( stdin )`. Je také ekvivalentní s funkcí **GetChar**, ale je implementována pouze jako funkce, nikoli jako funkce a makro. **_fgetwchar** je verze **_fgetchar**pro nejrůznější znaky.

Tyto funkce nejsou kompatibilní se standardem ANSI.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_fgettchar**|**_fgetchar**|**_fgetchar**|**_fgetwchar**|

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_fgetchar**|\<stdio.h>|
|**_fgetwchar**|\<stdio. h > nebo \<WCHAR. h >|

Konzola není v aplikacích Univerzální platforma Windows (UWP) podporována. Standardní popisovače streamů, které jsou spojeny s konzolou –**stdin**, **stdout**a **stderr**– musí být přesměrované před tím, než je funkce běhového běhu v aplikacích pro UWP můžou použít. Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_fgetchar.c
// This program uses _fgetchar to read the first
// 80 input characters (or until the end of input)
// and place them into a string named buffer.
//

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   char buffer[81];
   int  i, ch;

   // Read in first 80 characters and place them in "buffer":
   ch = _fgetchar();
   for( i=0; (i < 80 ) && ( feof( stdin ) == 0 ); i++ )
   {
      buffer[i] = (char)ch;
      ch = _fgetchar();
   }

   // Add null to end string
   buffer[i] = '\0';
   printf( "%s\n", buffer );
}
```

```Output

      Line one.
Line two.Line one.
Line two.
```

## <a name="see-also"></a>Viz také:

[Vstup/výstup datového proudu](../../c-runtime-library/stream-i-o.md)<br/>
[fputc, fputwc](fputc-fputwc.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
