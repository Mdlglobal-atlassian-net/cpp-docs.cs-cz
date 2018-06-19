---
title: _dup –, _dup2 – | Microsoft Docs
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
ms.openlocfilehash: ad477dc09ce6c8bee2d69e479f8e1615639cb14d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32399800"
---
# <a name="dup-dup2"></a>_dup, _dup2

Vytvoří druhý popisovače souborů, pro otevření souboru (**_dup –**), nebo pouze Změna přiřazení popisovače souborů (**_dup2 –**).

## <a name="syntax"></a>Syntaxe

```C
int _dup( int fd );
int _dup2( int fd1, int fd2 );
```

### <a name="parameters"></a>Parametry

*FD*, *fd1*<br/>
Soubor popisovače odkazující na soubor otevřít.

*FD2:*<br/>
Všechny popisovače souborů.

## <a name="return-value"></a>Návratová hodnota

**_dup –** vrací nový popisovač souboru. **_dup2 –** vrátí hodnotu 0, čímž indikuje úspěšné provedení. Pokud dojde k chybě, každý funkce vrátí hodnotu -1 a nastaví **errno** k **ebadf –** Pokud popisovače souborů je neplatný nebo k **emfile –** Pokud jsou k dispozici žádné další popisovače souborů. V případě popisovač souboru je neplatný. funkce také vyvolá obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md).

Další informace o těchto a dalších návratové kódy najdete v tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**_Dup –** a **_dup2 –** funkce přidružit aktuálně otevřených souborů druhý popisovače souborů. Tyto funkce lze použít k přiřazení popisovač předdefinovaného souboru, jako je například **stdout**, s jiný soubor. Operace na souboru se dá provést pomocí buď popisovače souborů. Typ přístupová oprávnění k souboru je vytvoření nový popisovač nemá vliv. **_dup –** vrátí další popisovač souboru k dispozici pro daný soubor. **_dup2 –** vynutí *fd2* k odkazování na stejném souboru jako *fd1*. Pokud *fd2* souvisí s otevřete soubor v době volání, že soubor zavřený.

Obě **_dup –** a **_dup2 –** přijmout popisovače souborů jako parametry. Předávání datového proudu (**soubor \*** ) Chcete-li některé z těchto funkcí, použijte [_fileno –](fileno.md). **Fileno –** rutina vrátí popisovače souborů, které jsou aktuálně přidružen s daným datovým proudem. Následující příklad ukazuje, jak přidružit **stderr** (definován jako **soubor \***  v Stdio.h) s popisovače souborů:

```C
int cstderr = _dup( _fileno( stderr ));
```

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_dup –**|\<IO.h >|
|**_dup2**|\<IO.h >|

Konzole není podporována v aplikacích pro univerzální platformu Windows (UWP). Standardní datový proud obslužných rutin, které jsou spojeny s konzolou, **stdin –**, **stdout**, a **stderr**, musí být přesměrována C běhové funkce mohli používat v aplikacích pro UPW . Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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

[I/O nízké úrovně](../../c-runtime-library/low-level-i-o.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
