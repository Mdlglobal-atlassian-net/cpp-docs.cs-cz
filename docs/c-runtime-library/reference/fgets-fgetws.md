---
title: fgets –, fgetws – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: e92deea033443ec942895d2aef2d1a307ac89f34
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32402017"
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

*str –*<br/>
Umístění úložiště pro data.

*numChars*<br/>
Maximální počet znaků ke čtení.

*Datový proud*<br/>
Ukazatel na **souboru** struktura.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí *str*. **NULL** je vrácen do indikují chybu nebo podmínku end souboru. Použití **feof –** nebo **ferror –** k určení, zda došlo k chybě. Pokud *str* nebo *datového proudu* je ukazatel s hodnotou null, nebo *numChars* je menší než nebo rovna hodnotě nula, tato funkce volá obslužnou rutinu neplatný parametr, jak je popsáno v [ Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění **errno** je nastaven na **einval –** a funkce vrátí hodnotu **NULL**.

V tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o těchto a dalších kódy chyb.

## <a name="remarks"></a>Poznámky

**Fgets –** funkce načte řetězec ze vstupu *datového proudu* argument a uloží jej do *str*. **fgets –** čte znaků z aktuální pozici datového proudu k a včetně první znak nového řádku na konec datového proudu, nebo dokud počet znaků pro čtení se rovná *numChars* – 1, nastane dříve. Výsledek uložené v *str* spolu s znak hodnoty null. Znak nový řádek, pokud pro čtení, je zahrnuta v řetězci.

**fgetws –** je verze široká charakterová **fgets –**.

**fgetws –** čte argument široká charakterová *str* jako vícebajtových znaků řetězec nebo řetězec široká charakterová podle jestli *datového proudu* je otevřen v režimu textových nebo binárního režimu v uvedeném pořadí. Další informace o používání textovém a binárním režimu v kódování Unicode a vícebajtové datového proudu I/O najdete v tématu [Text a vstupně-výstupní soubor binárního režimu](../../c-runtime-library/text-and-binary-mode-file-i-o.md) a [vstupně-výstupní datový proud Unicode v textovém a binárním režimu](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fgetts –**|**fgets –**|**fgets –**|**fgetws –**|

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fgets –**|\<stdio.h>|
|**fgetws –**|\<stdio.h > nebo \<wchar.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_fgets.c
// This program uses fgets to display
// a line from a file on the screen.
//

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

## <a name="see-also"></a>Viz také

[Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[fputs, fputws](fputs-fputws.md)<br/>
[gets, _getws](../../c-runtime-library/gets-getws.md)<br/>
[puts, _putws](puts-putws.md)<br/>
