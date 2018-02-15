---
title: "_Write – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _write
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
apitype: DLLExport
f1_keywords:
- _write
dev_langs:
- C++
helpviewer_keywords:
- _write function
- write function
- files [C++], writing to
ms.assetid: 7b868c33-766f-4e1a-95a7-e8d25f0604c4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8bf8fcbfc0d66f89667d36baeb75252e7d92abc5
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="write"></a>_write
Zapíše data do souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _write(  
   int fd,  
   const void *buffer,  
   unsigned int count   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fd`  
 Soubor popisovače souboru, do kterého se data jsou zapsána.  
  
 `buffer`  
 Data k zápisu.  
  
 `count`  
 Počet bajtů.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěšného `_write` vrátí počet bajtů zapsaných ve skutečnosti. Pokud se skutečné množství místa na disku zbývající je menší než velikost vyrovnávací paměti při pokusu o zápis na disk, je v funkce `_write` se nezdaří a není vyprázdnit všechny obsahu do vyrovnávací paměti na disk. Vrácená hodnota -1 označuje chybu. Pokud jsou předány neplatné parametry, tato funkce vyvolá obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, funkce vrátí hodnotu -1 a `errno` nastaven na jednu ze tří hodnot: `EBADF`, což znamená, že popisovač souboru je neplatný nebo soubor není otevřena pro zápis; `ENOSPC`, tzn., není k dispozici dostatek volného místa na zařízení pro operaci; nebo `EINVAL`, to znamená, že `buffer` ukazatele null nebo který odlišným `count` bajtů byl předán má být zapsán do souboru v režimu Unicode.  
  
 Další informace o těchto a dalších návratové kódy najdete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 Pokud soubor otevřete v textovém režimu, se jednotlivé znaky konce řádku nahradí CR - konce řádku pár ve výstupu. Pokud chcete nahrazení neovlivňuje návratovou hodnotu.  
  
 Při otevření souboru v režimu převodu znakové sady Unicode – například pokud `fd` otevřete pomocí `_open` nebo `_sopen` a režimu parametr, který zahrnuje `_O_WTEXT`, `_O_U16TEXT`, nebo `_O_U8TEXT`, nebo pokud je otevřen pomocí `fopen` a režimu parametr, který zahrnuje `ccs=UNICODE`, `ccs=UTF-16LE`, nebo `ccs=UTF-8`, nebo pokud změnit režim do režimu převodu znakové sady Unicode pomocí `_setmode`–`buffer` interpretována jako ukazatel na pole `wchar_t` obsahující **UTF-16** data. Pokus o zápis lichý počet bajtů v tomto režimu způsobí, že chyba ověření parametru.  
  
## <a name="remarks"></a>Poznámky  
 `_write` Funkce zápisy `count` bajtů z `buffer` do souboru přidružené `fd`. Zahájí operaci zápisu na aktuální pozici ukazatele souboru (pokud existuje) přidružené k dané souboru. Pokud je soubor otevřený pro připojování, operace začíná na aktuální konec souboru. Po operaci zápisu ukazatele souboru je zvýšit počet skutečně zapsaných bajtů.  
  
 Při zápisu do otevřeného v režimu textových souborů `_write` znak CTRL + Z považuje za logický koncoví z – soubor. Při zápisu do zařízení, `_write` zpracovává CTRL + Z znak ve vyrovnávací paměti jako ukončovací výstupu.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_write`|\<io.h>|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt__write.c  
//   
// This program opens a file for output and uses _write to write  
// some bytes to the file.  
  
#include <io.h>  
#include <stdio.h>  
#include <stdlib.h>  
#include <fcntl.h>  
#include <sys/types.h>  
#include <sys/stat.h>  
#include <errno.h>  
#include <share.h>  
  
char buffer[] = "This is a test of '_write' function";  
  
int main( void )  
{  
   int         fileHandle = 0;  
   unsigned    bytesWritten = 0;  
  
   if ( _sopen_s(&fileHandle, "write.o", _O_RDWR | _O_CREAT,  
                  _SH_DENYNO, _S_IREAD | _S_IWRITE) )  
      return -1;  
  
   if (( bytesWritten = _write( fileHandle, buffer, sizeof( buffer ))) == -1 )  
   {  
      switch(errno)  
      {  
         case EBADF:  
            perror("Bad file descriptor!");  
            break;  
         case ENOSPC:  
            perror("No space left on device!");  
            break;  
         case EINVAL:  
            perror("Invalid parameter: buffer was NULL!");  
            break;  
         default:  
            // An unrelated error occured   
            perror("Unexpected error!");  
      }  
   }  
   else  
   {  
      printf_s( "Wrote %u bytes to file.\n", bytesWritten );  
   }  
   _close( fileHandle );  
}  
```  
  
```Output  
Wrote 36 bytes to file.  
```  
  
## <a name="see-also"></a>Viz také  
 [I/O nízké úrovně](../../c-runtime-library/low-level-i-o.md)   
 [fwrite –](../../c-runtime-library/reference/fwrite.md)   
 [_open, _wopen](../../c-runtime-library/reference/open-wopen.md)   
 [_read](../../c-runtime-library/reference/read.md)   
 [_setmode](../../c-runtime-library/reference/setmode.md)