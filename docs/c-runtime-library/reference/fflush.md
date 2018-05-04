---
title: fflush – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- streams, flushing
- flushing
- fflush function
ms.assetid: 8bbc753f-dc74-4e77-b563-74da2835e92b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 72f0812e713d0d474363dcc5f79cc11eddb46020
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="fflush"></a>fflush

Počet vyprázdnění datového proudu.

## <a name="syntax"></a>Syntaxe

```C
int fflush(
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*Datový proud*<br/>
Ukazatel na **souboru** struktura.

## <a name="return-value"></a>Návratová hodnota

**fflush –** vrátí hodnotu 0, pokud vyrovnávací paměť byla byla úspěšně zapsána. Hodnota 0, se vrátí v případech, ve kterých zadaného datového proudu má bez vyrovnávací paměti nebo je otevřen jen pro čtení. Vrácená hodnota **EOF** označuje chybu.

> [!NOTE]
> Pokud **fflush –** vrátí **EOF**, data mohou být ztracena z důvodu chyby zápisu. Při nastavování obslužné rutiny kritická chyba, je nejbezpečnější vypnutí ukládání do vyrovnávací paměti s **setvbuf –** funkce nebo pomocí rutiny nízké úrovně vstupně-výstupních operací, jako například **_Otevřít**, **_close –**, a **_Write –** místo funkce datového proudu vstupně-výstupní operace.

## <a name="remarks"></a>Poznámky

**Fflush –** funkce vyprázdnění datového proudu *datového proudu*. Pokud datový proud byl otevřen v zápisu režimu, nebo byl otevřen v režimu aktualizace a poslední operace byla zápis, obsah vyrovnávací paměti datového proudu se zapisují do podkladový soubor nebo zařízení a vyrovnávací paměť se zahodí. Pokud datový proud byl otevřen v režimu pro čtení nebo datový proud má bez vyrovnávací paměti, volání **fflush –** nemá žádný vliv, a všechny vyrovnávací paměti je zachován. Volání **fflush –** Neguje účinku jakékoli předchozí volání **ungetc –** pro datový proud. Datový proud zůstane otevřený po volání.

Pokud *datového proudu* je **NULL**, chování je stejné jako volání **fflush –** na každý otevřít datový proud. Všechny datové proudy otevřít v režimu zápisu a jsou vyprázdněny všechny datové proudy otevřít v režimu aktualizace kde poslední akci byla zápis. Volání nemá žádný vliv na jiné datové proudy.

Vyrovnávací paměti se obvykle spravuje podle operačního systému, která určuje optimální čas automaticky zapsat data na disk: Pokud vyrovnávací paměť je plná, když datový proud je uzavřen nebo když program ukončí normálně bez zavírání datového proudu. Funkce běhové knihovny k potvrzení na disku umožňuje Ujistěte se, že je důležitá data zapsána přímo na disku, nikoli do vyrovnávací paměti operačního systému. Bez přepisování existujícího programu, můžete povolit tuto funkci pomocí propojení objektu soubory programu s COMMODE.OBJ. Ve výsledném spustitelného souboru, volá, aby se **_flushall –** zapisovat obsah všech vyrovnávací paměti na disk. Pouze **_flushall –** a **fflush –** jsou ovlivněné COMMODE.OBJ.

Informace o řízení funkce potvrzení na disku naleznete v tématu [vstupně-výstupní datový proud](../../c-runtime-library/stream-i-o.md), [fopen –](fopen-wfopen.md), a [_fdopen –](fdopen-wfdopen.md).

Tato funkce zamkne volající vlákno a je proto bezpečné pro přístup z více vláken. Bez uzamčení verze, najdete v části **_fflush_nolock –**.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fflush**|\<stdio.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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

```Output

      This is a test
This is a test

```

```Output

      This is a test
This is a testEnter a sentence of four words with scanf: This is a test
This
is
a
test
Enter the same sentence with gets: This is a test
This is a test
```

## <a name="see-also"></a>Viz také

[Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_flushall](flushall.md)<br/>
[setvbuf](setvbuf.md)<br/>
