---
title: "fread – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: fread
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
f1_keywords: fread
dev_langs: C++
helpviewer_keywords:
- reading data [C++], from input streams
- fread function
- data [C++], reading from input stream
- streams [C++], reading data from
ms.assetid: 9a3c1538-93dd-455e-ae48-77c1e23c53f0
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a3ca6ea76bf710db5e7d758963039e7c65f31fbe
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fread"></a>fread
Čte data z datového proudu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
size_t fread(   
   void *buffer,  
   size_t size,  
   size_t count,  
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `buffer`  
 Umístění úložiště pro data.  
  
 `size`  
 Položka velikost v bajtech.  
  
 `count`  
 Maximální počet položek ke čtení.  
  
 `stream`  
 Ukazatel na `FILE` struktura.  
  
## <a name="return-value"></a>Návratová hodnota  
 `fread`Vrátí počet položek úplné ve skutečnosti čtení, které můžou být menší než `count` Pokud dojde k chybě, nebo pokud je nalezen konec souboru dříve, než dorazila `count`. Použití `feof` nebo `ferror` funkce k rozlišení chybu čtení z podmínku end souboru. Pokud `size` nebo `count` 0, `fread` vrátí 0 a obsah vyrovnávací paměti jsou stejné. Pokud `stream` nebo `buffer` je ukazatel s hodnotou null, `fread` volá obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, tato funkce nastaví `errno` k `EINVAL` a vrátí hodnotu 0.  
  
 V tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o těchto a dalších kódy chyb.  
  
## <a name="remarks"></a>Poznámky  
 `fread` Funkce přečte až `count` položky `size` bajtů ze vstupu `stream` a ukládá je v `buffer`. Ukazatele souboru přidružené `stream` (pokud existuje) je zvýšit počet bajtů ve skutečnosti číst. S daným datovým proudem se při otevření v textovém režimu, páry vrátit-konce řádku znaků CR jsou nahrazeny znaky konce řádku jeden. Pokud chcete nahrazení nemá žádný vliv na ukazatele souboru nebo návratovou hodnotu. Pozice ukazatele souboru je neurčitou, pokud dojde k chybě. Hodnota částečně čtení položky nelze určit.  
  
 Tato funkce zamezí jiná vlákna. Pokud potřebujete bez uzamčení verzi, použijte `_fread_nolock`.  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Požadovaný hlavičkový soubor|  
|--------------|---------------------|  
|`fread`|\<stdio.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_fread.c  
// This program opens a file named FREAD.OUT and  
// writes 25 characters to the file. It then tries to open  
// FREAD.OUT and read in 25 characters. If the attempt succeeds,  
// the program displays the number of actual items read.  
  
#include <stdio.h>  
  
int main( void )  
{  
   FILE *stream;  
   char list[30];  
   int  i, numread, numwritten;  
  
   // Open file in text mode:  
   if( fopen_s( &stream, "fread.out", "w+t" ) == 0 )  
   {  
      for ( i = 0; i < 25; i++ )  
         list[i] = (char)('z' - i);  
      // Write 25 characters to stream   
      numwritten = fwrite( list, sizeof( char ), 25, stream );  
      printf( "Wrote %d items\n", numwritten );  
      fclose( stream );  
  
   }  
   else  
      printf( "Problem opening the file\n" );  
  
   if( fopen_s( &stream, "fread.out", "r+t" ) == 0 )  
   {  
      // Attempt to read in 25 characters   
      numread = fread( list, sizeof( char ), 25, stream );  
      printf( "Number of items read = %d\n", numread );  
      printf( "Contents of buffer = %.25s\n", list );  
      fclose( stream );  
   }  
   else  
      printf( "File could not be opened\n" );  
}  
```  
  
```Output  
Wrote 25 items  
Number of items read = 25  
Contents of buffer = zyxwvutsrqponmlkjihgfedcb  
```  
  
## <a name="see-also"></a>Viz také  
 [Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)   
 [fwrite –](../../c-runtime-library/reference/fwrite.md)   
 [_Zobrazit](../../c-runtime-library/reference/read.md)