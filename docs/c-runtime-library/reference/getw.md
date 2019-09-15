---
title: _getw
ms.date: 11/04/2016
api_name:
- _getw
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
- _getw
helpviewer_keywords:
- _getw function
- integers, getting from streams
- getw function
ms.assetid: ef75facc-b84e-470f-9f5f-8746c90822a0
ms.openlocfilehash: ad03c92ce90542ecae13609ee228ad094f64fc07
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954880"
---
# <a name="_getw"></a>_getw

Získá celé číslo z datového proudu.

## <a name="syntax"></a>Syntaxe

```C
int _getw(
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*stream*<br/>
Ukazatel na strukturu **souborů** .

## <a name="return-value"></a>Návratová hodnota

**_getw** vrací celočíselnou hodnotu čtenou. Návratová hodnota **EOF** značí chybu nebo konec souboru. Vzhledem k tomu, že hodnota **EOF** je také legitimní celočíselná hodnota, použijte **feof** nebo **trajekt** k ověření konce souboru nebo chybové podmínky. Pokud má *datový proud* **hodnotu null**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, **errno** je nastaven na **EINVAL** a funkce vrátí **EOF**.

## <a name="remarks"></a>Poznámky

Funkce **_getw** čte další binární hodnotu typu **int** ze souboru přidruženého ke *streamování* a zvýší přidružený ukazatel na soubor (pokud existuje), který odkazuje na další nepřečtený znak. **_getw** nepředpokládá žádné speciální zarovnání položek v datovém proudu. Problémy s přenosem může nastat v **_getw** , protože velikost typu **int** a řazení bajtů v rámci typu **int** se v různých systémech liší.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_getw**|\<stdio.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_getw.c
// This program uses _getw to read a word
// from a stream, then performs an error check.

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   FILE *stream;
   int i;

   if( fopen_s( &stream, "crt_getw.txt", "rb" ) )
      printf( "Couldn't open file\n" );
   else
   {
      // Read a word from the stream:
      i = _getw( stream );

      // If there is an error...
      if( ferror( stream ) )
      {
         printf( "_getw failed\n" );
         clearerr_s( stream );
      }
      else
         printf( "First data word in file: 0x%.4x\n", i );
      fclose( stream );
   }
}
```

### <a name="input-crt_getwtxt"></a>Vstup: crt_getw. txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Výstup

```Output
First data word in file: 0x656e694c
```

## <a name="see-also"></a>Viz také:

[Vstup/výstup datového proudu](../../c-runtime-library/stream-i-o.md)<br/>
[_putw](putw.md)<br/>
