---
title: _Rtc_seterrorfunc – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _RTC_SetErrorFunc
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
- RTC_SetErrorFunc
- _RTC_SetErrorFunc
dev_langs:
- C++
helpviewer_keywords:
- RTC_SetErrorFunc function
- _RTC_SetErrorFunc function
ms.assetid: b2292722-0d83-4092-83df-3d5b19880666
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e146f699f9026260470b1c540c7567f074896a38
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2018
---
# <a name="rtcseterrorfunc"></a>_RTC_SetErrorFunc

Funkce označí jako obslužná rutina pro vytváření sestav Kontrola chyb za běhu (RTCs). Tato funkce je zastaralé; použít **_rtc_seterrorfuncw –** místo.

## <a name="syntax"></a>Syntaxe

```C
_RTC_error_fn _RTC_SetErrorFunc(
   _RTC_error_fn function
);
```

### <a name="parameters"></a>Parametry

*Funkce*<br/>
Adresa funkce, která bude zpracovávat Kontrola chyb za běhu.

## <a name="return-value"></a>Návratová hodnota

Chyba dříve definované funkce. Pokud není žádná dříve definované funkce, vrátí **NULL**.

## <a name="remarks"></a>Poznámky

Nepoužívejte tuto funkci; Místo toho použijte **_rtc_seterrorfuncw –**. Ho je uchována pouze z důvodů zpětné kompatibility.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_RTC_SetErrorFunc**|\<rtcapi.h >|

Další informace najdete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Viz také

[_CrtDbgReport, _CrtDbgReportW](crtdbgreport-crtdbgreportw.md)<br/>
[Kontrola chyb za běhu](../../c-runtime-library/run-time-error-checking.md)<br/>
