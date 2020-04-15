---
title: fread_s
ms.date: 4/2/2020
api_name:
- fread_s
- _o_fread_s
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
- fread_s
- stdio/fread_s
ms.assetid: ce735de0-f005-435d-a8f2-6f4b80ac775e
ms.openlocfilehash: 97f7ca80d4b458b952393a5b1f72bebe0bdb0d9f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346129"
---
# <a name="fread_s"></a>fread_s

Čte data z datového proudu. Tato verze [fread](fread.md) má vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
size_t fread_s(
   void *buffer,
   size_t bufferSize,
   size_t elementSize,
   size_t count,
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*Vyrovnávací paměti*<br/>
Umístění úložiště pro data.

*Buffersize*<br/>
Velikost cílové vyrovnávací paměti v bajtech.

*elementVelikost*<br/>
Velikost položky číst v bajtů.

*Počet*<br/>
Maximální počet položek ke čtení.

*Proudu*<br/>
Ukazatel na **strukturu FILE.**

## <a name="return-value"></a>Návratová hodnota

**fread_s** vrátí počet (celé) položky, které byly přečteny do vyrovnávací paměti, které mohou být menší než *počet,* pokud dojde k chybě čtení nebo konec souboru před *dosažením count.* Funkce **feof** nebo **ferror** slouží k odlišení chyby od stavu konce souboru. Pokud *velikost* nebo *počet* je 0, **vrátí fread_s** 0 a obsah vyrovnávací paměti jsou beze změny. Pokud *datový proud* nebo vyrovnávací *paměť* je nulový ukazatel, **fread_s** vyvolá neplatný obslužnou rutinu parametru, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, tato funkce nastaví **errno** na **EINVAL** a vrátí 0.

Další informace o kódech chyb naleznete [v tématech _doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **fread_s** čte až *počítat* položky *elementSize* bajtů ze vstupního *datového proudu* a ukládá je do *vyrovnávací paměti*.  Ukazatel souboru, který je spojen s *datovým proudem* (pokud existuje) se zvýší o počet bajtů skutečně číst. Pokud je daný datový proud otevřen v textovém režimu, dvojice přímotivního podpájení vozíku se nahradí znaky podávání jednoho řádku. Nahrazení nemá žádný vliv na ukazatel souboru nebo vrácenou hodnotu. Pozice ukazatele souboru je neurčitá, pokud dojde k chybě. Nelze určit hodnotu částečně přečtené položky.

Tato funkce uzamkne ostatní vlákna. Pokud požadujete verzi bez uzamčení, použijte **_fread_nolock**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fread_s**|\<stdio.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```cpp
// crt_fread_s.c
// Command line: cl /EHsc /nologo /W4 crt_fread_s.c
//
// This program opens a file that's named FREAD.OUT and
// writes characters to the file. It then tries to open
// FREAD.OUT and read in characters by using fread_s. If the attempt succeeds,
// the program displays the number of actual items read.

#include <stdio.h>

#define BUFFERSIZE 30
#define DATASIZE 22
#define ELEMENTCOUNT 2
#define ELEMENTSIZE (DATASIZE/ELEMENTCOUNT)
#define FILENAME "FREAD.OUT"

int main( void )
{
   FILE *stream;
   char list[30];
   int  i, numread, numwritten;

   for ( i = 0; i < DATASIZE; i++ )
      list[i] = (char)('z' - i);
   list[DATASIZE] = '\0'; // terminal null so we can print it

   // Open file in text mode:
   if( fopen_s( &stream, FILENAME, "w+t" ) == 0 )
   {
      // Write DATASIZE characters to stream
      printf( "Contents of buffer before write/read:\n\t%s\n\n", list );
      numwritten = fwrite( list, sizeof( char ), DATASIZE, stream );
      printf( "Wrote %d items\n\n", numwritten );
      fclose( stream );
   } else {
      printf( "Problem opening the file\n" );
      return -1;
   }

   if( fopen_s( &stream, FILENAME, "r+t" ) == 0 )   {
      // Attempt to read in characters in 2 blocks of 11
      numread = fread_s( list, BUFFERSIZE, ELEMENTSIZE, ELEMENTCOUNT, stream );
      printf( "Number of %d-byte elements read = %d\n\n", ELEMENTSIZE, numread );
      printf( "Contents of buffer after write/read:\n\t%s\n", list );
      fclose( stream );
   } else {
      printf( "File could not be opened\n" );
      return -1;
   }
}
```

```Output
Contents of buffer before write/read:
        zyxwvutsrqponmlkjihgfe

Wrote 22 items

Number of 11-byte elements read = 2

Contents of buffer after write/read:
        zyxwvutsrqponmlkjihgfe
```

## <a name="see-also"></a>Viz také

[I/O proudu](../../c-runtime-library/stream-i-o.md)<br/>
[fwrite](fwrite.md)<br/>
[_read](read.md)<br/>
