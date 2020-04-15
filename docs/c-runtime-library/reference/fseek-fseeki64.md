---
title: fseek, _fseeki64
ms.date: 4/2/2020
api_name:
- _fseeki64
- fseek
- _o__fseeki64
- _o_fseek
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
- fseek
- _fseeki64
helpviewer_keywords:
- _fseeki64 function
- fseeki64 function
- fseek function
- file pointers [C++], moving
- file pointers [C++]
- seek file pointers
ms.assetid: f6bb1f8b-891c-426e-9e14-0e7e5c62df70
ms.openlocfilehash: e8f6021a0b770f6b435653c190d5968f9ac50a57
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345758"
---
# <a name="fseek-_fseeki64"></a>fseek, _fseeki64

Přesune ukazatel souboru do určeného umístění.

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

*Proudu*<br/>
Ukazatel na **strukturu FILE.**

*Posun*<br/>
Počet bajtů od *počátku*.

*Původu*<br/>
Počáteční pozice.

## <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, **fseek** a **_fseeki64** vrátí 0. V opačném případě vrátí nenulovou hodnotu. Na zařízeních, která nejsou schopna hledat, není vrácená hodnota definována. Pokud *stream* je ukazatel null, nebo pokud *origin* není jedním z povolených hodnot popsaných níže, **fseek** a **_fseeki64** vyvolat obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, tyto funkce nastavit **errno** **eINVAL** a vrátit -1.

## <a name="remarks"></a>Poznámky

Funkce **fseek** a **_fseeki64** přesune ukazatel souboru (pokud existuje) přidružený k *datovému proudu* do nového umístění, které je *posunuty* bajtů od *počátku*. Další operace na datovém proudu probíhá v novém umístění. V datovém proudu otevřeném pro aktualizaci může být další operace čtení nebo zápis. Původ *argumentu* musí být jedna z následujících konstant definovaných v STDIO. H:

|hodnota původu|Význam|
|-|-|
| **SEEK_CUR** | Aktuální pozice ukazatele souboru. |
| **SEEK_END** | Konec souboru. |
| **SEEK_SET** | Začátek souboru. |

Pomocí **fseek** a **_fseeki64** můžete změnit umístění ukazatele kdekoli v souboru. Ukazatel může být také umístěn za konec souboru. **fseek** a **_fseeki64** vymaže indikátor konce souboru a neguje účinek všech předchozích [ungetc](ungetc-ungetwc.md) volání proti *proudu*.

Při otevření souboru pro připojení dat je aktuální pozice souboru určena poslední vstupně-out operace, nikoli podle místa dalšího zápisu by došlo. Pokud u souboru otevřeného pro připojení ještě nedošlo k žádné operaci vstupně-in, je pozice souboru začátkem souboru.

Pro datové proudy otevřené v textovém režimu **fseek** a **_fseeki64** mají omezené použití, protože překlady datového řádku vozíku může způsobit **fseek** a **_fseeki64** způsobit neočekávané výsledky. Pouze **fseek** a **_fseeki64** operace zaručeně pracovat na datových proudech otevřených v textovém režimu jsou:

- Hledám s posunem 0 vzhledem k libovolné hodnoty původu.

- Hledá od začátku souboru s hodnotou posunu vrácena z volání [ftell](ftell-ftelli64.md) při použití **fseek** nebo [_ftelli64](ftell-ftelli64.md) při použití **_fseeki64**.

Také v textovém režimu je ctrl+z interpretován jako znak konce souboru na vstupu. V souborech otevřených pro čtení / zápis, [fopen](fopen-wfopen.md) a všechny související rutiny zkontrolujte CTRL + Z na konci souboru a odstranit, pokud je to možné. Důvodem je použití kombinace **fseek** a [ftell](ftell-ftelli64.md) nebo **_fseeki64** a [_ftelli64](ftell-ftelli64.md), chcete-li přesunout v rámci souboru, který končí CTRL + Z může způsobit **fseek** nebo **_fseeki64** chovat nesprávně blízko konce souboru.

Když CRT otevře soubor, který začíná znakem objednávky bajtů (BOM), ukazatel souboru je umístěn za kusovníkem (to znamená na začátku skutečného obsahu souboru). Pokud máte **fseek** na začátek souboru, použijte [ftell](ftell-ftelli64.md) získat počáteční pozici a **fseek** na něj spíše než na pozici 0.

Tato funkce uzamkne další vlákna během provádění a je proto bezpečná pro přístup z více vláken. O verzi bez zamykání viz [_fseek_nolock _fseeki64_nolock](fseek-nolock-fseeki64-nolock.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fseek**|\<stdio.h>|
|**_fseeki64**|\<stdio.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

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

[I/O proudu](../../c-runtime-library/stream-i-o.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[ftell, _ftelli64](ftell-ftelli64.md)<br/>
[_lseek, _lseeki64](lseek-lseeki64.md)<br/>
[rewind](rewind.md)<br/>
