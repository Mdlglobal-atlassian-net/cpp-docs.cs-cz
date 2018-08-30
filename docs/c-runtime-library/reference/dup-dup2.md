---
title: _dup – _dup2 – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _dup
- _dup2
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
- _dup2
- _dup
dev_langs:
- C++
helpviewer_keywords:
- _dup2 function
- dup function
- file handles [C++], duplicating
- file handles [C++], reassigning
- dup2 function
- _dup function
ms.assetid: 4d07e92c-0d76-4832-a770-dfec0e7a0cfa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 820172e1e6ab4ad007c89b2b40f03512134f0f0d
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43215950"
---
# <a name="dup-dup2"></a>_dup, _dup2

Vytvoří druhý popisovač souboru pro otevření souboru (**_dup –**), nebo znovu přiřadí popisovač souboru (**_dup2 –**).

## <a name="syntax"></a>Syntaxe

```C
int _dup( int fd );
int _dup2( int fd1, int fd2 );
```

### <a name="parameters"></a>Parametry

*FD*, *fd1*<br/>
Popisovače souboru odkazující na otevření souboru.

*FD2*<br/>
Všechny popisovače souboru.

## <a name="return-value"></a>Návratová hodnota

**_dup –** vrátí nový popisovač souboru. **_dup2 –** vrátí hodnotu 0 označující úspěšné provedení. Pokud dojde k chybě, každá funkce vrátí hodnotu -1 a nastaví **errno** k **EBADF** Pokud popisovač souboru je neplatný nebo **EMFILE** Pokud nejsou k dispozici žádné další popisovače souboru. V případě neplatného popisovače souboru, funkce také vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md).

Další informace o těchto a dalších návratových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**_Dup –** a **_dup2 –** přidružují druhý popisovač souboru s aktuálně otevřený soubor. Tyto funkce slouží k přidružení předdefinovaného popisovače souboru, jako je například **stdout**, s použitím jiného souboru. Operace se souborem lze provádět pomocí libovolného popisovače souboru. Typ přístupu povolený pro soubor není ovlivněn vytvořením nového popisovače. **_dup –** vrátí další popisovače souborů pro daný soubor. **_dup2 –** vynutí *fd2* k odkazování na stejném souboru jako *fd1*. Pokud *fd2* je spojen s otevřeným souborem v okamžiku volání, daný soubor je zavřen.

Obě **_dup –** a **_dup2 –** přijímají popisovače souborů jako parametry. Chcete-li předat proud (`FILE *`) Chcete-li některé z těchto funkcí, použijte [_fileno](fileno.md). **Fileno –** rutina vrátí popisovač souboru, který je aktuálně přiřazen k daným datovým proudem. Následující příklad ukazuje, jak přidružit **stderr** (definované jako `FILE *` v souboru Stdio.h) s popisovačem souboru:

```C
int cstderr = _dup( _fileno( stderr ));
```

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_dup –**|\<IO.h >|
|**_dup2**|\<IO.h >|

Konzole není podporována v aplikacích pro univerzální platformu Windows (UPW). Standardní datový proud popisovačů, které jsou spojeny s konzolou, **stdin**, **stdout**, a **stderr**, musí být přesměrován před funkcí jazyka C za běhu můžete použít v aplikacích pro UWP . Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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
