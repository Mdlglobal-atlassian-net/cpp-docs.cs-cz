---
title: "_eof – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _eof
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
f1_keywords: _eof
dev_langs: C++
helpviewer_keywords:
- eof function
- end of file, testing for
- _eof function
- files [C++], end of
- testing, for end-of-file
- end of file
ms.assetid: 265703f4-d07e-4005-abf3-b1d0cdd9e0b0
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2a81e289f5496393966109cd7b3940e55918cb29
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="eof"></a>_eof
Testy pro konec souboru (EOF).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _eof(   
   int fd   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fd`  
 Popisovače souborů na otevření souboru.  
  
## <a name="return-value"></a>Návratová hodnota  
 `_eof`Pokud aktuální pozice konce souboru, nebo 0, pokud není, vrátí hodnotu 1. Vrácená hodnota -1 označuje chybu; v takovém případě je volána obslužná rutina neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění `errno` je nastaven na `EBADF`, což naznačuje popisovač souboru je neplatný.  
  
## <a name="remarks"></a>Poznámky  
 `_eof` Funkce určuje, zda konec souboru přidružené `fd` byl dosažen.  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|  
|--------------|---------------------|---------------------|  
|`_eof`|\<IO.h >|\<errno.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_eof.c  
// This program reads data from a file  
// ten bytes at a time until the end of the  
// file is reached or an error is encountered.  
//  
#include <io.h>  
#include <fcntl.h>  
#include <stdio.h>  
#include <stdlib.h>  
#include <share.h>  
  
int main( void )  
{  
   int  fh, count, total = 0;  
   char buf[10];  
   if( _sopen_s( &fh, "crt_eof.txt", _O_RDONLY, _SH_DENYNO, 0 ) )  
   {  
        perror( "Open failed");  
        exit( 1 );  
   }  
   // Cycle until end of file reached:   
   while( !_eof( fh ) )  
   {  
      // Attempt to read in 10 bytes:   
      if( (count = _read( fh, buf, 10 )) == -1 )  
      {  
         perror( "Read error" );  
         break;  
      }  
      // Total actual bytes read   
      total += count;  
   }  
   printf( "Number of bytes read = %d\n", total );  
   _close( fh );  
}  
```  
  
## <a name="input-crteoftxt"></a>Vstup: crt_eof.txt  
  
```  
This file contains some text.  
```  
  
### <a name="output"></a>Výstup  
  
```  
Number of bytes read = 29  
```  
  
## <a name="see-also"></a>Viz také  
 [Zpracování chyb](../../c-runtime-library/error-handling-crt.md)   
 [I/O nízké úrovně](../../c-runtime-library/low-level-i-o.md)   
 [clearerr –](../../c-runtime-library/reference/clearerr.md)   
 [feof –](../../c-runtime-library/reference/feof.md)   
 [ferror –](../../c-runtime-library/reference/ferror.md)   
 [perror, _wperror –](../../c-runtime-library/reference/perror-wperror.md)