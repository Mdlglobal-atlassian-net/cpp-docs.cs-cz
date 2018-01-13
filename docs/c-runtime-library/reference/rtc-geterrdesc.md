---
title: "_Rtc_geterrdesc – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _RTC_GetErrDesc
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
- RTC_GetErrDesc
- _RTC_GetErrDesc
dev_langs: C++
helpviewer_keywords:
- run-time errors
- _RTC_GetErrDesc function
- RTC_GetErrDesc function
ms.assetid: 7994ec2b-5488-4fd4-806d-a166c9a9f927
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3149c1be671566785f67963368a50cdf2eee3809
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="rtcgeterrdesc"></a>_RTC_GetErrDesc
Vrátí stručný popis typu Chyba spuštění kontroly (RTC).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      const char * _RTC_GetErrDesc(  
   _RTC_ErrorNumber errnum   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *errnum*  
 Číslo v rozsahu od 0 do 1 menší než hodnota vrácený `_RTC_NumErrors`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Řetězec znaků, který obsahuje krátký popis jeden z typů chyb zjištěna chyba spuštění kontroly systémem. Pokud chyba je menší než nula nebo větší než nebo rovna hodnotě vrácené [_rtc_numerrors –](../../c-runtime-library/reference/rtc-numerrors.md), `_RTC_GetErrDesc` vrátí hodnotu NULL.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_RTC_GetErrDesc`|\<rtcapi.h >|  
  
 Další informace najdete v tématu [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Knihovny  
 Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Viz také  
 [_Rtc_numerrors –](../../c-runtime-library/reference/rtc-numerrors.md)   
 [Kontrola chyb za běhu](../../c-runtime-library/run-time-error-checking.md)