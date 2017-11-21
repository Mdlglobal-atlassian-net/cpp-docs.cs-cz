---
title: "_findfirst –, _findfirst32 –, _findfirst32i64 –, _findfirst64 –, _findfirst64i32 –, _findfirsti64 –, _wfindfirst –, _wfindfirst32 –, _wfindfirst32i64 –, _wfindfirst64 –, _wfindfirst64i32 –, _wfindfirsti64 – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _findfirst
- _wfindfirst
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- findfirst32i64
- wfindfirst32i64
- tfindfirst64
- _findfirst64i32
- _wfindfirst32i64
- _wfindfirsti64
- wfindfirst
- _tfindfirsti64
- findfirst32
- _tfindfirst32
- _findfirsti64
- findfirst
- wfindfirst64
- wfindfirst32
- tfindfirst32
- _wfindfirst64i32
- findfirst64i32
- tfindfirst64i32
- _wfindfirst
- findfirsti64
- _findfirst32i64
- wfindfirst64i32
- _wfindfirst32
- _findfirst32
- _tfindfirst32i64
- tfindfirst
- _tfindfirst64i32
- findfirst64
- _tfindfirst
- _findfirst64
- _tfindfirst64
- tfindfirst32i64
- _findfirst
- _wfindfirst64
dev_langs: C++
helpviewer_keywords:
- _tfindfirst64 function
- _wfindfirst64i32 function
- _wfindfirst32i64 function
- wfindfirst32 function
- _findfirst function
- wfindfirst64 function
- _wfindfirst function
- _findfirst64i32 function
- wfindfirst function
- _findfirst64 function
- tfindfirst32 function
- _tfindfirst64i32 function
- findfirst function
- findfirst32i64 function
- tfindfirst64 function
- _tfindfirst32 function
- tfindfirst32i64 function
- tfindfirst64i32 function
- _wfindfirsti64 function
- _findfirst32i64 function
- findfirst32 function
- findfirsti64 function
- findfirst64i32 function
- tfindfirsti64 function
- tfindfirst function
- _wfindfirst32 function
- wfindfirsti64 function
- _tfindfirsti64 function
- _tfindfirst function
- _tfindfirst32i64 function
- findfirst64 function
- _findfirst32 function
- _findfirsti64 function
- wfindfirst32i64 function
- wfindfirst64i32 function
- _wfindfirst64 function
ms.assetid: 9bb46d1a-b946-47de-845a-a0b109a33ead
caps.latest.revision: "25"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ab92c7116b5a4c76d136f3f448b75b3801977822
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="findfirst-findfirst32-findfirst32i64-findfirst64-findfirst64i32-findfirsti64-wfindfirst-wfindfirst32-wfindfirst32i64-wfindfirst64-wfindfirst64i32-wfindfirsti64"></a>_findfirst –, _findfirst32 –, _findfirst32i64 –, _findfirst64 –, _findfirst64i32 –, _findfirsti64 –, _wfindfirst –, _wfindfirst32 –, _wfindfirst32i64 –, _wfindfirst64 –, _wfindfirst64i32 –, _wfindfirsti64 –
Zadání informací o první instance název souboru, který odpovídá zadané v souboru `filespec` argument.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
intptr_t _findfirst(  
   const char *filespec,  
   struct _finddata_t *fileinfo   
);  
intptr_t _findfirst32(  
   const char *filespec,  
   struct _finddata32_t *fileinfo   
);  
intptr_t _findfirst64(  
   const char *filespec,  
   struct _finddata64_t *fileinfo   
);  
intptr_t _findfirsti64(  
   const char *filespec,  
   struct _finddatai64_t *fileinfo   
);  
intptr_t _findfirst32i64(  
   const char *filespec,  
   struct _finddata32i64_t *fileinfo   
);  
intptr_t _findfirst64i32(  
   const char *filespec,  
   struct _finddata64i32_t *fileinfo   
);  
intptr_t _wfindfirst(  
   const wchar_t *filespec,  
   struct _wfinddata_t *fileinfo   
);  
intptr_t _wfindfirst32(  
   const wchar_t *filespec,  
   struct _wfinddata32_t *fileinfo   
);  
intptr_t _wfindfirst64(  
   const wchar_t *filespec,  
   struct _wfinddata64_t *fileinfo   
);  
intptr_t _wfindfirsti64(  
   const wchar_t *filespec,  
   struct _wfinddatai64_t *fileinfo   
);  
intptr_t _wfindfirst32i64(  
   const wchar_t *filespec,  
   struct _wfinddata32i64_t *fileinfo   
);  
intptr_t _wfindfirst64i32(  
   const wchar_t *filespec,  
   struct _wfinddata64i32_t *fileinfo   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `filespec`  
 Specifikaci souboru cíle (můžete použít zástupné znaky).  
  
 `fileinfo`  
 Vyrovnávací paměť informace o souboru.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěšného `_findfirst` vrátí popisovač jedinečný vyhledávání identifikace soubor nebo skupinu souborů, které odpovídají `filespec` specifikace, který může být použit v následné volání [_findnext –](../../c-runtime-library/reference/findnext-functions.md) nebo `_findclose`. V opačném `_findfirst` vrátí hodnotu -1 a nastaví `errno` na jednu z následujících hodnot.  
  
 `EINVAL`  
 Neplatný parametr: `filespec` nebo `fileinfo` byla `NULL`. Nebo operační systém vrátil neočekávanou chybu.  
  
 `ENOENT`  
 Specifikaci souboru, který se neshoduje.  
  
 `ENOMEM`  
 Není dostatek paměti.  
  
 `EINVAL`  
 Zadání názvu souboru je neplatný nebo daný název souboru byl větší, než `MAX_PATH`.  
  
 Další informace o těchto a dalších návratové kódy najdete v tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 Pokud není předán neplatný parametr v těchto funkcí vyvolat obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md).  
  
