---
title: "_dup –, _dup2 – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
helpviewer_keywords:
- _dup2 function
- dup function
- file handles [C++], duplicating
- file handles [C++], reassigning
- dup2 function
- _dup function
ms.assetid: 4d07e92c-0d76-4832-a770-dfec0e7a0cfa
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f267ebf6526ed46cf3ef5670c6aeeb93a5a075e4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="dup-dup2"></a>_dup, _dup2
Vytvoří druhý popisovače souborů, pro otevření souboru (`_dup`), nebo pouze Změna přiřazení popisovače souborů (`_dup2`).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _dup(   
   int fd   
);  
int _dup2(   
   int fd1,  
   int fd2   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fd`, `fd1`  
 Soubor popisovače odkazující na soubor otevřít.  
  
 `fd2`  
 Všechny popisovače souborů.  
  
## <a name="return-value"></a>Návratová hodnota  
 `_dup`vrátí nový popisovač souboru. `_dup2`Vrátí hodnotu 0, čímž indikuje úspěšné provedení. Pokud dojde k chybě, každý funkce vrátí hodnotu -1 a nastaví `errno` k `EBADF` Pokud popisovače souborů je neplatný nebo k `EMFILE` Pokud jsou k dispozici žádné další popisovače souborů. V případě popisovač souboru je neplatný. funkce také vyvolá obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md).  
  
 Další informace o těchto a dalších návratové kódy najdete v tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Poznámky  
 `_dup` a `_dup2` funkce přidružit aktuálně otevřených souborů druhý popisovače souborů. Tyto funkce lze použít k přiřazení popisovač předdefinovaného souboru, jako je například `stdout`, s jiný soubor. Operace na souboru se dá provést pomocí buď popisovače souborů. Typ přístupová oprávnění k souboru je vytvoření nový popisovač nemá vliv. `_dup`Vrátí popisovač další soubor k dispozici pro daný soubor. `_dup2`Vynutí `fd2` k odkazování na stejném souboru jako `fd1`. Pokud `fd2` souvisí s otevřete soubor v době volání, že soubor zavřený.  
  
 Obě `_dup` a `_dup2` přijmout popisovače souborů jako parametry. Předávání datového proudu `(FILE *)` na jednu z těchto funkcí používat [_fileno –](../../c-runtime-library/reference/fileno.md). `fileno` Rutina vrátí popisovače souborů, které jsou aktuálně přidružen s daným datovým proudem. Následující příklad ukazuje, jak přidružit `stderr` (definován jako `FILE` `*` v Stdio.h) s popisovače souborů:  
  
```  
int cstderr = _dup( _fileno( stderr ));  
```  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_dup`|\<IO.h >|  
|`_dup2`|\<IO.h >|  
  
 Konzole není podporována v [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikace. Standardní datový proud obslužných rutin, které jsou spojeny s konzolou –`stdin`, `stdout`, a `stderr`– C běhové funkce je mohli používat, musí být přesměrována [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikace. Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_dup.c  
// This program uses the variable old to save  
// the original stdout. It then opens a new file named  
// DataFile and forces stdout to refer to it. Finally, it  
// restores stdout to its original state.  
//  
  
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
 [I/O nízké úrovně](../../c-runtime-library/low-level-i-o.md)   
 [_close –](../../c-runtime-library/reference/close.md)   
 [_creat –, _wcreat –](../../c-runtime-library/reference/creat-wcreat.md)   
 [_Otevřít _wopen –](../../c-runtime-library/reference/open-wopen.md)