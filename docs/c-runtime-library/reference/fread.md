---
title: fread
ms.date: 11/28/2018
api_name:
- fread
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
- fread
helpviewer_keywords:
- reading data [C++], from input streams
- fread function
- data [C++], reading from input stream
- streams [C++], reading data from
ms.assetid: 9a3c1538-93dd-455e-ae48-77c1e23c53f0
ms.openlocfilehash: 7cf4542a656798f7e2431b2f939df1b5d6396144
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956820"
---
# <a name="fread"></a>fread

Načte data z datového proudu.

## <a name="syntax"></a>Syntaxe

```C
size_t fread(
   void *buffer,
   size_t size,
   size_t count,
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*vyrovnávací paměti*<br/>
Umístění úložiště pro data

*hodnota*<br/>
Velikost položky v bajtech

*výpočtu*<br/>
Maximální počet položek, které se mají přečíst

*stream*<br/>
Ukazatel na strukturu **souborů** .

## <a name="return-value"></a>Návratová hodnota

**fread** vrátí počet úplných položek, které jsou skutečně čteny, což může být menší než *počet* , pokud dojde k chybě, nebo pokud byl zjištěn konec souboru před dosažením *počtu*. Použijte funkci **feof** nebo **Deferred** k odlišení chyby čtení z podmínky konce souboru. Pokud je *Velikost* nebo *počet* 0, **fread** vrátí 0 a obsah vyrovnávací paměti zůstane beze změny. Pokud je *datový proud* nebo *vyrovnávací paměť* ukazatel s hodnotou null, vyvolá **fread** neplatnou obslužnou rutinu parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tato funkce nastaví **errno** na **EINVAL** a vrátí hodnotu 0.

Další informace o těchto kódech chyb naleznete v tématech [ \_doserrno\_, errno, \_\_sys errlist a \_sys NERR](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

## <a name="remarks"></a>Poznámky

Funkce **fread** čte až do *počtu* položek *velikosti* bajtů ze vstupního *datového proudu* a ukládá je do *vyrovnávací paměti*. Ukazatel na soubor přidružený ke *streamu* (pokud existuje) se zvyšuje o počet skutečně přečtených bajtů. Pokud je daný datový proud otevřen v [textovém režimu](../../c-runtime-library/text-and-binary-mode-file-i-o.md), systém Windows ve stylu newlines se převede na newlines ve stylu systému UNIX. To znamená, že páry znak návratového kanálu (CRLF) jsou nahrazeny znaky jednoduchého řádku (LF). Náhrada nemá žádný vliv na ukazatel na soubor nebo na vrácenou hodnotu. Pozice ukazatele na soubor je neurčitá, pokud dojde k chybě. Nelze určit hodnotu částečného čtení položky.

Při použití v datovém proudu v textovém režimu platí, že pokud je velikost požadovaných dat (tj. *počet* *velikostí* \* ) větší než nebo rovna velikosti vyrovnávací paměti interního **souboru** \* (ve výchozím nastavení je to 4096 bajtů, lze konfigurovat pomocí [ setvbuf –](../../c-runtime-library/reference/setvbuf.md)), data streamu se zkopírují přímo do uživatelem zadané vyrovnávací paměti a konverze nového řádku se provádí v této vyrovnávací paměti. Vzhledem k tomu, že převedená data můžou být kratší než data streamu zkopírovaná do vyrovnávací paměti, *Velikost* *return_value* \* dat za *vyrovnávací paměť*\[(kde *return_value* je návratová hodnota z **fread**) může obsahuje převedená data ze souboru. Z tohoto důvodu doporučujeme, abyste koncovým znakům ukončujícím hodnoty null ve *vyrovnávací paměti*\[*return_value* \* *Velikost*], pokud je záměr vyrovnávací paměti fungovat jako řetězec ve stylu jazyka C. Podrobnosti o účincích v textovém režimu a binárním režimu najdete v tématu [fopen](fopen-wfopen.md) .

Tato funkce zamkne další vlákna. Pokud potřebujete neuzamykání verze, použijte **_fread_nolock**.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fread**|\<stdio.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_fread.c
// This program opens a file named FREAD.OUT and
// writes 25 characters to the file. It then tries to open
// FREAD.OUT and read in 25 characters. If the attempt succeeds,
// the program displays the number of actual items read.

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char list[30];
   int  i, numread, numwritten;

   // Open file in text mode:
   if( fopen_s( &stream, "fread.out", "w+t" ) == 0 )
   {
      for ( i = 0; i < 25; i++ )
         list[i] = (char)('z' - i);
      // Write 25 characters to stream
      numwritten = fwrite( list, sizeof( char ), 25, stream );
      printf( "Wrote %d items\n", numwritten );
      fclose( stream );

   }
   else
      printf( "Problem opening the file\n" );

   if( fopen_s( &stream, "fread.out", "r+t" ) == 0 )
   {
      // Attempt to read in 25 characters
      numread = fread( list, sizeof( char ), 25, stream );
      printf( "Number of items read = %d\n", numread );
      printf( "Contents of buffer = %.25s\n", list );
      fclose( stream );
   }
   else
      printf( "File could not be opened\n" );
}
```

```Output
Wrote 25 items
Number of items read = 25
Contents of buffer = zyxwvutsrqponmlkjihgfedcb
```

## <a name="see-also"></a>Viz také:

[Vstup/výstup datového proudu](../../c-runtime-library/stream-i-o.md)<br/>
[Vstupně-výstupní operace textu a binárního souboru](../../c-runtime-library/text-and-binary-mode-file-i-o.md)<br/>
[fopen](fopen-wfopen.md)<br/>
[fwrite](fwrite.md)<br/>
[_read](read.md)<br/>
