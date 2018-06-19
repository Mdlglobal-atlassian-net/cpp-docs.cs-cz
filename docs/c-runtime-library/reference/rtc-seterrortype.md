---
title: _Rtc_seterrortype – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _RTC_SetErrorType
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
dev_langs:
- C++
helpviewer_keywords:
- run-time errors
- RTC_SetErrorType function
- _RTC_SetErrorType function
ms.assetid: f5f99be7-d357-4b11-b8f5-ddd3428f2b06
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 83395727b37ea3901e2e3c28d7adb6663f043d12
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32406612"
---
# <a name="rtcseterrortype"></a>_RTC_SetErrorType

Přidruží k chybě, která se zjišťují pomocí Kontrola chyb za běhu (RTCs) s typem. Popisovače chyb zpracuje postup výstupní chyby zadaného typu.

## <a name="syntax"></a>Syntaxe

```C
int _RTC_SetErrorType(
   _RTC_ErrorNumber errnum,
   int ErrType
);
```

### <a name="parameters"></a>Parametry

*errnum*<br/>
Číslo v rozsahu od 0 do 1 menší než hodnota vrácený [_rtc_numerrors –](rtc-numerrors.md).

*ErrType*<br/>
Hodnota pro přiřazení k tomuto *errnum*. Například můžete použít **_CRT_ERROR**. Pokud používáte **_crtdbgreport –** jako popisovače chyb, *ErrType* může mít jenom jednu symbolů definované v [_crtsetreportmode –](crtsetreportmode.md). Pokud máte vlastní obslužnou rutinu chyby ([_rtc_seterrorfunc –](rtc-seterrorfunc.md)), může mít jako mnoho *ErrType*se označují jako zde *errnum*s.

*ErrType* _RTC_ERRTYPE_IGNORE mají zvláštní význam **_crtsetreportmode –**; chyba je ignorována.

## <a name="return-value"></a>Návratová hodnota

Předchozí hodnotu pro typ chyby *typu*.

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení jsou všechny chyby nastavení *ErrType* = 1, který odpovídá **_CRT_ERROR**. Další informace o této chybě výchozí typy, jako **_CRT_ERROR**, najdete v části [_crtdbgreport –](crtdbgreport-crtdbgreportw.md).

Než bude možné volat tuto funkci, nejprve je třeba volat některou z funkcí inicializace chyba spuštění kontroly; v tématu [pomocí kontrol běhu bez běhové knihovny jazyka C](/visualstudio/debugger/using-run-time-checks-without-the-c-run-time-library)

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_RTC_SetErrorType**|\<rtcapi.h >|

Další informace najdete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Viz také

[_RTC_GetErrDesc](rtc-geterrdesc.md)<br/>
[Kontrola chyb za běhu](../../c-runtime-library/run-time-error-checking.md)<br/>
