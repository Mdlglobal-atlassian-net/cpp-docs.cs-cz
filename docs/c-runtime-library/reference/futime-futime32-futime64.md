---
title: "_futime – _futime32 –, _futime64 – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _futime64
- _futime32
- _futime
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
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- futime
- _futime
- futime64
- _futime64
dev_langs:
- C++
helpviewer_keywords:
- _futime function
- futime32 function
- futime64 function
- file modification time [C++]
- _futime64 function
- futime function
- _futime32 function
ms.assetid: b942ce8f-5cc7-4fa8-ab47-de5965eded53
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8caa47cd82f61c46ee10f03987bac9735ce506cc
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="futime-futime32-futime64"></a>_futime, _futime32, _futime64
Nastaví čas změny pro soubor otevřený.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _futime(   
   int fd,  
   struct _utimbuf *filetime   
);  
int _futime32(   
   int fd,  
   struct __utimbuf32 *filetime   
);  
int _futime64(   
   int fd,  
   struct __utimbuf64 *filetime   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fd`  
 Popisovače souborů k otevření souboru.  
  
 `filetime`  
 Ukazatel na strukturu obsahující nové datum změny.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí 0, pokud bylo úspěšné. Pokud dojde k chybě, je obslužná rutina neplatný parametr vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, funkce vrátí hodnotu -1 a `errno` je nastaven na `EBADF`, označující popisovač souboru je neplatný nebo `EINVAL`, označující neplatný parametr.  
  
## <a name="remarks"></a>Poznámky  
 `_futime` Rutiny nastaví datum změny a doba přístupu k otevření souboru spojené s `fd`. `_futime` je stejný jako [_utime –](../../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md)kromě toho, že je její argument popisovače souborů otevřeného souboru, nikoli název souboru nebo cestu k souboru. `_utimbuf` Struktura obsahuje pole pro nové změny datum a čas přístup. Obě pole musí obsahovat platné hodnoty. `_utimbuf32` a `_utimbuf64` jsou stejné jako `_utimbuf` s výjimkou použití typů 32bitové a 64bitové verze čas, v uvedeném pořadí. `_futime` a `_utimbuf` použít typu time 64-bit a `_futime` je stejný jako v chování `_futime64`. Pokud potřebujete vynutit staré chování, definovat `_USE_32BIT_TIME_T`. Provedete to způsobí, že `_futime` být identické v chování `_futime32` a způsobí, že `_utimbuf` strukturu chcete použít typ čas 32-bit, což odpovídá `__utimbuf32`.  
  
 `_futime64`, které používá `__utimbuf64` struktury, může číst a upravovat soubor datům až 23:59:59, 31. prosince 3000, UTC; zatímco volání `_futime32` selže, pokud data v souboru je novější než 23:59:59 18 leden 2038 UTC. Půlnoc, 1. ledna 1970, je dolní mez rozsahu kalendářních dat pro tyto funkce.  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|  
|--------------|---------------------|---------------------|  
|`_futime`|\<sys/utime.h>|\<errno.h>|  
|`_futime32`|\<sys/utime.h>|\<errno.h>|  
|`_futime64`|\<sys/utime.h>|\<errno.h>|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_futime.c  
// This program uses _futime to set the  
// file-modification time to the current time.  
  
#include <stdio.h>  
#include <stdlib.h>  
#include <fcntl.h>  
#include <io.h>  
#include <sys/types.h>  
#include <sys/stat.h>  
#include <sys/utime.h>  
#include <share.h>  
  
int main( void )  
{  
   int hFile;  
  
   // Show file time before and after.   
   system( "dir crt_futime.c_input" );  
  
   _sopen_s( &hFile, "crt_futime.c_input", _O_RDWR, _SH_DENYNO, 0 );  
  
   if( _futime( hFile, NULL ) == -1 )  
      perror( "_futime failed\n" );  
   else  
      printf( "File time modified\n" );  
  
   _close (hFile);  
  
   system( "dir crt_futime.c_input" );  
}  
```  
  
## <a name="input-crtfutimecinput"></a>Vstup: crt_futime.c_input  
  
```  
Arbitrary file contents.  
```  
  
### <a name="sample-output"></a>Vzorový výstup  
  
```  
Volume in drive Z has no label.  
 Volume Serial Number is 5C68-57C1  
  
 Directory of Z:\crt  
  
03/25/2004  10:40 AM                24 crt_futime.c_input  
               1 File(s)             24 bytes  
               0 Dir(s)  24,268,476,416 bytes free  
 Volume in drive Z has no label.  
 Volume Serial Number is 5C68-57C1  
  
 Directory of Z:\crt  
  
03/25/2004  10:41 AM                24 crt_futime.c_input  
               1 File(s)             24 bytes  
               0 Dir(s)  24,268,476,416 bytes free  
File time modified  
```  
  
## <a name="see-also"></a>Viz také  
 [Správa času](../../c-runtime-library/time-management.md)