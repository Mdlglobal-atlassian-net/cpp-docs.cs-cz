---
title: _dup, _dup2
ms.date: 4/2/2020
api_name:
- _dup
- _dup2
- _o__dup
- _o__dup2
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
- _dup2
- _dup
helpviewer_keywords:
- _dup2 function
- dup function
- file handles [C++], duplicating
- file handles [C++], reassigning
- dup2 function
- _dup function
ms.assetid: 4d07e92c-0d76-4832-a770-dfec0e7a0cfa
ms.openlocfilehash: 239f857bb40c9609cb6f7ff373295a7a1f8523a9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348117"
---
# <a name="_dup-_dup2"></a>_dup, _dup2

Vytvoří druhý popisovač souboru pro otevřený soubor (**_dup**) nebo znovu přiřadí popisovač souboru (**_dup2**).

## <a name="syntax"></a>Syntaxe

```C
int _dup( int fd );
int _dup2( int fd1, int fd2 );
```

### <a name="parameters"></a>Parametry

*fd*, *fd1*<br/>
Popisovače souborů odkazující na otevřený soubor.

*fd2*<br/>
Libovolný popisovač souboru.

## <a name="return-value"></a>Návratová hodnota

**_dup** vrátí nový popisovač souboru. **_dup2** vrátí hodnotu 0, což označuje úspěch. Pokud dojde k chybě, každá funkce vrátí -1 a nastaví **errno** na **EBADF,** pokud je popisovač souboru neplatný, nebo **na EMFILE,** pokud nejsou k dispozici žádné další popisovače souborů. V případě neplatného popisovače souboru funkce také vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v [části Ověření parametru](../../c-runtime-library/parameter-validation.md).

Další informace o těchto a dalších návratových kódech naleznete [v tématech _doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **_dup** a **_dup2** přidruží popisovač druhého souboru k aktuálně otevřenému souboru. Tyto funkce lze použít k přidružení předdefinovaného popisovače souboru, například popisovače **stdout**, k jinému souboru. Operace se souborem lze provádět pomocí obou popisovačů souborů. Typ přístupu povolený pro soubor není ovlivněn vytvořením nového popisovače. **_dup** vrátí další dostupný popisovač souboru pro daný soubor. **_dup2** *vynutí, aby fd2* odkazoval na stejný soubor jako *fd1*. Pokud *fd2* je přidružen a otevřený soubor v době volání, tento soubor je uzavřen.

**_dup** i **_dup2** přijímají popisovače souborů jako parametry. Chcete-li datový`FILE *`proud ( ) předat jedné z těchto funkcí, použijte [_fileno](fileno.md). Rutina **fileno** vrátí popisovač souboru, který je aktuálně přidružen k danému datovému proudu. Následující příklad ukazuje, jak přidružit `FILE *` **stderr** (definované jako v Stdio.h) s popisovačsouboru:

```C
int cstderr = _dup( _fileno( stderr ));
```

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_dup**|\<io.h>|
|**_dup2**|\<io.h>|

Konzola není podporována v aplikacích univerzální platformy Windows (UPW). Standardní popisovače datového proudu, které jsou přidruženy ke **konzole, stdin**, **stdout**a **stderr**, musí být přesměrovány před c run-time funkce je možné použít v aplikacích UPW. Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_dup.c
// This program uses the variable old to save
// the original stdout. It then opens a new file named
// DataFile and forces stdout to refer to it. Finally, it
// restores stdout to its original state.

#include <io.h>
#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   int old;
   FILE *DataFile;

   old = _dup( 1 );   // "old" now refers to "stdout"
                      // Note:  file descriptor 1 == "stdout"
   if( old == -1 )
   {
      perror( "_dup( 1 ) failure" );
      exit( 1 );
   }
   _write( old, "This goes to stdout first\n", 26 );
   if( fopen_s( &DataFile, "data", "w" ) != 0 )
   {
      puts( "Can't open file 'data'\n" );
      exit( 1 );
   }

   // stdout now refers to file "data"
   if( -1 == _dup2( _fileno( DataFile ), 1 ) )
   {
      perror( "Can't _dup2 stdout" );
      exit( 1 );
   }
   puts( "This goes to file 'data'\n" );

   // Flush stdout stream buffer so it goes to correct file
   fflush( stdout );
   fclose( DataFile );

   // Restore original stdout
   _dup2( old, 1 );
   puts( "This goes to stdout\n" );
   puts( "The file 'data' contains:" );
   _flushall();
   system( "type data" );
}
```

```Output
This goes to stdout first
This goes to stdout

The file 'data' contains:
This goes to file 'data'
```

## <a name="see-also"></a>Viz také

[Vstupně-nosné(v" nízké úrovně](../../c-runtime-library/low-level-i-o.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
