---
title: fread
ms.date: 11/28/2018
apiname:
- fread
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
- fread
helpviewer_keywords:
- reading data [C++], from input streams
- fread function
- data [C++], reading from input stream
- streams [C++], reading data from
ms.assetid: 9a3c1538-93dd-455e-ae48-77c1e23c53f0
ms.openlocfilehash: 7248eb08409b50d855dbb70c7638a856302b345b
ms.sourcegitcommit: bd637e9c39650cfd530520ea978a22fa4caa0e42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/07/2019
ms.locfileid: "55849968"
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
Maximální počet položek, které chcete načíst.

*stream*<br/>
Ukazatel na **souboru** struktury.

## <a name="return-value"></a>Návratová hodnota

**fread –** vrátí počet celé položky ve skutečnosti čtení, které mohou být menší než *počet* Pokud dojde k chybě nebo pokud je nalezen konec souboru před dosažením *počet*. Použití **feof** nebo **ferror** funkce k rozlišení chybu čtení z podmínku ukončení souboru. Pokud *velikost* nebo *počet* je 0, **fread –** vrátí 0 a obsah vyrovnávací paměti jsou beze změny. Pokud *stream* nebo *vyrovnávací paměti* je ukazatel s hodnotou null, **fread –** vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, tato funkce nastaví **errno** k **EINVAL** a vrátí hodnotu 0.

Zobrazit [ \_doserrno –, errno, \_sys\_errlist, a \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o těchto chybových kódech.

## <a name="remarks"></a>Poznámky

**Fread –** funkce přečte až *počet* položky *velikost* bajtů ze vstupu *stream* a ukládá je v *vyrovnávací paměti* . Ukazatel na soubor přidružený k *stream* (pokud existuje) je zvýšen počet skutečně přečtených bajtů. Pokud daný datový proud je otevřen v [textovém režimu](../../c-runtime-library/text-and-binary-mode-file-i-o.md), vložení znaků newline Windows-style se převedou na vložení znaků newline stylu systému Unix. To znamená páry znaků CR návratový znak odřádkování (CRLF) jsou nahrazeny jednoho konce řádku (LF) znaků. Pokud chcete nahrazení nemá žádný vliv na ukazatel na soubor nebo návratovou hodnotu. Ukazatel na soubor pozice je neurčité, pokud dojde k chybě. Hodnota částečně čtení položky nelze určit.

Při použití režimu textového datového proudu, pokud požadované množství dat (to znamená *velikost* \* *počet*) je větší než nebo rovna hodnotě vnitřní **souboru** \*velikost vyrovnávací paměti (výchozí hodnota je 4096 bajtů, konfigurovat pomocí [setvbuf –](../../c-runtime-library/reference/setvbuf.md)), streamování dat je zkopírován přímo do uživatelem zadaného vyrovnávací paměti a nového řádku převod se provádí ve vyrovnávací paměti. Protože převedená data mohou být kratší než streamování dat zkopírována do mezipaměti, data posledních *vyrovnávací paměti*\[*return_ value* \* *velikost*] () kde *return_ value* je návratová hodnota z **fread –**) mohou obsahovat nepřevedeném data ze souboru. Z tohoto důvodu doporučujeme vám – s ukončením null znaková data na *vyrovnávací paměti*\[*return_ value* \* *velikost*] Pokud je cílem vyrovnávací paměti aby se choval jako řetězec stylu C. Zobrazit [fopen](fopen-wfopen.md) podrobnosti o důsledcích režimu textového a binárního režimu.

Tato funkce zamezí jiných vláken. Pokud potřebujete nezamykací verzi, použijte **_fread_nolock –**.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fread**|\<stdio.h>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[Textové a binární soubor vstupně-výstupních operací](../../c-runtime-library/text-and-binary-mode-file-i-o.md)<br/>
[fopen –](fopen-wfopen.md)<br/>
[fwrite](fwrite.md)<br/>
[_read](read.md)<br/>
