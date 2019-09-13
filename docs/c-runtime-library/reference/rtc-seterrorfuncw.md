---
title: _RTC_SetErrorFuncW
ms.date: 11/04/2016
api_name:
- _RTC_SetErrorFuncW
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
- _RTC_SetErrorFuncW
- RTC_SetErrorFuncW
helpviewer_keywords:
- run-time errors
- RTC_SetErrorFuncW function
- _RTC_error_fnW typedef
- _RTC_SetErrorFuncW function
- RTC_error_fnW typedef
ms.assetid: b3e0d71f-1bd3-4c37-9ede-2f638eb3c81a
ms.openlocfilehash: 0d45e5c857e917ca23b62482c64a06314565226e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948968"
---
# <a name="_rtc_seterrorfuncw"></a>_RTC_SetErrorFuncW

Určí funkci jako obslužnou rutinu pro oznamování kontrol chyb za běhu (RTCs).

## <a name="syntax"></a>Syntaxe

```C
_RTC_error_fnW _RTC_SetErrorFuncW(
   _RTC_error_fnW function
);
```

### <a name="parameters"></a>Parametry

*slouží*<br/>
Adresa funkce, která bude zpracovávat kontroly chyb za běhu.

## <a name="return-value"></a>Návratová hodnota

Dříve definovaná chybová funkce; nebo **hodnotu null** , pokud není k dispozici dříve definovaná funkce.

## <a name="remarks"></a>Poznámky

V novém kódu použijte pouze **_RTC_SetErrorFuncW**. **_RTC_SetErrorFunc** je zařazena do knihovny pouze z důvodu zpětné kompatibility.

Zpětné volání **_RTC_SetErrorFuncW** se vztahuje pouze na součást, kterou byl propojen, ale ne globálně.

Ujistěte se, že adresa, kterou předáte do **_RTC_SetErrorFuncW** , je ta, která má platnou funkci pro zpracování chyb.

Pokud byla chyba přiřazena typu-1 pomocí [_RTC_SetErrorType](rtc-seterrortype.md), není volána funkce pro zpracování chyb.

Před voláním této funkce je nutné nejprve zavolat jednu z inicializačních funkcí kontroly chyb v době běhu. Další informace naleznete v tématu [použití kontrol za běhu bez běhové knihovny jazyka C](/visualstudio/debugger/using-run-time-checks-without-the-c-run-time-library).

**_RTC_error_fnW** je definována takto:

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

*errorType*<br/>
Typ chyby, který je určen parametrem [_RTC_SetErrorType](rtc-seterrortype.md).

*Bitmap*<br/>
Zdrojový soubor, kde došlo k chybě, nebo hodnotu null, pokud nejsou k dispozici žádné informace o ladění.

*číslo řádku*<br/>
Řádek v *souboru filename* , kde došlo k chybě, nebo 0, pokud nejsou k dispozici žádné informace o ladění.

*moduleName*<br/>
Název knihovny DLL nebo spustitelného souboru, kde došlo k chybě.

*format*<br/>
printf styl řetězce pro zobrazení chybové zprávy pomocí zbývajících parametrů. První argument VA_ARGLIST je číslo chyby RTC, ke které došlo.

Příklad, který ukazuje, jak používat **_RTC_error_fnW**, najdete v tématu věnovaném [přizpůsobení nativních kontrol za běhu](/visualstudio/debugger/native-run-time-checks-customization).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_RTC_SetErrorFuncW**|\<rtcapi.h>|

Další informace najdete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Viz také:

[_CrtDbgReport, _CrtDbgReportW](crtdbgreport-crtdbgreportw.md)<br/>
[Kontrola chyb za běhu](../../c-runtime-library/run-time-error-checking.md)<br/>
