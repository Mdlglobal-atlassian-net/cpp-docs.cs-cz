---
title: _dup, _dup2
ms.date: 11/04/2016
api_name:
- _dup
- _dup2
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
ms.openlocfilehash: da47d6f040b62906d30107f9036ffa2a3ea05a1c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70937791"
---
# <a name="_dup-_dup2"></a>_dup, _dup2

Vytvoří druhý popisovač souboru pro otevřený soubor ( **_dup**) nebo znovu přiřadí popisovač souboru ( **_dup2**).

## <a name="syntax"></a>Syntaxe

```C
int _dup( int fd );
int _dup2( int fd1, int fd2 );
```

### <a name="parameters"></a>Parametry

*fd*, *fd1*<br/>
Popisovače souborů odkazující na otevřený soubor.

*fd2*<br/>
Jakýkoli popisovač souboru.

## <a name="return-value"></a>Návratová hodnota

**_dup** vrací nový popisovač souboru. **_dup2** vrátí 0 pro indikaci úspěchu. Pokud dojde k chybě, každá funkce vrátí hodnotu-1 a nastaví **errno** na **EBADF** , pokud je popisovač souboru neplatný nebo **EMFILE** , pokud nejsou k dispozici žádné další popisovače souboru. V případě neplatného popisovače souboru funkce také vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md).

Další informace o těchto a dalších návratových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **_dup** a **_dup2** přiřadí druhý popisovač souboru s aktuálně otevřeným souborem. Tyto funkce lze použít k přidružení předdefinovaného popisovače souboru, například pro **stdout**, s jiným souborem. Operace se souborem lze provádět pomocí popisovače souboru. Typ přístupu povolený pro soubor není ovlivněn vytvořením nového deskriptoru. **_dup** vrací další dostupný popisovač souboru pro daný soubor. **_dup2** vynutí, aby *fd2* odkazovaly na stejný soubor jako *FD1*. Pokud je *fd2* přidružen k otevřenému souboru v době volání, je tento soubor uzavřen.

**_Dup** i **_dup2** přijímají popisovače souboru jako parametry. Chcete-li předat datový`FILE *`proud () některé z těchto funkcí, použijte [_fileno](fileno.md). Rutina **fileno** vrátí popisovač souboru, který je aktuálně přidružený k danému datovému proudu. Následující příklad ukazuje, jak přidružit **stderr** (definované jako `FILE *` v stdio. h) s popisovačem souboru:

```C
int cstderr = _dup( _fileno( stderr ));
```

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_dup**|\<io.h>|
|**_dup2**|\<io.h>|

Konzola není v aplikacích Univerzální platforma Windows (UWP) podporována. Standardní popisovače streamů, které jsou spojeny s konzolou, **stdin**, **stdout**a **stderr**, musí být přesměrované před tím, než je funkce modulu runtime jazyka C můžou použít v aplikacích pro UWP. Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také:

[I/O nízké úrovně](../../c-runtime-library/low-level-i-o.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
