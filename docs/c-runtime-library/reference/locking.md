---
title: "_locking – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _locking
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
f1_keywords: _locking
dev_langs: C++
helpviewer_keywords:
- locking function
- bytes [C++], locking file
- files [C++], locking bytes
- files [C++], locking
- _locking function
ms.assetid: 099aaac1-d4ca-4827-aed6-24dff9844150
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 29211f494c905f3d82ebe3238706b2528dadce0a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="locking"></a>_locking
Uzamkne nebo odemkne bajtů souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      int _locking(  
   int fd,  
   int mode,  
   long nbytes   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fd`  
 Popisovač souboru.  
  
 *režim*  
 Uzamčení akce k provedení.  
  
 *nbytes*  
 Počet bajtů, které mají zamknout.  
  
## <a name="return-value"></a>Návratová hodnota  
 `_locking`v případě úspěchu vrátí hodnotu 0. Vrácená hodnota -1 označuje selhání, v takovém případě [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) nastaven na jednu z následujících hodnot.  
  
 `EACCES`  
 Zamykání porušení (soubor již zamčený nebo odemčený).  
  
 `EBADF`  
 Popisovač souboru je neplatný.  
  
 `EDEADLOCK`  
 Narušení uzamčení. Vrátí, když `_LK_LOCK` nebo `_LK_RLCK` zadán příznak a nelze jej zamknout soubor po 10 pokusů.  
  
 `EINVAL`  
 Byl zadán neplatný argument `_locking`.  
  
 V případě, že je chyba způsobená chybný parametr, jako je například popisovač souboru je neplatný. je obslužná rutina neplatný parametr vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md).  
  
## <a name="remarks"></a>Poznámky  
 `_locking` Funkce uzamkne nebo odemkne *nbytes* bajtů soubor určený touto `fd`. Zamykací bajty v souboru brání přístupu k těchto bajtů s jinými procesy. Všechny blokování a odblokování začíná na aktuální pozici ukazatele souboru a pokračuje další *nbytes* bajtů. Je možné zámku bajtů za koncem souboru.  
  
 *režim* musí mít jednu z následujících manifestu konstanty, které jsou definovány v Locking.h.  
  
 `_LK_LOCK`  
 Zamkne zadaný počet bajtů. Pokud počet bajtů nelze zamknout, program se okamžitě pokusí znovu po 1 sekunda. Pokud po 10 pokusy o, nelze jej zamknout počet bajtů, konstanta vrátí chybu.  
  
 `_LK_NBLCK`  
 Zamkne zadaný počet bajtů. Pokud počet bajtů nelze zamknout, konstanta vrátí chybu.  
  
 `_LK_NBRLCK`  
 Stejné jako `_LK_NBLCK`.  
  
 `_LK_RLCK`  
 Stejné jako `_LK_LOCK`.  
  
 `_LK_UNLCK`  
 Odemkne zadaný bajtů, které musí byla dříve uzamčena.  
  
 Více oblastí souboru, které se nepřekrývají může být uzamčena. V oblasti odemykají musí byla dříve uzamčena. `_locking`nesloučí přiléhající oblasti; Pokud jsou dva uzamčení oblasti vedle sebe, každou oblast, musí být odemknout samostatně. Oblasti má být uzamčena pouze stručně a by měl být odemčené před zavřením souboru nebo ukončení programu.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|  
|-------------|---------------------|---------------------|  
|`_locking`|\<IO.h > a \<sys/locking.h >|\<errno.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="libraries"></a>Knihovny  
 Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_locking.c  
/* This program opens a file with sharing. It locks  
 * some bytes before reading them, then unlocks them. Note that the  
 * program works correctly only if the file exists.  
 */  
  
#include <sys/types.h>  
#include <sys/stat.h>  
#include <sys/locking.h>  
#include <share.h>  
#include <fcntl.h>  
#include <stdio.h>  
#include <stdlib.h>  
#include <io.h>  
  
int main( void )  
{  
   int  fh, numread;  
   char buffer[40];  
  
   /* Quit if can't open file or system doesn't   
    * support sharing.   
    */  
   errno_t err = _sopen_s( &fh, "crt_locking.txt", _O_RDONLY, _SH_DENYNO,   
                          _S_IREAD | _S_IWRITE );  
   printf( "%d %d\n", err, fh );  
   if( err != 0 )  
      exit( 1 );  
  
   /* Lock some bytes and read them. Then unlock. */  
   if( _locking( fh, LK_NBLCK, 30L ) != -1 )  
   {  
      long lseek_ret;  
      printf( "No one can change these bytes while I'm reading them\n" );  
      numread = _read( fh, buffer, 30 );  
      buffer[30] = '\0';  
      printf( "%d bytes read: %.30s\n", numread, buffer );  
      lseek_ret = _lseek( fh, 0L, SEEK_SET );  
      _locking( fh, LK_UNLCK, 30L );  
      printf( "Now I'm done. Do what you will with them\n" );  
   }  
   else  
      perror( "Locking failed\n" );  
  
   _close( fh );  
}  
```  
  
## <a name="input-crtlockingtxt"></a>Vstup: crt_locking.txt  
  
```  
The first thirty bytes of this file will be locked.  
```  
  
## <a name="sample-output"></a>Vzorový výstup  
  
```  
No one can change these bytes while I'm reading them  
30 bytes read: The first thirty bytes of this  
Now I'm done. Do what you will with them  
```  
  
## <a name="see-also"></a>Viz také  
 [Zpracování souborů](../../c-runtime-library/file-handling.md)   
 [_creat –, _wcreat –](../../c-runtime-library/reference/creat-wcreat.md)   
 [_open, _wopen](../../c-runtime-library/reference/open-wopen.md)