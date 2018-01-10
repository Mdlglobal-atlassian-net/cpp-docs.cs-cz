---
title: timespec_get, _timespec32_get, _timespec64_get1 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- timespec_get
- _timespec32_get
- _timespec64_get
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
- timespec_get
- _timespec32_get
- _timespec64_get
- time/timespec_get
- time/_timespec32_get
- time/_timespec64_get
- timespec
- _timespec32
- _timespec64
dev_langs: C++
helpviewer_keywords:
- timespec_get function
- _timespec32_get function
- _timespec64_get function
ms.assetid: ed757258-b4f2-4c1d-a91b-22ea6ffce4ab
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 681f9d125a7f45dae2a8e604df655facdd246067
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="timespecget-timespec32get-timespec64get"></a>timespec_get, _timespec32_get, _timespec64_get
Nastaví interval ukazuje první argument na aktuální čas kalendáře podle základní zadané doby.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int timespec_get(  
    struct timespec* const time_spec,  
    int const base  
);  
int _timespec32_get(  
    struct _timespec32* const time_spec,  
    int const base  
);  
int _timespec64_get(  
    struct _timespec64* const time_spec,  
    int const base  
);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `time_spec`  
 Ukazatel na struktura, který je nastavený na dobu v sekundách a nanosekundách od začátku epoch.  
  
 `base`  
 Hodnota závisí na implementaci nulová, která určuje základní doba.  
  
## <a name="return-value"></a>Návratová hodnota  
 Hodnota `base` když úspěšné, jinak vrátí nula.  
  
## <a name="remarks"></a>Poznámky  
 `timespec_get` Funkce nastavit aktuální čas v struktura, na kterou odkazuje `time_spec` argument. Všechny verze tato struktura mít dva členy `tv_sec` a `tv_nsec`. `tv_sec` Hodnota nastavena na celočíselný počet sekund a `tv_nsec` na celočíselný počet nanosekundách zaokrouhlené na řešení systémové hodiny od začátku epoch určeného `base`.  
  
 **Konkrétní Microsoft**  
  
 Tyto funkce podporují pouze `TIME_UTC` jako `base` hodnotu. Tím se nastaví `time_spec` hodnota počet sekund a nanosekundách od okamžiku spuštění epoch, půlnoc, 1. ledna 1970 koordinovaný světový čas (UTC). V `struct _timespec32`, `tv_sec` je `__time32_t` hodnotu. V `struct _timespec64`, `tv_sec` je `__time64_t` hodnotu. V `struct timespec`, `tv_sec` je `time_t` typu, který je 32bitová verze nebo 64 bitů v závislosti na tom, zda je definována _USE_32BIT_TIME_T makro preprocesoru. `timespec_get` Funkce je vložená funkce, která volá `_timespec32_get` Pokud _USE_32BIT_TIME_T je definován; jinak zavolá `_timespec64_get`.  
  
 **Konkrétní Microsoft end**  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`timespec_get`, `_timespec32_get`, `_timespec64_get`|C: \<time.h >, C++: \<ctime > nebo \<time.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Správa času](../../c-runtime-library/time-management.md)   
 [asctime –, _wasctime –](../../c-runtime-library/reference/asctime-wasctime.md)   
 [asctime_s –, _wasctime_s –](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [_ftime – _ftime32 –, _ftime64 –](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime – _gmtime32 –, _gmtime64 –](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [gmtime_s – _gmtime32_s –, _gmtime64_s –](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [místní čas, _localtime32 –, _localtime64 –](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [localtime_s – _localtime32_s –, _localtime64_s –](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [čas, _time32 –, _time64 –](../../c-runtime-library/reference/time-time32-time64.md)   
 [_utime, _utime32, _utime64, _wutime, _wutime32, _wutime64](../../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md)