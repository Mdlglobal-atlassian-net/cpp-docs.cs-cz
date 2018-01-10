---
title: _Zobrazit | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _read
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
f1_keywords: _read
dev_langs: C++
helpviewer_keywords:
- data [CRT]
- _read function
- read function
- data [C++], reading
- reading data [C++]
- files [C++], reading
ms.assetid: 2ce9c433-57ad-47fe-9ac1-4a7d4c883d30
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0c55e2607a706648c818fc94e73197756470110c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="read"></a>_read

Čte data ze souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _read(  
   int fd,  
   void *buffer,  
   unsigned int count   
);  
```  
  
### <a name="parameters"></a>Parametry  

*FD*  
Popisovače souborů na otevření souboru.  
  
*vyrovnávací paměti*  
Umístění úložiště pro data.  
  
*počet*  
Maximální počet bajtů.  
  
## <a name="return-value"></a>Návratová hodnota  

`_read`Vrátí počet bajtů přečtených, což může být menší než *počet* Pokud méně než *počet* left bajtů v souboru nebo pokud byl soubor otevřít v textovém režimu, v takovém případě každý vrátí řádek znaků CR kanálu pár `\r\n` se nahradí znak jednoho konce řádku `\n`. Pouze jeden konce řádku znak se počítá v návratovou hodnotu. Pokud chcete nahrazení neovlivňuje ukazatele souboru.  
  
Pokud funkce se pokusí přečíst na konci souboru, vrátí hodnotu 0. Pokud *fd* není platný soubor není otevřen pro čtení, nebo je soubor uzamčený, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, funkce vrátí hodnotu -1 a nastaví je povoleno spuštění `errno` k `EBADF`.  
  
Pokud *vyrovnávací paměti* je **NULL**, je volána obslužná rutina neplatný parametr. Pokud je povoleno provádění pokračovat, funkce vrátí hodnotu -1 a `errno` je nastaven na `EINVAL`.  
  
Další informace o tomto a ostatní návratové kódy najdete v tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Poznámky  

`_read` Funkce přečte maximálně *počet* bajtů do *vyrovnávací paměti* ze souboru přidružené *fd*. Operace čtení začíná na aktuální pozici přidruženou k dané soubor ukazatele souboru. Po operaci čtení ukazatele souboru odkazuje na Další nepřečtená znak.  
  
Pokud byl soubor otevřít v textovém režimu, čtení ukončí při `_read` zaznamená CTRL + Z znaku, který je považován za indikátor end souboru. Použití [_lseek –](../../c-runtime-library/reference/lseek-lseeki64.md) zrušte end souborového indikátoru.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_read`|\<IO.h >|  
  
Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Knihovny  

Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Příklad  
  
```C  
// crt_read.c  
/* This program opens a file named crt_read.txt  
 * and tries to read 60,000 bytes from  
 * that file using _read. It then displays the  
 * actual number of bytes read.  
 */  
  
#include <fcntl.h>      /* Needed only for _O_RDWR definition */  
#include <io.h>  
#include <stdlib.h>  
#include <stdio.h>  
#include <share.h>  
  
char buffer[60000];  
  
int main( void )  
{  
   int fh;  
   unsigned int nbytes = 60000, bytesread;  
  
   /* Open file for input: */  
   if( _sopen_s( &fh, "crt_read.txt", _O_RDONLY, _SH_DENYNO, 0 ) )  
   {  
      perror( "open failed on input file" );  
      exit( 1 );  
   }  
  
   /* Read in input: */  
   if( ( bytesread = _read( fh, buffer, nbytes ) ) <= 0 )  
      perror( "Problem reading file" );  
   else  
      printf( "Read %u bytes from file\n", bytesread );  
  
   _close( fh );  
}  
```  
  
### <a name="input-crtreadtxt"></a>Vstup: crt_read.txt  
  
```  
Line one.  
Line two.  
```  
  
### <a name="output"></a>Výstup  
  
```  
Read 19 bytes from file  
```  
  
## <a name="see-also"></a>Viz také  

[I/O nízké úrovně](../../c-runtime-library/low-level-i-o.md)   
[_creat –, _wcreat –](../../c-runtime-library/reference/creat-wcreat.md)   
[fread –](../../c-runtime-library/reference/fread.md)   
[_Otevřít _wopen –](../../c-runtime-library/reference/open-wopen.md)   
[_write](../../c-runtime-library/reference/write.md)
