---
title: fread
ms.date: 4/2/2020
api_name:
- fread
- _o_fread
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
- fread
helpviewer_keywords:
- reading data [C++], from input streams
- fread function
- data [C++], reading from input stream
- streams [C++], reading data from
ms.assetid: 9a3c1538-93dd-455e-ae48-77c1e23c53f0
ms.openlocfilehash: 26ffd56072f1a5fddc3131a42cd47c145e437b60
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346054"
---
# <a name="fread"></a>fread

Čte data z datového proudu.

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

*Vyrovnávací paměti*<br/>
Umístění úložiště pro data.

*Velikost*<br/>
Velikost položky v bajtech.

*Počet*<br/>
Maximální počet položek ke čtení.

*Proudu*<br/>
Ukazatel na **strukturu FILE.**

## <a name="return-value"></a>Návratová hodnota

**funkce fread** vrátí počet skutečně přečtených celých položek, což může být menší než *počet,* pokud dojde k chybě nebo pokud dojde k ukončení souboru před dosažením *počtu*. Funkce **feof** nebo **ferror** slouží k rozlišení chyby čtení od podmínky konce souboru. Pokud *je velikost* nebo *počet* 0, **fread** vrátí 0 a obsah vyrovnávací paměti jsou beze změny. Pokud *je datový proud* nebo vyrovnávací *paměť* nulovým ukazatelem, **fread** vyvolá neplatnou obslužnou rutinu parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, tato funkce nastaví **errno** na **EINVAL** a vrátí 0.

Další informace o těchto chybových kódech naleznete v tématech [ \_doserrno, errno, \_sys\_errlist a \_sys\_nerr.](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)

## <a name="remarks"></a>Poznámky

Funkce **fread** čte až *počítat* položky *velikosti* bajtů ze vstupního *datového proudu* a ukládá je do *vyrovnávací paměti*. Ukazatel souboru přidružený k *datovému proudu* (pokud existuje) se zvýší o počet skutečně přečtených bajtů. Pokud je daný datový proud otevřen v [textovém režimu](../../c-runtime-library/text-and-binary-mode-file-i-o.md), nové řádky ve stylu systému Windows jsou převedeny na nové řádky ve stylu Unixu. To znamená, že dvojice zpětného kanálu řádku vozíku (CRLF) jsou nahrazeny znaky posuvu jednoho řádku (LF). Nahrazení nemá žádný vliv na ukazatel souboru nebo vrácenou hodnotu. Pozice ukazatele souboru je neurčitá, pokud dojde k chybě. Nelze určit hodnotu částečně přečtené položky.

Při použití v datovém proudu textového režimu, pokud množství požadovaných dat (tj. *počet* *velikostí)* \* je větší nebo rovno vnitřní velikosti vyrovnávací paměti **SOUBORU** \* (ve výchozím nastavení je to 4096 bajtů, konfigurovatelné pomocí [setvbuf](../../c-runtime-library/reference/setvbuf.md)), data datového proudu se zkopíruje přímo do vyrovnávací paměti poskytované uživatelem a převod nového řádku se provádí v této vyrovnávací paměti. Vzhledem k tomu, že převedená data mohou být kratší než data datového proudu zkopírovaná do vyrovnávací paměti, mohou data za *vyrovnávací pamětí*\[*return_value* \* *velikost*] (kde *return_value* je vrácená hodnota z **fread**) obsahovat nepřevedená data ze souboru. Z tohoto důvodu doporučujeme datům znaků null ukončit ve *vyrovnávací paměti*\[*return_value* \* *velikost*] pokud záměr vyrovnávací paměti je fungovat jako řetězec stylu C. Podrobnosti o účincích textového a binárního režimu naleznete v [tématu fopen.](fopen-wfopen.md)

Tato funkce uzamkne ostatní vlákna. Pokud potřebujete verzi bez zamykání, použijte **_fread_nolock**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fread**|\<stdio.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také

[I/O proudu](../../c-runtime-library/stream-i-o.md)<br/>
[Vstupně-nos textu a binárního souboru](../../c-runtime-library/text-and-binary-mode-file-i-o.md)<br/>
[Fopen](fopen-wfopen.md)<br/>
[fwrite](fwrite.md)<br/>
[_read](read.md)<br/>
