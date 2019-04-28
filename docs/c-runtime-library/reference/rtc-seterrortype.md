---
title: _RTC_SetErrorType
ms.date: 11/04/2016
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
helpviewer_keywords:
- run-time errors
- RTC_SetErrorType function
- _RTC_SetErrorType function
ms.assetid: f5f99be7-d357-4b11-b8f5-ddd3428f2b06
ms.openlocfilehash: 022079bd199477c8bca92e853ed66879c96428db
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62357132"
---
# <a name="rtcseterrortype"></a>_RTC_SetErrorType

Přidruží k chybě, která zjistí kontroly chyb za běhu (RTCs) s typem. Vaše obslužná rutina chyb zpracovává jak do výstupního chyby zadaného typu.

## <a name="syntax"></a>Syntaxe

```C
int _RTC_SetErrorType(
   _RTC_ErrorNumber errnum,
   int ErrType
);
```

### <a name="parameters"></a>Parametry

*errnum*<br/>
Číslo mezi 0 a 1 menší než hodnota vrácená [_rtc_numerrors –](rtc-numerrors.md).

*ErrType*<br/>
Hodnota pro přiřazení k tomuto *errnum*. Například můžete použít **_CRT_ERROR**. Pokud používáte **_CrtDbgReport** jako vaše obslužná rutina chyb *ErrType* může být pouze jeden symboly definované v [_CrtSetReportMode](crtsetreportmode.md). Pokud máte vlastní obslužnou rutinu chyb ([_RTC_SetErrorFunc](rtc-seterrorfunc.md)), můžete mít kolik *ErrType*se označují jako tam *errnum*s.

*ErrType* _RTC_ERRTYPE_IGNORE má zvláštní význam **_CrtSetReportMode**; tato chyba je ignorována.

## <a name="return-value"></a>Návratová hodnota

Předchozí hodnota pro typ chyby *typ*.

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení jsou všechny chyby nastavené *ErrType* = 1, která odpovídá **_CRT_ERROR**. Další informace o chybě výchozí typy, jako **_CRT_ERROR**, naleznete v tématu [_CrtDbgReport](crtdbgreport-crtdbgreportw.md).

Předtím, než bude možné volat tuto funkci, musíte nejdřív voláním funkce inicializace Kontrola chyb za běhu. Zobrazit [pomocí kontrol za běhu bez běhové knihovny jazyka C](/visualstudio/debugger/using-run-time-checks-without-the-c-run-time-library)

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_RTC_SetErrorType**|\<rtcapi.h>|

Další informace najdete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Viz také:

[_RTC_GetErrDesc](rtc-geterrdesc.md)<br/>
[Kontrola chyb za běhu](../../c-runtime-library/run-time-error-checking.md)<br/>
