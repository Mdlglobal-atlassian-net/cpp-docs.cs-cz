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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: c9bfc9a575504d890d0021937713c720c4557441
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910194"
---
# <a name="fseek-_fseeki64"></a>fseek, _fseeki64

Přesune ukazatel na soubor do zadaného umístění.

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

*Stream*<br/>
Ukazatel na strukturu **souborů** .

*polohy*<br/>
Počet bajtů od *počátku*

*zdroji*<br/>
Počáteční pozice.

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu **fseek** a **_fseeki64** vrátí hodnotu 0. V opačném případě vrátí nenulovou hodnotu. U zařízení, která neumožňují hledání, není tato návratová hodnota definována. Pokud je *datový proud* ukazatel s hodnotou null, nebo pokud není *zdrojem* jedna z povolených hodnot uvedených níže, **fseek** a **_fseeki64** vyvolat neplatnou obslužnou rutinu parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tyto funkce nastaví **errno** na **EINVAL** a vrátí-1.

## <a name="remarks"></a>Poznámky

Funkce **fseek** a **_fseeki64** přesune ukazatel na soubor (pokud existuje) přidružený ke *streamu* do nového umístění, které má *posun* bajtů od *počátku*. Další operace s datovým proudem probíhá na novém místě. U datového proudu otevřeného pro aktualizaci může být další operace buď čtení, nebo zápis. *Počátek* argumentu musí být jedna z následujících konstant definovaná v stdio. Y

|hodnota počátku|Význam|
|-|-|
| **SEEK_CUR** | Aktuální pozice ukazatele na soubor |
| **SEEK_END** | Konec souboru |
| **SEEK_SET** | Začátek souboru. |

Můžete použít **fseek** a **_fseeki64** k přemístění ukazatele kdekoli v souboru. Ukazatel lze také umístit za konec souboru. **fseek** a **_fseeki64** vymaže indikátor konce souboru a negace efektu všech předchozích volání [ungetc –](ungetc-ungetwc.md) proti *streamu*.

Když se pro připojená data otevře soubor, určí se aktuální pozice souboru podle poslední vstupně-výstupní operace, ne podle toho, kde by se mohlo objevit další zápis. Pokud v souboru otevřeném pro připojení ještě nedošlo k žádné vstupně-výstupní operaci, je pozice souboru na začátku souboru.

Pro datové proudy otevřené v textovém režimu **fseek** a **_fseeki64** mají omezené použití, protože překlady kanálu návratového řádku můžou způsobit **fseek** a **_fseeki64** způsobit neočekávané výsledky. Pro práci s datovými proudy otevřenými v textovém režimu jsou zaručené jenom operace **fseek** a **_fseeki64** :

- Hledání s posunem 0 relativně k libovolnému z původních hodnot.

- Hledání od začátku souboru s hodnotou posunu vrácenou z volání [ftell](ftell-ftelli64.md) při použití **fseek** nebo [_ftelli64](ftell-ftelli64.md) při použití **_fseeki64**.

V textovém režimu je také kombinace kláves CTRL + Z interpretována jako znak konce souboru na vstupu. V souborech otevřených pro čtení/zápis [fopen](fopen-wfopen.md) a všechny související rutiny kontrolují CTRL + Z na konci souboru a pokud je to možné, odeberte je. K tomu dochází, protože použití kombinace **fseek** a [ftell](ftell-ftelli64.md) nebo **_fseeki64** a [_ftelli64](ftell-ftelli64.md), aby se přesunuly v souboru, který končí kombinací kláves CTRL + Z, může způsobit, že se **fseek** nebo **_fseeki64** na konci souboru chová nesprávně.

Když CRT otevře soubor, který začíná znakem pořadí bajtů (BOM), ukazatel na soubor se umístí po kusovníku (tj. na začátku aktuálního obsahu souboru). Pokud je třeba **fseek** na začátek souboru, použijte [ftell](ftell-ftelli64.md) k získání počáteční pozice a **fseek** místo pozice 0.

Tato funkce zamkne další vlákna během provádění a je proto bezpečná pro přístup z více vláken. Neuzamykání verze naleznete v tématu [_fseek_nolock _fseeki64_nolock](fseek-nolock-fseeki64-nolock.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fseek**|\<stdio. h>|
|**_fseeki64**|\<stdio. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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
