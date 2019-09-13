---
title: _RTC_SetErrorFunc
ms.date: 11/04/2016
api_name:
- _RTC_SetErrorFunc
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- RTC_SetErrorFunc
- _RTC_SetErrorFunc
helpviewer_keywords:
- RTC_SetErrorFunc function
- _RTC_SetErrorFunc function
ms.assetid: b2292722-0d83-4092-83df-3d5b19880666
ms.openlocfilehash: 6b173dd9af9fe11146341468c44a0abc10ce90bc
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949017"
---
# <a name="_rtc_seterrorfunc"></a>_RTC_SetErrorFunc

Určí funkci jako obslužnou rutinu pro kontroly chyb za běhu generování sestav (RTCs). Tato funkce je zastaralá. místo toho použijte **_RTC_SetErrorFuncW** .

## <a name="syntax"></a>Syntaxe

```C
_RTC_error_fn _RTC_SetErrorFunc(
   _RTC_error_fn function
);
```

### <a name="parameters"></a>Parametry

*slouží*<br/>
Adresa funkce, která bude zpracovávat kontroly chyb za běhu.

## <a name="return-value"></a>Návratová hodnota

Dříve definovaná funkce Error. Pokud není k dispozici žádná dříve definovaná funkce, vrátí **hodnotu null**.

## <a name="remarks"></a>Poznámky

Nepoužívejte tuto funkci. místo toho použijte **_RTC_SetErrorFuncW**. Je zachována pouze z důvodu zpětné kompatibility.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_RTC_SetErrorFunc**|\<rtcapi.h>|

Další informace najdete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Viz také:

[_CrtDbgReport, _CrtDbgReportW](crtdbgreport-crtdbgreportw.md)<br/>
[Kontrola chyb za běhu](../../c-runtime-library/run-time-error-checking.md)<br/>
