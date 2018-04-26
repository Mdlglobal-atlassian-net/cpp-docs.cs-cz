---
title: fseek, _fseeki64 – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _fseeki64
- fseek
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
apitype: DLLExport
f1_keywords:
- fseek
- _fseeki64
dev_langs:
- C++
helpviewer_keywords:
- _fseeki64 function
- fseeki64 function
- fseek function
- file pointers [C++], moving
- file pointers [C++]
- seek file pointers
ms.assetid: f6bb1f8b-891c-426e-9e14-0e7e5c62df70
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 266eb1589c97b177057e6a72874261c745acb475
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="fseek-fseeki64"></a>fseek, _fseeki64

Přesune ukazatele souboru do zadaného umístění.

## <a name="syntax"></a>Syntaxe

```C
int fseek(
   FILE *stream,
   long offset,
   int origin
);
int _fseeki64(
   FILE *stream,
   __int64 offset,
   int origin
);
```

### <a name="parameters"></a>Parametry

*Datový proud*<br/>
Ukazatel na **souboru** struktura.

*Posun*<br/>
Počet bajtů z *původu*.

*Počátek*<br/>
Počáteční pozice.

## <a name="return-value"></a>Návratová hodnota

V případě úspěšného **fseek** a **_fseeki64 –** vrátí hodnotu 0. Jinak vrátí nenulovou hodnotu. Na zařízeních nepodporující vyhledávání není definován návratovou hodnotu. Pokud *datového proudu* je ukazatel s hodnotou null, nebo pokud *původu* není jednou z povolených hodnot, které jsou popsané dál, **fseek** a **_fseeki64 –** vyvolání neplatný Obslužná rutina parametru, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, nastavte tyto funkce **errno** k **einval –** a vrátí hodnotu -1.

## <a name="remarks"></a>Poznámky

**Fseek** a **_fseeki64 –** funkce přesune přidružené ukazatele souboru (pokud existuje) *datového proudu* do nového umístění, která je *posun* bajtů z *původu*. Další operace v datovém proudu je provedeno na nové umístění. Na datový proud otevřen pro aktualizace může být další operace čtení nebo zápis. Argument *původu* musí mít jednu z následujících konstanty, které jsou definované v STDIO. V:

|Hodnota počátku|Význam|
|-|-|
**SEEK_CUR –**|Aktuální umístění ukazatele souboru.
**SEEK_END –**|Konec souboru.
**SEEK_SET –**|Začátek souboru.

Můžete použít **fseek** a **_fseeki64 –** aby přemístil ukazatel kdekoli v souboru. Ukazatele mohou být také umístěny přesahuje za konec souboru. **fseek** a **_fseeki64 –** vymaže indikátoru end souboru a Neguje účinku žádné před [ungetc –](ungetc-ungetwc.md) volá proti *datového proudu*.

Po otevření souboru pro připojování dat aktuální pozice v souboru je určen poslední vstupně-výstupní operace, nikoli kde bude probíhat další zápisu. Pokud žádná vstupně-výstupní operace došlo k ještě v souboru otevřen pro přidávání, pozice v souboru je spuštění souboru.

Pro datové proudy otevřít v režimu textových **fseek** a **_fseeki64 –** omezenou použití, protože může způsobit znaků CR vrátit-konce řádku překlady **fseek** a **_ fseeki64 –** k vést k neočekávaným výsledkům. Jediným **fseek** a **_fseeki64 –** operace zaručit pracovat na datové proudy otevřít v textovém režimu jsou:

- Hledání s posunem 0 relativně k některé z původní hodnoty.

- Vyhledávání od začátku souboru s hodnoty posunu vrácená z volání [ftell –](ftell-ftelli64.md) při použití **fseek** nebo [_ftelli64 –](ftell-ftelli64.md) při použití **_fseeki64 –**.

Také v režimu textových CTRL + Z interpretována jako znak end souboru na vstup. V souborech otevřít pro čtení/zápis [fopen –](fopen-wfopen.md) a všechny související rutiny vyhledávat CTRL + Z na konci souboru a pokud je to možné jej odebrat. To je provést, protože pomocí kombinace **fseek** a [ftell –](ftell-ftelli64.md) nebo **_fseeki64 –** a [_ftelli64 –](ftell-ftelli64.md), chcete-li přesunout v souboru, který končí CTRL + Z může způsobit **fseek** nebo **_fseeki64 –** chovat nesprávně blíží konec souboru.

Když CRT otevře soubor, který začíná s značky pořadí bajtů (BOM), po Kusovníku umístění ukazatele souboru (který je na začátku skutečný obsah souboru). Pokud budete muset **fseek** na začátek souboru, použijte [ftell –](ftell-ftelli64.md) získat počáteční pozice a **fseek** k němu a nikoli na pozici 0.

Tato funkce zamezí jiná vlákna během provádění a je proto bezpečné pro přístup z více vláken. Bez uzamčení verze, najdete v části [_fseek_nolock –, _fseeki64_nolock –](fseek-nolock-fseeki64-nolock.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fseek**|\<stdio.h>|
|**_fseeki64**|\<stdio.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_fseek.c
// This program opens the file FSEEK.OUT and
// moves the pointer to the file's beginning.

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char line[81];
   int  result;

   if ( fopen_s( &stream, "fseek.out", "w+" ) != 0 )
   {
      printf( "The file fseek.out was not opened\n" );
      return -1;
   }
   fprintf( stream, "The fseek begins here: "
                    "This is the file 'fseek.out'.\n" );
   result = fseek( stream, 23L, SEEK_SET);
   if( result )
      perror( "Fseek failed" );
   else
   {
      printf( "File pointer is set to middle of first line.\n" );
      fgets( line, 80, stream );
      printf( "%s", line );
    }
   fclose( stream );
}
```

```Output
File pointer is set to middle of first line.
This is the file 'fseek.out'.
```

## <a name="see-also"></a>Viz také

[Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[ftell, _ftelli64](ftell-ftelli64.md)<br/>
[_lseek, _lseeki64](lseek-lseeki64.md)<br/>
[rewind](rewind.md)<br/>
