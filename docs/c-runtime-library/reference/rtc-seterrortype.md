---
title: _RTC_SetErrorType
ms.date: 11/04/2016
api_name:
- _RTC_SetErrorType
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
- RTC_SetErrorType
- _RTC_SetErrorType
helpviewer_keywords:
- run-time errors
- RTC_SetErrorType function
- _RTC_SetErrorType function
ms.assetid: f5f99be7-d357-4b11-b8f5-ddd3428f2b06
ms.openlocfilehash: 6c1eff5920931aa3b72bf3dbc6232c371828b16a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948926"
---
# <a name="_rtc_seterrortype"></a>_RTC_SetErrorType

Přidruží chybu, která je zjištěna při kontrolách běhových chyb (RTCs) s typem. Vaše obslužná rutina chyb zpracovává výstup chyb zadaného typu.

## <a name="syntax"></a>Syntaxe

```C
int _RTC_SetErrorType(
   _RTC_ErrorNumber errnum,
   int ErrType
);
```

### <a name="parameters"></a>Parametry

*errnum*<br/>
Číslo od 0 do 1 menší než hodnota vrácená funkcí [_RTC_NumErrors](rtc-numerrors.md).

*ErrType*<br/>
Hodnota, která se má přiřadit k tomuto *errnum*. Můžete například použít **_CRT_ERROR**. Pokud používáte **_CrtDbgReport** jako obslužnou rutinu chyb, *ErrType* může být pouze jeden ze symbolů definovaných v [_CrtSetReportMode](crtsetreportmode.md). Máte-li vlastní obslužnou rutinu chyb ([_RTC_SetErrorFunc](rtc-seterrorfunc.md)), můžete mít tolik *ErrType*, kolik je *errnum*s.

*ERRTYPE* _RTC_ERRTYPE_IGNORE má zvláštní význam pro **_CrtSetReportMode**; Tato chyba je ignorována.

## <a name="return-value"></a>Návratová hodnota

Předchozí hodnota *typu*typu chyby.

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení jsou všechny chyby nastavené na *ErrType* = 1, což odpovídá **_CRT_ERROR**. Další informace o výchozích typech chyb, jako je **_CRT_ERROR**, naleznete v tématu [_CrtDbgReport](crtdbgreport-crtdbgreportw.md).

Před voláním této funkce je nutné nejprve zavolat jednu z inicializačních funkcí kontroly chyb za běhu; viz [použití kontrol za běhu bez běhové knihovny jazyka C](/visualstudio/debugger/using-run-time-checks-without-the-c-run-time-library) .

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_RTC_SetErrorType**|\<rtcapi.h>|

Další informace najdete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Viz také:

[_RTC_GetErrDesc](rtc-geterrdesc.md)<br/>
[Kontrola chyb za běhu](../../c-runtime-library/run-time-error-checking.md)<br/>
