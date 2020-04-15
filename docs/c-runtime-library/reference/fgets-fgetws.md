---
title: fgets, fgetws
ms.date: 4/2/2020
api_name:
- fgets
- fgetws
- _o_fgets
- _o_fgetws
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
ms.openlocfilehash: a1120529157801aac5cf1c4fd61f844fde443bed
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346870"
---
# <a name="fgets-fgetws"></a>fgets, fgetws

Získat řetězec z datového proudu.

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

*Str*<br/>
Umístění úložiště pro data.

*numChars*<br/>
Maximální počet znaků ke čtení.

*Proudu*<br/>
Ukazatel na **strukturu FILE.**

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí *str*. **Hodnota NULL** je vrácena k označení chyby nebo podmínky konce souboru. Použijte **feof** nebo **ferror** k určení, zda došlo k chybě. Pokud *str* nebo *stream* je nula ukazatel nebo *numChars* je menší nebo rovno nule, tato funkce vyvolá neplatný parametr obslužné rutiny, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, **je chybné číslo** nastaveno na **hodnotu EINVAL** a funkce vrátí **hodnotu NULL**.

Další informace o těchto a dalších kódech chyb naleznete v [_doserrno, errno, _sys_errlist a _sys_nerr.](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)

## <a name="remarks"></a>Poznámky

Funkce **fgets** přečte řetězec z argumentu vstupního *datového proudu* a uloží jej do *str*. **fgets** čte znaky z aktuální pozice datového proudu do a včetně prvního znaku nového řádku, na konec datového proudu, nebo dokud se počet přečtených znaků nerovná *numChars* - 1, podle toho, co nastane dříve. Výsledek uložený v *str* je připojen s nulovým znakem. Znak nového řádku, pokud je přečten, je součástí řetězce.

**fgetws** je širokoznaková verze **fgets**.

**fgetws** přečte argument široký znak *str* jako řetězec vícebajtových znaků nebo řetězec s širokým znakem podle toho, zda je *datový proud* otevřen v textovém nebo binárním režimu. Další informace o používání režimů textu a binárních režimů v režimech Unicode a vícebajtových datových proudech vi/v naleznete v [tématu Text a binární režim V/O souboru](../../c-runtime-library/text-and-binary-mode-file-i-o.md) a [V. a V. v režimu Text a Binární režimy](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fgetts**|**fgets**|**fgets**|**fgetws**|

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fgets**|\<stdio.h>|
|**fgetws**|\<stdio.h> \<nebo wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

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

### <a name="input-crt_fgetstxt"></a>Vstup: crt_fgets.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Výstup

```Output
Line one.
```

## <a name="see-also"></a>Viz také

[I/O proudu](../../c-runtime-library/stream-i-o.md)<br/>
[fputs, fputws](fputs-fputws.md)<br/>
[gets, _getws](../../c-runtime-library/gets-getws.md)<br/>
[puts, _putws](puts-putws.md)<br/>
