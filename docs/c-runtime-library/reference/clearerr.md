---
title: "clearerr – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: clearerr
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
f1_keywords: clearerr
dev_langs: C++
helpviewer_keywords:
- error indicator for streams
- resetting stream error indicator
- clearerr function
ms.assetid: a9711cd4-3335-43d4-a018-87bbac5b3bac
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e1c9c815307c8a454456c76fee419f1c048fded1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="clearerr"></a>clearerr
Obnoví označení chyb pro datový proud. Bezpečnější verze této funkce je k dispozici. v tématu [clearerr_s –](../../c-runtime-library/reference/clearerr-s.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void clearerr(  
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `stream`  
 Ukazatel na `FILE` struktura.  
  
## <a name="remarks"></a>Poznámky  
 `clearerr` Funkce resetuje označení chyb a end souborového indikátor pro `stream`. Chyba indikátory nejsou vymazána automaticky; Po nastavení označení chyb pro zadaného datového proudu nadále vrátí hodnotu chyby, dokud operace u tohoto datového proudu `clearerr`, `fseek`, `fsetpos`, nebo `rewind` je volána.  
  
 Pokud `stream` je `NULL`, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, tato funkce nastaví `errno` k `EINVAL` a vrátí. Další informace o `errno` a kódy chyb, najdete v části [errno – konstanty](../../c-runtime-library/errno-constants.md).  
  
 Bezpečnější verze této funkce je k dispozici. v tématu [clearerr_s –](../../c-runtime-library/reference/clearerr-s.md).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`clearerr`|\<stdio.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_clearerr.c  
// This program creates an error  
// on the standard input stream, then clears  
// it so that future reads won't fail.  
  
#include <stdio.h>  
  
int main( void )  
{  
   int c;  
   // Create an error by writing to standard input.  
   putc( 'c', stdin );  
   if( ferror( stdin ) )  
   {  
      perror( "Write error" );  
      clearerr( stdin );  
   }  
  
   // See if read causes an error.  
   printf( "Will input cause an error? " );  
   c = getc( stdin );  
   if( ferror( stdin ) )  
   {  
      perror( "Read error" );  
      clearerr( stdin );  
   }  
   else  
      printf( "No read error\n" );  
}  
```  
  
```Output  
  
n  
  
```  
  
```Output  
  
      nWrite error: No error  
Will input cause an error? n  
No read error  
```  
  
## <a name="see-also"></a>Viz také  
 [Zpracování chyb](../../c-runtime-library/error-handling-crt.md)   
 [Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)   
 [_eof –](../../c-runtime-library/reference/eof.md)   
 [feof –](../../c-runtime-library/reference/feof.md)   
 [ferror –](../../c-runtime-library/reference/ferror.md)   
 [perror, _wperror –](../../c-runtime-library/reference/perror-wperror.md)