## <a name="remarks"></a>Poznámky  
 Je třeba volat [_findclose –](../../c-runtime-library/reference/findclose.md) po dokončení se buď `_findfirst` nebo `_findnext` funkci (nebo všechny varianty). Tím se uvolní prostředky využívané třídou tyto funkce ve vaší aplikaci.  
  
 Variace tyto funkce, které mají `w` předponu široká charakterová verze; jinak, jsou shodné s odpovídající funkce jednobajtové.  
  
 Variace tyto funkce podporují 32bitovou nebo 64bitovou čas typy a velikosti souborů 32bitové nebo 64bitové verze. První číselnou příponou (`32` nebo `64`) určuje velikost typ času; druhý přípona je buď `i32` nebo `i64`a určuje, zda velikost souboru je reprezentována jako 32bitové nebo 64bitové celé číslo. Další informace o tom, které podporují verze 32bitové a 64bitové verze čas typy a velikosti souborů najdete v následující tabulce. `i32` Nebo `i64` přípona je vynechána, pokud je stejná jako velikost typ času, takže `_findfirst64` také podporuje 64bitový soubor délky a `_findfirst32` podporuje pouze 32bitové souboru délky.  
  
 Tyto funkce používat různé formy `_finddata_t` struktury pro `fileinfo` parametr. Další informace o struktuře najdete v tématu [funkce hledání Filename](../../c-runtime-library/filename-search-functions.md).  
  
 Varianty, které používají typu time 64-bit povolit vytváření souborů data, která se vyjádřit až prostřednictvím 23:59:59, 31. prosince 3000, UTC. Ty, které používají 32bitovou čas typy představují data pouze prostřednictvím 23:59:59 18 leden 2038 UTC. Půlnoc, 1. ledna 1970, je dolní mez rozsahu kalendářních dat pro všechny tyto funkce.  
  
 Pokud nemáte konkrétní důvod používat verze, které explicitně zadat čas velikost, použijte `_findfirst` nebo `_wfindfirst` nebo, pokud potřebujete podporovat velikost souboru je větší než 3 GB, použijte `_findfirsti64` nebo `_wfindfirsti64`. Všechny tyto funkce použijte typ 64-bit času. V dřívějších verzích tyto funkce používají typu time 32-bit. Pokud je to narušující změně pro aplikaci, můžete třeba definovat `_USE_32BIT_TIME_T` se vrátit k původní chování. Pokud `_USE_32BIT_TIME_T` je definován `_findfirst`, `_finfirsti64`, a jejich odpovídající verze Unicode používají 32bitové čas.  
  
### <a name="time-type-and-file-length-type-variations-of-findfirst"></a>Typ času a soubor délka typu Variant _findfirst –  
  
|Funkce|`_USE_32BIT_TIME_T`definované?|Typ času|Typ délku souboru|  
|---------------|----------------------------------|---------------|----------------------|  
|`_findfirst`, `_wfindfirst`|Nejsou definována.|64bitových|32bitová|  
|`_findfirst`, `_wfindfirst`|Definované|32bitová|32bitová|  
|`_findfirst32`, `_wfindfirst32`|Není vliv na definici – makro|32bitová|32bitová|  
|`_findfirst64`, `_wfindfirst64`|Není vliv na definici – makro|64bitových|64bitových|  
|`_findfirsti64`, `_wfindfirsti64`|Nejsou definována.|64bitových|64bitových|  
|`_findfirsti64`, `_wfindfirsti64`|Definované|32bitová|64bitových|  
|`_findfirst32i64`, `_wfindfirst32i64`|Není vliv na definici – makro|32bitová|64bitových|  
|`_findfirst64i32`, `_wfindfirst64i32`|Není vliv na definici – makro|64bitových|32bitová|  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tfindfirst`|`_findfirst`|`_findfirst`|`_wfindfirst`|  
|`_tfindfirst32`|`_findfirst32`|`_findfirst32`|`_wfindfirst32`|  
|`_tfindfirst64`|`_findfirst64`|`_findfirst64`|`_wfindfirst64`|  
|`_tfindfirsti64`|`_findfirsti64`|`_findfirsti64`|`_wfindfirsti64`|  
|`_tfindfirst32i64`|`_findfirst32i64`|`_findfirst32i64`|`_wfindfirst32i64`|  
|`_tfindfirst64i32`|`_findfirst64i32`|`_findfirst64i32`|`_wfindfirst64i32`|  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Požadovaný hlavičkový soubor|  
|--------------|---------------------|  
|`_findfirst`|\<IO.h >|  
|`_findfirst32`|\<IO.h >|  
|`_findfirst64`|\<IO.h >|  
|`_findfirsti64`|\<IO.h >|  
|`_findfirst32i64`|\<IO.h >|  
|`_findfirst64i32`|\<IO.h >|  
|`_wfindfirst`|\<IO.h > nebo \<wchar.h >|  
|`_wfindfirst32`|\<IO.h > nebo \<wchar.h >|  
|`_wfindfirst64`|\<IO.h > nebo \<wchar.h >|  
|`_wfindfirsti64`|\<IO.h > nebo \<wchar.h >|  
|`_wfindfirst32i64`|\<IO.h > nebo \<wchar.h >|  
|`_wfindfirst64i32`|\<IO.h > nebo \<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="see-also"></a>Viz také  
 [Systémová volání](../../c-runtime-library/system-calls.md)   
 [Název souboru – funkce hledání](../../c-runtime-library/filename-search-functions.md)