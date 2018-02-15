---
title: "fgetpos – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- fgetpos
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
- fgetpos
dev_langs:
- C++
helpviewer_keywords:
- fgetpos function
- streams, file position indicator
ms.assetid: bfa05c38-1135-418c-bda1-d41be51acb62
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3740fdc7924e12fc9eeb2de4ab108ad376c764da
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="fgetpos"></a>fgetpos
Získá datový proud pozice souboru indikátoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int fgetpos(   
   FILE *stream,  
   fpos_t *pos   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `stream`  
 Cílový datový proud.  
  
 `pos`  
 Označení pozice úložiště.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěšného `fgetpos` vrátí hodnotu 0. Při selhání, vrátí nenulovou hodnotu a nastaví `errno` na jednu z následujících manifest konstanty (definovanou v STDIO. H): `EBADF`, což znamená, že zadaný datový proud není platný soubor ukazatel nebo není dostupný, nebo `EINVAL`, to znamená `stream` hodnotu nebo hodnotu `pos` je neplatná, jako třeba když je buď ukazatele null. Pokud `stream` nebo `pos` je `NULL` ukazatele, funkce vyvolá obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md).  
  
## <a name="remarks"></a>Poznámky  
 `fgetpos` Funkce získá aktuální hodnotu `stream` označení pozice souboru a ukládá je v objektu, na kterou odkazuje argument `pos`. `fsetpos` Funkce můžete později použít informace uložené v `pos` resetovat `stream` argumentu ukazatel na pozici v době `fgetpos` byla volána. `pos` Hodnota je uložený ve formátu interní a je určena pro použití pouze systémem `fgetpos` a `fsetpos`.  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Požadovaný hlavičkový soubor|  
|--------------|---------------------|  
|`fgetpos`|\<stdio.h>|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_fgetpos.c  
// This program uses fgetpos and fsetpos to  
// return to a location in a file.  
  
#include <stdio.h>  
  
int main( void )  
{  
   FILE   *stream;  
   fpos_t pos;  
   char   buffer[20];  
  
   if( fopen_s( &stream, "crt_fgetpos.txt", "rb" ) ) {  
      perror( "Trouble opening file" );  
      return -1;  
   }  
  
   // Read some data and then save the position.   
   fread( buffer, sizeof( char ), 8, stream );  
   if( fgetpos( stream, &pos ) != 0 ) {  
      perror( "fgetpos error" );  
      return -1;  
   }  
  
   fread( buffer, sizeof( char ), 13, stream );  
   printf( "after fgetpos: %.13s\n", buffer );  
  
   // Restore to old position and read data   
   if( fsetpos( stream, &pos ) != 0 ) {  
      perror( "fsetpos error" );  
      return -1;  
   }  
  
   fread( buffer, sizeof( char ), 13, stream );  
   printf( "after fsetpos: %.13s\n", buffer );  
   fclose( stream );  
}  
```  
  
## <a name="input-crtfgetpostxt"></a>Vstup: crt_fgetpos.txt  
  
```  
fgetpos gets a stream's file-position indicator.  
```  
  
### <a name="output-crtfgetpostxt"></a>Výstup crt_fgetpos.txt  
  
```  
after fgetpos: gets a stream  
after fsetpos: gets a stream  
```  
  
## <a name="see-also"></a>Viz také  
 [Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)   
 [fsetpos](../../c-runtime-library/reference/fsetpos.md)