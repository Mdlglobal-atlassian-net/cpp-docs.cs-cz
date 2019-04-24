---
title: ftell, _ftelli64
ms.date: 11/04/2016
apiname:
- _ftelli64
- ftell
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
- _ftelli64
- ftell
helpviewer_keywords:
- ftell function
- ftelli64 function
- _ftelli64 function
- file pointers [C++], getting current position
- file pointers [C++]
ms.assetid: 40149cd8-65f2-42ff-b70c-68e3e918cdd7
ms.openlocfilehash: cc76ad0776ae82637b95d32cdc6254d3c40da5b5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62332780"
---
# <a name="ftell-ftelli64"></a>ftell, _ftelli64

Získá aktuální pozici ukazatele souboru.

## <a name="syntax"></a>Syntaxe

```C
long ftell(
   FILE *stream
);
__int64 _ftelli64(
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*stream*<br/>
Cíl **souboru** struktury.

## <a name="return-value"></a>Návratová hodnota

**ftell –** a **_ftelli64 –** vrátit aktuální pozici souboru. Hodnota vrácená **ftell –** a **_ftelli64 –** nemusí odrážet fyzické bajtovým posunem pro datové proudy otevřít v textovém režimu, protože režim textu způsobí, že překlad návratový znak odřádkování návrat na začátek řádku. Použití **ftell –** s [fseek](fseek-fseeki64.md) nebo **_ftelli64 –** s [_fseeki64 –](fseek-fseeki64.md) se vraťte do umístění souborů správně. Při chybě **ftell –** a **_ftelli64 –** vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, tyto funkce vrátí hodnotu-1 L a nastaví **errno** na jednu ze dvou konstant, definované v ERRNO. H. **EBADF** – Konstanta znamená, že *stream* argument není platný soubor hodnota ukazatele nebo neodkazuje na otevřený soubor. **EINVAL** znamená, že neplatný *stream* funkci byl předán argument. Na zařízeních nepodporující vyhledávání (například terminálech a tiskárnách) nebo když *datového proudu* neodkazuje na otevřený soubor, vrácená hodnota je definováno.

Zobrazit [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o těchto a dalších návratových kódů.

## <a name="remarks"></a>Poznámky

**Ftell –** a **_ftelli64 –** funkce načíst aktuální pozice ukazatel na soubor (pokud existuje) přidružené k *stream*. Pozice je vyjádřena jako posun vzhledem k začátku datového proudu.

Všimněte si, že pokud je soubor otevřen pro připojení dat, aktuální pozici souboru je určeno poslední vstupně-výstupní operace, ne, podle kterých by dojít k další zápis. Například pokud je soubor otevřen pro připojení a byl poslední operaci čtení, pozice v souboru je místo, kde další operaci čtení začne, kde další zápis nespustí. (Když je soubor otevřen pro přidávání, pozice v souboru přesunut na konec souboru před každou operací zápisu.) Pokud nemá žádné vstupně-výstupní operace, ale došlo k chybě na soubor otevřen pro přidávání, pozice v souboru je začátku souboru.

V textovém režimu je CTRL + Z interpretováno jako endovém souborovém znak na vstupu. V souborech otevřených pro čtení/zápis **fopen** a všechny související rutiny kontrolovat CTRL + Z na konci souboru a pokud je to možné ho odebrat. To se provádí, protože používá kombinaci **ftell –** a [fseek](fseek-fseeki64.md) nebo **_ftelli64 –** a [_fseeki64 –](fseek-fseeki64.md), pro přesun v rámci souboru, který končí CTRL + Z může způsobit, že **ftell –** nebo **_ftelli64 –** nesprávné chování na konci souboru.

Tato funkce uzamkne volající vlákno během spuštění a proto je bezpečná pro vlákno. Nezamykací verzi naleznete v tématu **_ftell_nolock –**.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|Volitelná záhlaví|
|--------------|---------------------|----------------------|
|**ftell –**|\<stdio.h>|\<errno.h>|
|**_ftelli64**|\<stdio.h>|\<errno.h>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_ftell.c
// This program opens a file named CRT_FTELL.C
// for reading and tries to read 100 characters. It
// then uses ftell to determine the position of the
// file pointer and displays this position.

#include <stdio.h>

FILE *stream;

int main( void )
{
   long position;
   char list[100];
   if( fopen_s( &stream, "crt_ftell.c", "rb" ) == 0 )
   {
      // Move the pointer by reading data:
      fread( list, sizeof( char ), 100, stream );
      // Get position after read:
      position = ftell( stream );
      printf( "Position after trying to read 100 bytes: %ld\n",
              position );
      fclose( stream );
   }
}
```

```Output
Position after trying to read 100 bytes: 100
```

## <a name="see-also"></a>Viz také:

[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[fgetpos](fgetpos.md)<br/>
[fseek, _fseeki64](fseek-fseeki64.md)<br/>
[_lseek, _lseeki64](lseek-lseeki64.md)<br/>
