---
title: fread_s | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: fread_s
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
- fread_s
- stdio/fread_s
dev_langs: C++
ms.assetid: ce735de0-f005-435d-a8f2-6f4b80ac775e
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d77f0f7eb0c9eabf8626a920e04534c79048bd90
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="freads"></a>fread_s
Čte data z datového proudu. Tato verze [fread –](../../c-runtime-library/reference/fread.md) má rozšířené zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
size_t fread_s(   
   void *buffer,  
   size_t bufferSize,  
   size_t elementSize,  
   size_t count,  
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `buffer`  
 Umístění úložiště pro data.  
  
 `bufferSize`  
 Velikost cílové vyrovnávací paměti v bajtech.  
  
 `elementSize`  
 Velikost položky ke čtení v bajtech.  
  
 `count`  
 Maximální počet položek ke čtení.  
  
 `stream`  
 Ukazatel na `FILE` struktura.  
  
## <a name="return-value"></a>Návratová hodnota  
 `fread_s`Vrátí počet (celé) položky, které byly čtení do vyrovnávací paměti, který může být menší než `count` Pokud je zaznamenána chyba čtení nebo konec souboru před `count` je dosaženo. Použití `feof` nebo `ferror` funkce k rozlišení chybu z podmínku end souboru. Pokud `size` nebo `count` 0, `fread_s` vrátí 0 a obsah vyrovnávací paměti jsou stejné. Pokud `stream` nebo `buffer` je ukazatel s hodnotou null, `fread_s` volá obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, tato funkce nastaví `errno` k `EINVAL` a vrátí hodnotu 0.  
  
 Další informace o chybových kódech najdete v tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Poznámky  
 `fread_s` Funkce přečte až `count` položky `elementSize` bajtů ze vstupu `stream` a ukládá je v `buffer`.  Ukazatele souboru, který je spojen s `stream` (pokud existuje) je zvýšit počet bajtů ve skutečnosti číst. S daným datovým proudem se při otevření v textovém režimu, páry vrátit-konce řádku znaků CR jsou nahrazeny znaky konce řádku jeden. Pokud chcete nahrazení nemá žádný vliv na ukazatele souboru nebo návratovou hodnotu. Pozice ukazatele souboru je neurčitou, pokud dojde k chybě. Hodnota částečně čtení položky nelze určit.  
  
 Tato funkce zamezí jiná vlákna. Pokud budete potřebovat bez uzamčení verzi, použijte `_fread_nolock`.  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Požadovaný hlavičkový soubor|  
|--------------|---------------------|  
|`fread_s`|\<stdio.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```cpp  
// crt_fread_s.c  
// Command line: cl /EHsc /nologo /W4 crt_fread_s.c  
//  
// This program opens a file that's named FREAD.OUT and  
// writes characters to the file. It then tries to open  
// FREAD.OUT and read in characters by using fread_s. If the attempt succeeds,  
// the program displays the number of actual items read.  
  
#include <stdio.h>  
  
#define BUFFERSIZE 30  
#define DATASIZE 22  
#define ELEMENTCOUNT 2  
#define ELEMENTSIZE (DATASIZE/ELEMENTCOUNT)  
#define FILENAME "FREAD.OUT"  
  
int main( void )  
{  
   FILE *stream;  
   char list[30];  
   int  i, numread, numwritten;  
  
   for ( i = 0; i < DATASIZE; i++ )  
      list[i] = (char)('z' - i);  
   list[DATASIZE] = '\0'; // terminal null so we can print it  
  
   // Open file in text mode:  
   if( fopen_s( &stream, FILENAME, "w+t" ) == 0 )  
   {  
      // Write DATASIZE characters to stream   
      printf( "Contents of buffer before write/read:\n\t%s\n\n", list );  
      numwritten = fwrite( list, sizeof( char ), DATASIZE, stream );  
      printf( "Wrote %d items\n\n", numwritten );  
      fclose( stream );  
   } else {  
      printf( "Problem opening the file\n" );  
      return -1;  
   }  
  
   if( fopen_s( &stream, FILENAME, "r+t" ) == 0 )   {  
      // Attempt to read in characters in 2 blocks of 11  
      numread = fread_s( list, BUFFERSIZE, ELEMENTSIZE, ELEMENTCOUNT, stream );  
      printf( "Number of %d-byte elements read = %d\n\n", ELEMENTSIZE, numread );  
      printf( "Contents of buffer after write/read:\n\t%s\n", list );  
      fclose( stream );  
   } else {  
      printf( "File could not be opened\n" );  
      return -1;  
   }  
}  
```  
  
```Output  
Contents of buffer before write/read:   
        zyxwvutsrqponmlkjihgfe  
  
Wrote 22 items  
  
Number of 11-byte elements read = 2  
  
Contents of buffer after write/read:   
        zyxwvutsrqponmlkjihgfe  
```  
  
## <a name="see-also"></a>Viz také  
 [Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)   
 [fwrite –](../../c-runtime-library/reference/fwrite.md)   
 [_read](../../c-runtime-library/reference/read.md)