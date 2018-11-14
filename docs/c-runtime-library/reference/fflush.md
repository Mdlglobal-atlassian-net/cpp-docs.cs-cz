---
title: fflush
ms.date: 11/04/2016
apiname:
- fflush
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
- fflush
helpviewer_keywords:
- streams, flushing
- flushing
- fflush function
ms.assetid: 8bbc753f-dc74-4e77-b563-74da2835e92b
ms.openlocfilehash: d03d20ee5024915d0ca4c5a21db4159e8c4f876a
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51329108"
---
# <a name="fflush"></a>fflush

Vyprázdní datového proudu.

## <a name="syntax"></a>Syntaxe

```C
int fflush(
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*Stream*<br/>
Ukazatel na **souboru** struktury.

## <a name="return-value"></a>Návratová hodnota

**fflush –** vrátí hodnotu 0, pokud byl úspěšně vyprázdní vyrovnávací paměť. Také je vrácena hodnota 0 v případech, ve kterých má bez vyrovnávací paměti nebo otevřen jen pro čtení zadaného datového proudu. Vrácená hodnota **EOF** označuje chybu.

> [!NOTE]
> Pokud **fflush –** vrátí **EOF**, data mohou být ztracena kvůli chybě zápisu. Při nastavování obslužné rutiny kritická chyba, je nejbezpečnější vypnout ukládání do vyrovnávací paměti s **setvbuf –** funkce nebo použít I/O rutiny nízké úrovně, jako **_Otevřít**, **_Zavřít**, a **_write** namísto funkce datového proudu vstupně-výstupních operací.

## <a name="remarks"></a>Poznámky

**Fflush –** funkce vyprázdní datový proud *stream*. Pokud byl datový proud otevřen v zápisu režimu, nebo byl otevřen v režimu aktualizace a byl poslední operaci zápisu, obsah vyrovnávací paměti datového proudu se zapisují do základního souboru nebo zařízení a vyrovnávací paměť se zahodí. Pokud byl datový proud otevřen v režimu pro čtení, nebo pokud datový proud bez vyrovnávací paměti, volání **fflush –** nemá žádný vliv, a všechny vyrovnávací paměti je zachován. Volání **fflush –** Neguje působení jakékoli předchozí volání **ungetc –** pro datový proud. Datový proud zůstane otevřený po volání.

Pokud *stream* je **NULL**, chování je stejné jako volání **fflush –** na každý otevřít datový proud. Všechny datové proudy otevřen v režimu zápisu a, vyprázdní všechny datové proudy otevřen v režimu aktualizace kterých se spustil poslední operaci zápisu. Volání nemá žádný vliv na jiné datové proudy.

Vyrovnávací paměti jsou obvykle udržuje operačního systému, který určuje optimální čas automaticky zapisovat data na disk: Pokud vyrovnávací paměť je plná, když datový proud je uzavřen nebo když program skončí obvykle bez zavření datového proudu. Funkce potvrzení na disku knihovny run-time umožňuje zajistit, že důležitá data se zapisují přímo na disk, nikoli do vyrovnávací paměti operačního systému. Bez přepsání existující program, můžete povolit tuto funkci tak propojování souborů objektů programu s COMMODE.OBJ. Výsledný spustitelný soubor volá do **_flushall –** zapisovat obsah všech vyrovnávací paměti na disk. Pouze **_flushall –** a **fflush –** jsou ovlivněny COMMODE.OBJ.

Informace o řízení funkce potvrzení na disku naleznete v tématu [vstupně-výstupní operace Stream](../../c-runtime-library/stream-i-o.md), [fopen](fopen-wfopen.md), a [_fdopen –](fdopen-wfdopen.md).

Tato funkce uzamkne volající vlákno a proto je bezpečná pro vlákno. Nezamykací verzi naleznete v tématu **_fflush_nolock –**.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fflush**|\<stdio.h>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_fflush.c
#include <stdio.h>
#include <conio.h>

int main( void )
{
   int integer;
   char string[81];

   // Read each word as a string.
   printf( "Enter a sentence of four words with scanf: " );
   for( integer = 0; integer < 4; integer++ )
   {
      scanf_s( "%s", string, sizeof(string) );
      printf( "%s\n", string );
   }

   // You must flush the input buffer before using gets.
   // fflush on input stream is an extension to the C standard
   fflush( stdin );
   printf( "Enter the same sentence with gets: " );
   gets_s( string, sizeof(string) );
   printf( "%s\n", string );
}
```

```Input
This is a test
This is a test
```

```Output
Enter a sentence of four words with scanf: This is a test
This
is
a
test
Enter the same sentence with gets: This is a test
This is a test
```

## <a name="see-also"></a>Viz také:

[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_flushall](flushall.md)<br/>
[setvbuf](setvbuf.md)<br/>
