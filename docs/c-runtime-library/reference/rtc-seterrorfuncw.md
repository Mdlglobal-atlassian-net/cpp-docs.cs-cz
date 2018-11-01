---
title: _RTC_SetErrorFuncW
ms.date: 11/04/2016
apiname:
- _RTC_SetErrorFuncW
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
- _RTC_SetErrorFuncW
- RTC_SetErrorFuncW
helpviewer_keywords:
- run-time errors
- RTC_SetErrorFuncW function
- _RTC_error_fnW typedef
- _RTC_SetErrorFuncW function
- RTC_error_fnW typedef
ms.assetid: b3e0d71f-1bd3-4c37-9ede-2f638eb3c81a
ms.openlocfilehash: 03e9f540a215550a698700f28e5722b33b119149
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50482693"
---
# <a name="rtcseterrorfuncw"></a>_RTC_SetErrorFuncW

Označí funkci jako obslužnou rutinu pro zasílání zpráv o chybách kontroly chyb za běhu (RTCs).

## <a name="syntax"></a>Syntaxe

```C
_RTC_error_fnW _RTC_SetErrorFuncW(
   _RTC_error_fnW function
);
```

### <a name="parameters"></a>Parametry

*– funkce*<br/>
Adresa funkce, která bude zpracovávat kontroly chyb za běhu.

## <a name="return-value"></a>Návratová hodnota

Dříve definované chybovou funkci; nebo **NULL** Pokud neexistuje žádná dříve definované funkce.

## <a name="remarks"></a>Poznámky

V novém kódu používat jenom **_RTC_SetErrorFuncW**. **_RTC_SetErrorFunc** pouze součástí knihovny z důvodu zpětné kompatibility.

**_RTC_SetErrorFuncW** zpětného volání platí pouze pro komponentu, která se připojují, ale ne globálně.

Ujistěte se, že na adresu, kterou můžete předat **_RTC_SetErrorFuncW** je, že platný chyby zpracování funkce.

Pokud k chybě byl přiřazen typ-1 s použitím [_RTC_SetErrorType](rtc-seterrortype.md), chyba zpracování funkce není volána.

Než bude možné volat tuto funkci, nejprve je třeba volat jednu z funkcí inicializace Kontrola chyb za běhu. Další informace najdete v tématu [použití knihovny Run-Time kontroluje bez the C Run-Time](/visualstudio/debugger/using-run-time-checks-without-the-c-run-time-library).

**_RTC_error_fnW** je definovaná následujícím způsobem:

```cpp
typedef int (__cdecl * _RTC_error_fnW)(
    int errorType,
    const wchar_t * filename,
    int linenumber,
    const wchar_t * moduleName,
    const wchar_t * format,
    ... );
```

kde:

*ErrorType.*<br/>
Typ chyby, která je určená [_RTC_SetErrorType](rtc-seterrortype.md).

*Název souboru*<br/>
Zdrojový soubor, ve kterém došlo k chybě, nebo hodnota null, pokud nejsou dostupné žádné ladicí informace.

*Číslo řádku*<br/>
Na řádku *filename* kde došlo k selhání, nebo 0, pokud nejsou dostupné žádné ladicí informace.

*Název modulu:*<br/>
Knihovna DLL nebo název spustitelného souboru, kde došlo k chybě.

*Formát*<br/>
řetězec ve stylu printf zobrazíte chybovou zprávu, pomocí zbývajících parametrů. Prvním argumentem funkce VA_ARGLIST je číslo RTC chyby, ke které došlo.

Příklad, který ukazuje způsob použití **_RTC_error_fnW**, naleznete v tématu [přizpůsobení nativní kontroly za běhu](/visualstudio/debugger/native-run-time-checks-customization).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_RTC_SetErrorFuncW**|\<rtcapi.h >|

Další informace najdete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Viz také:

[_CrtDbgReport, _CrtDbgReportW](crtdbgreport-crtdbgreportw.md)<br/>
[Kontrola chyb za běhu](../../c-runtime-library/run-time-error-checking.md)<br/>
