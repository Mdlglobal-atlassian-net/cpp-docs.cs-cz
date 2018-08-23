---
title: fseek, _fseeki64 – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
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
- api-ms-win-crt-stdio-l1-1-0.dll
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 01c0eee248090f6bffad6f68b34d59f1a6fa7265
ms.sourcegitcommit: e9ce38decc9f986edab5543de3464b11ebccb123
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2018
ms.locfileid: "42466023"
---
# <a name="fseek-fseeki64"></a>fseek, _fseeki64

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
Ukazatel na **souboru** struktury.

*Posun*<br/>
Počet bajtů z *původu*.

*Počátek*<br/>
Počáteční pozice.

## <a name="return-value"></a>Návratová hodnota

V případě úspěšného ověření **fseek** a **_fseeki64 –** vrátí hodnotu 0. V opačném případě vrací nenulovou hodnotu. Na zařízeních nepodporující vyhledávání návratová hodnota není definována. Pokud *stream* je ukazatel s hodnotou null, nebo pokud *původu* není jedním z povolených hodnot je popsáno níže, **fseek** a **_fseeki64 –** vyvolat neplatné Obslužná rutina parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, tyto funkce nastaví **errno** k **EINVAL** a vrátí hodnotu -1.

## <a name="remarks"></a>Poznámky

**Fseek** a **_fseeki64 –** funkce přesune ukazatel na soubor (pokud existuje) přidružené k *stream* do nového umístění, která je *posun* bajty z *původu*. Další operace v datovém proudu se provádí v novém umístění. Na datový proud otevřen pro úpravy může být další operace čtení nebo zápis. Argument *původu* musí být jedna z následujících konstant, definované v STDIO. V:

|původní hodnota|Význam|
|-|-|
**SEEK_CUR**|Aktuální pozici ukazatele na soubor.
**SEEK_END**|Konec souboru.
**SEEK_SET**|Začátku souboru.

Můžete použít **fseek** a **_fseeki64 –** přesuňte ukazatel myši kdekoli v souboru. Ukazatel může také být umístěné za koncem souboru. **fseek** a **_fseeki64 –** vymaže indikátor konce souboru a Neguje působení jakékoli předchozí [ungetc –](ungetc-ungetwc.md) volá proti *stream*.

Když je soubor otevřen pro připojení dat, aktuální pozice v souboru je určen poslední vstupně-výstupní operace, nikoli kde by tomu bylo další zápis. Pokud nemá žádné vstupně-výstupní operace, ale došlo k chybě na soubor otevřen pro přidávání, pozice v souboru je začátku souboru.

Pro datové proudy otevřít v textovém režimu **fseek** a **_fseeki64 –** mají omezenou použití, protože může způsobit návrat na začátek řádku návratový znak odřádkování překlady **fseek** a **_ fseeki64 –** k vést k neočekávaným výsledkům. Jediná **fseek** a **_fseeki64 –** operace zaručeno, že fungují u streamů otevřít v textovém režimu jsou:

- Hledání s posunem 0 vzhledem k některé z původní hodnoty.

- Hledání od začátku souboru s hodnoty posunu vrácená z volání [ftell –](ftell-ftelli64.md) při použití **fseek** nebo [_ftelli64 –](ftell-ftelli64.md) při použití **_fseeki64 –**.

Také v textovém režimu je CTRL + Z interpretováno jako endovém souborovém znak na vstupu. V souborech otevřených pro čtení/zápis [fopen](fopen-wfopen.md) a všechny související rutiny kontrolovat CTRL + Z na konci souboru a pokud je to možné ho odebrat. To se provádí, protože používá kombinaci **fseek** a [ftell –](ftell-ftelli64.md) nebo **_fseeki64 –** a [_ftelli64 –](ftell-ftelli64.md), pro přesun v rámci souboru, který končí CTRL + Z může způsobit, že **fseek** nebo **_fseeki64 –** nesprávné chování na konci souboru.

Když CRT otevře soubor, který začíná s značky pořadí bajtů (BOM), ukazatel na soubor je umístěn za BOM (to znamená, že na začátku souboru skutečný obsah). Pokud budete muset **fseek** na začátek souboru, použijte [ftell –](ftell-ftelli64.md) získat počáteční pozice a **fseek** k němu, nikoli na pozici 0.

Tato funkce zamezí ostatní vlákna během provádění a proto je bezpečná pro vlákno. Nezamykací verzi naleznete v tématu [_fseek_nolock – _fseeki64_nolock –](fseek-nolock-fseeki64-nolock.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fseek**|\<stdio.h>|
|**_fseeki64**|\<stdio.h>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také:

[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[ftell, _ftelli64](ftell-ftelli64.md)<br/>
[_lseek, _lseeki64](lseek-lseeki64.md)<br/>
[rewind](rewind.md)<br/>
