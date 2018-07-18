---
title: fgets fgetws – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 07/11/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- fgets
- fgetws
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
- _fgetts
- fgetws
- fgets
dev_langs:
- C++
helpviewer_keywords:
- _fgetts function
- streams, getting strings from
- streams, reading from
- fgets function
- fgetws function
- fgetts function
ms.assetid: ad549bb5-df98-4ccd-a53f-95114e60c4fc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9c155150a364c2cbbd230c56678e6e7dcb4e4fde
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/13/2018
ms.locfileid: "39027164"
---
# <a name="fgets-fgetws"></a>fgets, fgetws

Získáte řetězec z datového proudu.

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
Umístění úložiště pro data.

*numChars*<br/>
Maximální počet znaků pro čtení.

*Stream*<br/>
Ukazatel na **souboru** struktury.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrací *str*. **NULL** se vrátí k označení chyby nebo podmínku endovém souborovém. Použití **feof** nebo **ferror** k určení, zda došlo k chybě. Pokud *str* nebo *stream* je ukazatel s hodnotou null, nebo *numChars* je menší než nebo rovna hodnotě nula, tato funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v [ Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, **errno** je nastavena na **EINVAL** a funkce vrátí **NULL**.

Zobrazit [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o těchto a dalších chybových kódech.

## <a name="remarks"></a>Poznámky

**Fgets** funkce přečte řetězce ze vstupu *stream* argumentu a uloží jej do *str*. **fgets** čtení znaků z aktuální pozice datového proudu a včetně první znak nového řádku na konec datového proudu, nebo dokud číst počet znaků, které se rovná *numChars* – 1, podle toho, co nastane dřív. Výsledek je uložen v *str* připojeným znakem null. Nový řádek znak pro čtení, je zahrnutá v řetězci.

**fgetws –** je verze širokého znaku **fgets**.

**fgetws –** přečte argument širokého znaku *str* jako řetězec vícebajtového znaku nebo širokého znaku řetězce podle toho, zda *stream* je otevřen v textovém nebo binárním režimu v uvedeném pořadí. Další informace o používání textové a binární režimy v kódování Unicode a vícebajtových stream vstupně-najdete v tématu [textového a binárního režimu souboru vstupně-výstupních operací](../../c-runtime-library/text-and-binary-mode-file-i-o.md) a [vstupně-výstupní Stream kódování Unicode v textovém a binárním režimu](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fgetts –**|**fgets**|**fgets**|**fgetws –**|

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fgets**|\<stdio.h>|
|**fgetws –**|\<stdio.h > nebo \<wchar.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

### <a name="input-crtfgetstxt"></a>Vstup: crt_fgets.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Výstup

```Output
Line one.
```

## <a name="see-also"></a>Viz také:

[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[fputs, fputws](fputs-fputws.md)<br/>
[gets, _getws](../../c-runtime-library/gets-getws.md)<br/>
[puts, _putws](puts-putws.md)<br/>
