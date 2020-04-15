---
title: ftell, _ftelli64
ms.date: 4/2/2020
api_name:
- _ftelli64
- ftell
- _o__ftelli64
- _o_ftell
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
- _ftelli64
- ftell
helpviewer_keywords:
- ftell function
- ftelli64 function
- _ftelli64 function
- file pointers [C++], getting current position
- file pointers [C++]
ms.assetid: 40149cd8-65f2-42ff-b70c-68e3e918cdd7
ms.openlocfilehash: bfe79610161a7f4032517d9f7eaa0de50be18e50
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345616"
---
# <a name="ftell-_ftelli64"></a>ftell, _ftelli64

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

*Proudu*<br/>
Cílová struktura **SOUBORŮ.**

## <a name="return-value"></a>Návratová hodnota

**ftell** a **_ftelli64** vrátí aktuální pozici souboru. Hodnota vrácená **ftell** a **_ftelli64** nemusí odrážet posun fyzického bajtu pro datové proudy otevřené v textovém režimu, protože režim textu způsobuje překlad datového kanálu řádku řádku řádku. Pomocí **ftellu** s [fseek](fseek-fseeki64.md) nebo **_ftelli64** s [_fseeki64](fseek-fseeki64.md) se správně vraťte do umístění souborů. Při chybě **ftell** a **_ftelli64** vyvolat neplatnou obslužnou rutinu parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, tyto funkce vrátí -1L a nastavit **errno** na jednu ze dvou konstant, definované v ERRNO. H. Konstanta **EBADF** znamená, že argument *datového proudu* není platnou hodnotou ukazatele souboru nebo neodkazuje na otevřený soubor. **EINVAL** znamená, že neplatný argument *datového proudu* byl předán funkci. Na zařízeních, která nelze hledat (například terminály a tiskárny), nebo pokud *datový proud* neodkazuje na otevřený soubor, vrácená hodnota není definována.

Další informace o těchto a dalších návratových kódech naleznete v [_doserrno, errno, _sys_errlist a _sys_nerr.](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)

## <a name="remarks"></a>Poznámky

Funkce **ftell** a **_ftelli64** načítají aktuální polohu ukazatele souboru (pokud existuje) přidruženého k *datovému proudu*. Pozice je vyjádřena jako posun vzhledem k začátku datového proudu.

Všimněte si, že při otevření souboru pro připojení dat je aktuální pozice souboru určena poslední vstupně-va, nikoli podle místa, kde by došlo k dalšímu zápisu. Například pokud je soubor otevřen pro přílohu a poslední operace byla přečtena, pozice souboru je bod, kde by se spustila další operace čtení, nikoli kde by se spustil další zápis. (Při otevření souboru pro připojení je pozice souboru přesunuta na konec souboru před jakoukoli operací zápisu.) Pokud u souboru otevřeného pro připojení ještě nedošlo k žádné operaci vstupně-in, je pozice souboru začátkem souboru.

V textovém režimu je ctrl+z interpretován jako znak konce souboru na vstupu. V souborech otevřených pro čtení / zápis, **fopen** a všechny související rutiny zkontrolujte CTRL + Z na konci souboru a odstranit, pokud je to možné. Důvodem je použití kombinace **ftell** a [fseek](fseek-fseeki64.md) nebo **_ftelli64** a [_fseeki64](fseek-fseeki64.md), chcete-li přesunout v rámci souboru, který končí CTRL + Z může způsobit **ftell** nebo **_ftelli64** chovat nesprávně blízko konce souboru.

Tato funkce uzamkne volající vlákno během provádění a je proto bezpečná pro přístup z více vláken. O verzi bez zamykání viz **_ftell_nolock**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|Volitelná záhlaví|
|--------------|---------------------|----------------------|
|**ftell**|\<stdio.h>|\<errno.h>|
|**_ftelli64**|\<stdio.h>|\<errno.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také

[I/O proudu](../../c-runtime-library/stream-i-o.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[fgetpos](fgetpos.md)<br/>
[fseek, _fseeki64](fseek-fseeki64.md)<br/>
[_lseek, _lseeki64](lseek-lseeki64.md)<br/>
