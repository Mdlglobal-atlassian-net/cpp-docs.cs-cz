---
title: "_Rtc_numerrors – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _RTC_NumErrors
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
- _RTC_NumErrors
- RTC_NumErrors
dev_langs:
- C++
helpviewer_keywords:
- run-time errors
- _RTC_NumErrors function
- RTC_NumErrors function
ms.assetid: 7e82adae-38e2-4f8b-bc0b-37bda8109fd1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2034dd9c1e255196c66c4385e68c51845915ff59
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="rtcnumerrors"></a>_RTC_NumErrors
Vrátí celkový počet chyb, které lze vyhledat podle Kontrola chyb za běhu (RTC). Toto číslo můžete použít jako ovládacího prvku **pro** smyčky, kde je každá hodnota v smyčky předaný [_rtc_geterrdesc –](../../c-runtime-library/reference/rtc-geterrdesc.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
int _RTC_NumErrors( void );  
  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Celé číslo, jehož hodnota představuje celkový počet chyb, které lze vyhledat podle Kontrola chyb za běhu jazyka Visual C++.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_RTC_NumErrors`|\<rtcapi.h>|  
  
 Další informace najdete v tématu [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Knihovny  
 Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Viz také  
 [_RTC_GetErrDesc](../../c-runtime-library/reference/rtc-geterrdesc.md)   
 [Kontrola chyb za běhu](../../c-runtime-library/run-time-error-checking.md)