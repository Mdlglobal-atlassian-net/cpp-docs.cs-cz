---
title: "_Rtc_seterrortype – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _RTC_SetErrorType
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
- RTC_SetErrorType
- _RTC_SetErrorType
dev_langs: C++
helpviewer_keywords:
- run-time errors
- RTC_SetErrorType function
- _RTC_SetErrorType function
ms.assetid: f5f99be7-d357-4b11-b8f5-ddd3428f2b06
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f695cb018a09725f23fb0943f9acbef83a338314
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="rtcseterrortype"></a>_RTC_SetErrorType
Přidruží k chybě, která se zjišťují pomocí Kontrola chyb za běhu (RTCs) s typem. Popisovače chyb zpracuje postup výstupní chyby zadaného typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      int _RTC_SetErrorType(  
   _RTC_ErrorNumber errnum,  
   int ErrType   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *errnum*  
 Číslo v rozsahu od 0 do 1 menší než hodnota vrácený [_rtc_numerrors –](../../c-runtime-library/reference/rtc-numerrors.md).  
  
 *ErrType*  
 Hodnota pro přiřazení k tomuto *errnum*. Například můžete použít **_CRT_ERROR**. Pokud používáte `_CrtDbgReport` jako popisovače chyb, *ErrType* může mít jenom jednu symbolů definované v [_crtsetreportmode –](../../c-runtime-library/reference/crtsetreportmode.md). Pokud máte vlastní obslužnou rutinu chyby ([_rtc_seterrorfunc –](../../c-runtime-library/reference/rtc-seterrorfunc.md)), může mít jako mnoho *ErrType*se označují jako zde *errnum*s.  
  
 *ErrType* _RTC_ERRTYPE_IGNORE mají zvláštní význam `_CrtSetReportMode`; chyba je ignorována.  
  
## <a name="return-value"></a>Návratová hodnota  
 Předchozí hodnotu pro typ chyby `type`.  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení jsou všechny chyby nastavení *ErrType* = 1, který odpovídá **_CRT_ERROR**. Další informace o této chybě výchozí typy, jako **_CRT_ERROR**, najdete v části [_crtdbgreport –](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md).  
  
 Než bude možné volat tuto funkci, nejprve je třeba volat některou z funkcí inicializace chyba spuštění kontroly; v tématu [pomocí kontrol běhu bez běhové knihovny jazyka C](/visualstudio/debugger/using-run-time-checks-without-the-c-run-time-library)  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_RTC_SetErrorType`|\<rtcapi.h >|  
  
 Další informace najdete v tématu [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Knihovny  
 Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Viz také  
 [_Rtc_geterrdesc –](../../c-runtime-library/reference/rtc-geterrdesc.md)   
 [Kontrola chyb za běhu](../../c-runtime-library/run-time-error-checking.md)