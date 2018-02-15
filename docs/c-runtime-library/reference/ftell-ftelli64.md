---
title: "ftell –, _ftelli64 – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _ftelli64
- ftell
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
- _ftelli64
- ftell
dev_langs:
- C++
helpviewer_keywords:
- ftell function
- ftelli64 function
- _ftelli64 function
- file pointers [C++], getting current position
- file pointers [C++]
ms.assetid: 40149cd8-65f2-42ff-b70c-68e3e918cdd7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b7bb0c1954d79261298cccccec980fa446d0cf00
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="ftell-ftelli64"></a>ftell, _ftelli64
Získá aktuální umístění ukazatele souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
long ftell(   
   FILE *stream   
);  
__int64 _ftelli64(   
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `stream`  
 Cíl `FILE` struktura.  
  
## <a name="return-value"></a>Návratová hodnota  
 `ftell` a `_ftelli64` vrátí aktuální pozice v souboru. Hodnoty vrácené `ftell` a `_ftelli64` nemusí odrážet posun fyzické bajtů pro datové proudy otevřít v textovém režimu, protože režim textové způsobí, že překlad znaků CR vrátit-konce řádku. Použití `ftell` s `fseek` nebo `_ftelli64` s `_fseeki64` se vraťte do umístění souborů správně. V případě chyby `ftell` a `_ftelli64` vyvolat obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, tyto funkce vrátí hodnotu-1 L a sadu `errno` na jednu z dvě konstanty, definované v kód chyby. H. `EBADF` Konstanta znamená `stream` argument není platný soubor hodnota ukazatele nebo neodkazuje na otevření souboru. `EINVAL` znamená neplatný `stream` funkci byl předán argument. Na zařízeních nepodporující vyhledávání (jako jsou terminály a tiskárny) nebo když `stream` neodkazuje na soubor otevřít, není definován návratovou hodnotu.  
  
 V tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o těchto a dalších návratové kódy.  
  
## <a name="remarks"></a>Poznámky  
 `ftell` a `_ftelli64` funkce načíst aktuální pozici ukazatele souboru (pokud existuje) přidružené k `stream`. Pozice se vyjadřuje jako posun vůči začátkem datového proudu.  
  
 Všimněte si, že po otevření souboru pro připojování dat aktuální pozice v souboru je určen poslední vstupně-výstupní operace, nikoli kde bude probíhat další zápisu. Například pokud soubor, je otevřené připojení a poslední operace byla pro čtení, pozice v souboru je bod, kde další operace čtení by spustit, kde by spustit další zápisu. (Po otevření souboru pro připojování pozice v souboru přesunout na konec souboru před všechny operace zápisu.) Pokud žádná vstupně-výstupní operace došlo k ještě v souboru otevřen pro přidávání, pozice v souboru je začátku souboru.  
  
 V režimu textových CTRL + Z interpretována jako znak end souboru na vstup. V souborech otevřít pro čtení/zápis `fopen` a všechny související rutiny vyhledávat CTRL + Z na konci souboru a pokud je to možné jej odebrat. To je provést, protože pomocí kombinace `ftell` a `fseek` nebo `_ftelli64` a `_fseeki64`, v souboru, který může způsobit, že na konci CTRL + Z přesuňte `ftell` nebo `_ftelli64` chovat nesprávně blíží konec souboru.  
  
 Tato funkce zamkne volající vlákno během provádění a je proto bezpečné pro přístup z více vláken. Bez uzamčení verze, najdete v části `_ftell_nolock`.  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Požadovaný hlavičkový soubor|Volitelné hlavičky|  
|--------------|---------------------|----------------------|  
|`ftell`|\<stdio.h>|\<errno.h>|  
|`_ftelli64`|\<stdio.h>|\<errno.h>|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_ftell.c  
// This program opens a file named CRT_FTELL.C  
// for reading and tries to read 100 characters. It  
// then uses ftell to determine the position of the  
// file pointer and displays this position.  
  
#include <stdio.h>  
  
FILE *stream;  
  
int main( void )  
{  
   long position;  
   char list[100];  
   if( fopen_s( &stream, "crt_ftell.c", "rb" ) == 0 )  
   {  
      // Move the pointer by reading data:   
      fread( list, sizeof( char ), 100, stream );  
      // Get position after read:   
      position = ftell( stream );  
      printf( "Position after trying to read 100 bytes: %ld\n",  
              position );  
      fclose( stream );  
   }  
}  
```  
  
```Output  
Position after trying to read 100 bytes: 100  
```  
  
## <a name="see-also"></a>Viz také  
 [Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)   
 [fopen –, _wfopen –](../../c-runtime-library/reference/fopen-wfopen.md)   
 [fgetpos –](../../c-runtime-library/reference/fgetpos.md)   
 [fseek, _fseeki64](../../c-runtime-library/reference/fseek-fseeki64.md)   
 [_lseek, _lseeki64](../../c-runtime-library/reference/lseek-lseeki64.md)