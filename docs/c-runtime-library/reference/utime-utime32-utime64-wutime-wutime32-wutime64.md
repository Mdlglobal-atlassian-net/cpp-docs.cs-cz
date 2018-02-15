---
title: "_utime –, _utime32 –, _utime64 –, _wutime –, _wutime32 –, _wutime64 – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _utime64
- _utime
- _wutime
- _wutime64
- _wutime32
- _utime32
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
- _tutime
- _utime64
- wutime
- utime32
- wutime64
- _utime
- wutime32
- _wutime
- utime
- utime64
- _wutime64
- _utime32
- _tutime64
- _wutime32
dev_langs:
- C++
helpviewer_keywords:
- tutime function
- utime32 function
- utime64 function
- _utime function
- _tutime32 function
- time [C++], file modification
- wutime function
- _wutime function
- _wutime32 function
- _tutime64 function
- _tutime function
- files [C++], modification time
- _wutime64 function
- _utime32 function
- utime function
- _utime64 function
- wutime64 function
- wutime32 function
- tutime64 function
- tutime32 function
ms.assetid: 8d482d40-19b9-4591-bfee-5d7f601d1a9e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f94c67fe75f5675192dbd0f306d8eef0aace70f5
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="utime-utime32-utime64-wutime-wutime32-wutime64"></a>_utime, _utime32, _utime64, _wutime, _wutime32, _wutime64
Nastavte čas modifikace souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _utime(  
   const char *filename,  
   struct _utimbuf *times   
);  
int _utime32(  
   const char *filename,  
   struct __utimbuf32 *times   
);  
int _utime64(  
   const char *filename,  
   struct __utimbuf64 *times   
);  
int _wutime(  
   const wchar_t *filename,  
   struct _utimbuf *times   
);  
int _wutime32(  
   const wchar_t *filename,  
   struct __utimbuf32 *times   
);  
int _wutime64(  
   const wchar_t *filename,  
   struct __utimbuf64 *times   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `filename`  
 Ukazatel na řetězec, který obsahuje cesta nebo název souboru.  
  
 `times`  
 Ukazatel na uložené hodnoty času.  
  
## <a name="return-value"></a>Návratová hodnota  
 Každá z těchto funkcí vrátí 0, pokud čas modifikace souboru byl změněn. Vrácená hodnota -1 označuje chybu. Pokud je předán neplatný parametr, je obslužná rutina neplatný parametr vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, tyto funkce vrátí hodnotu -1 a `errno` nastaven na jednu z následujících hodnot:  
  
 `EACCES`  
 Cesta Určuje adresář nebo soubor určený jen pro čtení  
  
 `EINVAL`  
 Neplatný `times` argument  
  
 `EMFILE`  
 Příliš mnoho souborů (soubor musí být otevřené pro změnit jeho čas změny)  
  
 `ENOENT`  
 Cesta nebo název souboru nebyla nalezena  
  
 V tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o těchto a dalších návratové kódy.  
  
 Datum můžete změnit pro soubor, pokud je datum změny po půlnoc 1. ledna 1970 a před datem ukončení funkce používá. `_utime` a `_wutime` použít hodnotu 64-bit čas tak, aby koncové datum 23:59:59, 31. prosince 3000, UTC. Pokud `_USE_32BIT_TIME_T` je definována přinutit staré chování je koncové datum 23:59:59 18 leden 2038 UTC. `_utime32` nebo `_wutime32` použít typu time 32-bit bez ohledu na to, jestli se `_USE_32BIT_TIME_T` je definovaný a mít vždy starší koncové datum. `_utime64` nebo `_wutime64` vždy používat typ času 64-bit, takže tyto funkce podporují vždy novější koncové datum.  
  
## <a name="remarks"></a>Poznámky  
 `_utime` Funkce nastaví čas změny pro soubor určený touto `filename` *.* Proces musí mít oprávnění k zápisu do souboru, chcete-li změnit čas. V operačním systému Windows, můžete změnit čas přístupu a čas změny v `_utimbuf` struktura. Pokud `times` je `NULL` ukazatele, čas změny nastavena na aktuálním místním časem. V opačném `times` musí odkazovat na strukturu typu `_utimbuf`, definované v SYS\UTIME. H.  
  
 `_utimbuf` Struktura ukládá časů přístup a změny souboru používané `_utime` změnit data modifikace souboru. Struktura má následující pole, které jsou obě typu `time_t`:  
  
 `actime`  
 Čas přístup k souborům  
  
 `modtime`  
 Čas modifikace souboru  
  
 Konkrétní verze `_utimbuf` struktury (`_utimebuf32` a `__utimbuf64`) jsou definovány pomocí 32bitové a 64bitové verze typu time. Ty se používají v 32bitové a 64bitové verze konkrétních verzí této funkce. `_utimbuf` samotný ve výchozím nastavení používá typu time 64-bit, pokud `_USE_32BIT_TIME_T` je definována.  
  
 `_utime` je stejný jako `_futime` s tím rozdílem, že `filename` argument `_utime` je název souboru nebo cestu k souboru, místo popisovače souborů otevřeného souboru.  
  
 `_wutime` široká charakterová verze `_utime`; `filename` argument `_wutime` je široká charakterová řetězec. Tyto funkce chovají stejně jako jinak.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tutime`|`_utime`|`_utime`|`_wutime`|  
|`_tutime32`|`_utime32`|`_utime32`|`_wutime32`|  
|`_tutime64`|`_utime64`|`_utime64`|`_wutime64`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadované hlavičky|Volitelné hlavičky|  
|-------------|----------------------|----------------------|  
|`_utime`, `_utime32`, `_utime64`|\<sys/utime.h>|\<errno.h>|  
|`_utime64`|\<sys/utime.h>|\<errno.h>|  
|`_wutime`|\<utime.h > nebo \<wchar.h >|\<errno.h>|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
 Tento program používá `_utime` nastavit čas modifikace souboru na aktuální čas.  
  
```  
// crt_utime.c  
#include <stdio.h>  
#include <stdlib.h>  
#include <sys/types.h>  
#include <sys/utime.h>  
#include <time.h>  
  
int main( void )  
{  
   struct tm tma = {0}, tmm = {0};  
   struct _utimbuf ut;  
  
   // Fill out the accessed time structure  
   tma.tm_hour = 12;  
   tma.tm_isdst = 0;  
   tma.tm_mday = 15;  
   tma.tm_min = 0;  
   tma.tm_mon = 0;  
   tma.tm_sec = 0;  
   tma.tm_year = 103;  
  
   // Fill out the modified time structure  
   tmm.tm_hour = 12;  
   tmm.tm_isdst = 0;  
   tmm.tm_mday = 15;  
   tmm.tm_min = 0;  
   tmm.tm_mon = 0;  
   tmm.tm_sec = 0;  
   tmm.tm_year = 102;  
  
   // Convert tm to time_t  
   ut.actime = mktime(&tma);  
   ut.modtime = mktime(&tmm);  
  
   // Show file time before and after  
   system( "dir crt_utime.c" );  
   if( _utime( "crt_utime.c", &ut ) == -1 )  
      perror( "_utime failed\n" );  
   else  
      printf( "File time modified\n" );  
   system( "dir crt_utime.c" );  
}  
```  
  
## <a name="sample-output"></a>Vzorový výstup  
  
```  
Volume in drive C has no label.  
 Volume Serial Number is 9CAC-DE74  
  
 Directory of C:\test  
  
01/09/2003  05:38 PM               935 crt_utime.c  
               1 File(s)            935 bytes  
               0 Dir(s)  20,742,955,008 bytes free  
File time modified  
 Volume in drive C has no label.  
 Volume Serial Number is 9CAC-DE74  
  
 Directory of C:\test  
  
01/15/2002  12:00 PM               935 crt_utime.c  
               1 File(s)            935 bytes  
               0 Dir(s)  20,742,955,008 bytes free  
```  
  
## <a name="see-also"></a>Viz také  
 [Správa času](../../c-runtime-library/time-management.md)   
 [asctime, _wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](../../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)   
 [_ftime, _ftime32, _ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [_futime, _futime32, _futime64](../../c-runtime-library/reference/futime-futime32-futime64.md)   
 [gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime, _localtime32, _localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [_stat, _wstat – funkce](../../c-runtime-library/reference/stat-functions.md)   
 [time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)