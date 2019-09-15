---
title: fgets, fgetws
ms.date: 07/11/2018
api_name:
- fgets
- fgetws
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
- _fgetts
- fgetws
- fgets
helpviewer_keywords:
- _fgetts function
- streams, getting strings from
- streams, reading from
- fgets function
- fgetws function
- fgetts function
ms.assetid: ad549bb5-df98-4ccd-a53f-95114e60c4fc
ms.openlocfilehash: 3f68bee181ebb20eb7a0a2eaca02a72c4dc03616
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957403"
---
# <a name="fgets-fgetws"></a>fgets, fgetws

Získá řetězec z datového proudu.

## <a name="syntax"></a>Syntaxe

```C
char *fgets(
   char *str,
   int numChars,
   FILE *stream
);
wchar_t *fgetws(
   wchar_t *str,
   int numChars,
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Umístění úložiště pro data

*numChars*<br/>
Maximální počet znaků, které mají být čteny.

*stream*<br/>
Ukazatel na strukturu **souborů** .

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrací *str*. K označení chyby nebo stavu konce souboru je vrácena **hodnota null** . K určení, zda došlo k chybě, použijte **feof** nebo **trajekt** . Pokud *str* nebo *Stream* je ukazatel s hodnotou null, nebo je *numChars* menší nebo rovno nule, tato funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, **errno** je nastaven na **EINVAL** a funkce vrátí **hodnotu null**.

Další informace o těchto a dalších chybových kódech naleznete v tématech [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

## <a name="remarks"></a>Poznámky

Funkce **fgets** čte řetězec z argumentu vstupního *datového proudu* a ukládá ho do *str*. **fgets** čte znaky z aktuálního datového proudu do a včetně prvního znaku nového řádku, na konec proudu, nebo dokud se počet čtených znaků nerovná hodnotě *numChars* -1, podle toho, co nastane dřív. Výsledek uložený v *str* je připojen s znakem null. Znak nového řádku, je-li načten, je zahrnut do řetězce.

**fgetws** je verze **fgets**s velkým znakem.

**fgetws** přečte argument pro velký znak *str* jako řetězec vícebajtových znaků nebo řetězec s velkým znakem v závislosti na tom, zda je *datový proud* otevřen v textovém režimu nebo v binárním režimu v uvedeném pořadí. Další informace o používání textových a binárních režimů v kódování Unicode a vícebajtových vstupně-výstupních operacích naleznete v tématu [text a v binárním režimu vstupně](../../c-runtime-library/text-and-binary-mode-file-i-o.md) -výstupních operací a [datových proudů Unicode v textových a binárních režimech](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fgetts**|**fgets**|**fgets**|**fgetws**|

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fgets**|\<stdio.h>|
|**fgetws**|\<stdio. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_fgets.c
// This program uses fgets to display
// the first line from a file.

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char line[100];

   if( fopen_s( &stream, "crt_fgets.txt", "r" ) == 0 )
   {
      if( fgets( line, 100, stream ) == NULL)
         printf( "fgets error\numChars" );
      else
         printf( "%s", line);
      fclose( stream );
   }
}
```

### <a name="input-crt_fgetstxt"></a>Vstup: crt_fgets. txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Výstup

```Output
Line one.
```

## <a name="see-also"></a>Viz také:

[Vstup/výstup datového proudu](../../c-runtime-library/stream-i-o.md)<br/>
[fputs, fputws](fputs-fputws.md)<br/>
[gets, _getws](../../c-runtime-library/gets-getws.md)<br/>
[puts, _putws](puts-putws.md)<br/>
