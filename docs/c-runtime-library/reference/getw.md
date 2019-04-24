---
title: _getw
ms.date: 11/04/2016
apiname:
- _getw
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
- _getw
helpviewer_keywords:
- _getw function
- integers, getting from streams
- getw function
ms.assetid: ef75facc-b84e-470f-9f5f-8746c90822a0
ms.openlocfilehash: 615d3ac9bdc73ad200368eaeabf7c84951bc91ae
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157627"
---
# <a name="getw"></a>_getw

Získá celé číslo z datového proudu.

## <a name="syntax"></a>Syntaxe

```C
int _getw(
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*stream*<br/>
Ukazatel **souboru** struktury.

## <a name="return-value"></a>Návratová hodnota

**_getw –** vrátí celočíselnou hodnotu číst. Vrácená hodnota **EOF** označuje chybu nebo konec souboru. Ale protože **EOF** hodnota je také legitimní celočíselnou hodnotu, použijte **feof** nebo **ferror** ověření endovém souborovém nebo chybová podmínka. Pokud *stream* je **NULL**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, **errno** je nastavena na **EINVAL** a funkce vrátí **EOF**.

## <a name="remarks"></a>Poznámky

**_Getw –** funkce přečte další binární hodnota typu **int** ze souboru spojené s *stream* a zvýší přidružený ukazatel na soubor (pokud existuje) tak, aby odkazoval Další nepřečtené znak. **_getw –** nepřebírá žádné speciální zarovnání položek v datovém proudu. Může dojít k problémům s přenos s **_getw –** protože velikost **int** typu a pořadí bajtů v rámci **int** typ se liší mezi systémy.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_getw**|\<stdio.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

### <a name="input-crtgetwtxt"></a>Vstup: crt_getw.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Výstup

```Output
First data word in file: 0x656e694c
```

## <a name="see-also"></a>Viz také:

[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[_putw](putw.md)<br/>
