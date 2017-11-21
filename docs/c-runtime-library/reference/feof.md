---
title: "feof – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: feof
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
f1_keywords: feof
dev_langs: C++
helpviewer_keywords:
- end of file, testing for
- feof function
ms.assetid: 09081eee-7c4b-4189-861f-2fad95d3ec6d
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f95ad5c1d0328d365346b51f9347d3559071d9e8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="feof"></a>feof
Testy pro koncové soubor na datový proud.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int feof(   
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `stream`  
 Ukazatel na `FILE` struktura.  
  
## <a name="return-value"></a>Návratová hodnota  
 `feof` Funkce vrátí nenulovou hodnotu, pokud při pokusu o čtení za koncem souboru má v operaci čtení; jinak vrátí 0. Pokud je ukazatel datového proudu `NULL`, funkce vyvolá obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění `errno` je nastaven na `EINVAL` a `feof` vrátí hodnotu 0.  
  
 V tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o těchto a dalších kódy chyb.  
  
## <a name="remarks"></a>Poznámky  
 `feof` Rutiny (implementována jako funkce i jako makra) určuje, zda konec `stream` byl předán. Když je předána na konci souboru, přečtěte si operace vracejí indikátor end souborového, dokud datový proud je uzavřen, nebo dokud `rewind`, `fsetpos`, `fseek`, nebo `clearerr` je volána před ním.  
  
 Pokud soubor obsahuje 10 bajtů a čtení 10 bajtů ze souboru, například `feof` vrátí 0, protože přestože ukazatele souboru je na konci souboru, nebyly pokus o čtení za konec. Pouze po pokusu o čtení 11 bajtů bude `feof` vrátí nenulovou hodnotu.  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Požadovaný hlavičkový soubor|  
|--------------|---------------------|  
|`feof`|\<stdio.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_feof.c  
// This program uses feof to indicate when  
// it reaches the end of the file CRT_FEOF.TXT. It also  
// checks for errors with ferror.  
//  
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   int  count, total = 0;  
   char buffer[100];  
   FILE *stream;  
  
   fopen_s( &stream, "crt_feof.txt", "r" );  
   if( stream == NULL )  
      exit( 1 );  
  
   // Cycle until end of file reached:  
   while( !feof( stream ) )  
   {  
      // Attempt to read in 100 bytes:  
      count = fread( buffer, sizeof( char ), 100, stream );  
      if( ferror( stream ) )      {  
         perror( "Read error" );  
         break;  
      }  
  
      // Total up actual bytes read  
      total += count;  
   }  
   printf( "Number of bytes read = %d\n", total );  
   fclose( stream );  
}  
```  
  
## <a name="input-crtfeoftxt"></a>Vstup: crt_feof.txt  
  
```  
Line one.  
Line two.  
```  
  
### <a name="output"></a>Výstup  
  
```  
Number of bytes read = 19  
```  
  
## <a name="see-also"></a>Viz také  
 [Zpracování chyb](../../c-runtime-library/error-handling-crt.md)   
 [Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)   
 [clearerr –](../../c-runtime-library/reference/clearerr.md)   
 [_eof –](../../c-runtime-library/reference/eof.md)   
 [ferror –](../../c-runtime-library/reference/ferror.md)   
 [perror, _wperror –](../../c-runtime-library/reference/perror-wperror.md)