---
title: _Rtc_seterrorfuncw – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- run-time errors
- RTC_SetErrorFuncW function
- _RTC_error_fnW typedef
- _RTC_SetErrorFuncW function
- RTC_error_fnW typedef
ms.assetid: b3e0d71f-1bd3-4c37-9ede-2f638eb3c81a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cf610316c504e61d56556a20797f55d2906bca27
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="rtcseterrorfuncw"></a>_RTC_SetErrorFuncW

Funkce označí jako obslužná rutina pro vytváření sestav Kontrola chyb za běhu (RTCs).

## <a name="syntax"></a>Syntaxe

```C
_RTC_error_fnW _RTC_SetErrorFuncW(
   _RTC_error_fnW function
);
```

### <a name="parameters"></a>Parametry

*Funkce*<br/>
Adresa funkce, která bude zpracovávat Kontrola chyb za běhu.

## <a name="return-value"></a>Návratová hodnota

Funkce dříve definovaném chyba; nebo **NULL** Pokud není žádná dříve definované funkce.

## <a name="remarks"></a>Poznámky

V nový kód, použijte pouze **_rtc_seterrorfuncw –**. **_Rtc_seterrorfunc –** je pouze součástí knihovny z důvodu zpětné kompatibility.

**_Rtc_seterrorfuncw –** zpětné volání se vztahuje pouze na jiné součásti, která byla propojena, ale není globálně.

Ujistěte se, že na adresu, kterou předáte **_rtc_seterrorfuncw –** je, že platná chyba zpracování funkce.

Pokud k chybě byla přiřazena typu-1 pomocí [_rtc_seterrortype –](rtc-seterrortype.md), není volán zpracování funkce chyb.

Než bude možné volat tuto funkci, nejprve je třeba volat jedna z funkcí běhové chyby – kontrolní inicializace. Další informace najdete v tématu [pomocí Run-Time kontroluje bez C Run-Time knihovny](/visualstudio/debugger/using-run-time-checks-without-the-c-run-time-library).

**_Rtc_error_fnw – definice** je definován následujícím způsobem:

> **int – TypeDef (__cdecl \*_rtc_error_fnw – definice) (int** *errorType* **, const wchar_t \***  *filename* **, int***linenumber* **, const wchar_t \***  *moduleName* **, const wchar_t \***  *formátu* **,...);** 

kde:

*errorType* typ chyby, která je zadána [_rtc_seterrortype –](rtc-seterrortype.md).

*Název souboru* zdrojový soubor, kde došlo k chybě, nebo hodnota null, pokud je k dispozici žádné informace o ladění.

*lineNumber* na řádku *filename* kde došlo k chybě, nebo 0, pokud je k dispozici žádné informace o ladění.

*Název modulu* knihovna DLL nebo název spustitelného souboru, kde došlo k chybě.

*Formát* printf styl řetězec k zobrazení chybovou zprávu, pomocí zbývající parametrů. První argument funkce VA_ARGLIST je číslo RTC chyby, které došlo k chybě.

Pro příklad, který ukazuje způsob použití **_rtc_error_fnw – definice**, najdete v části [nativní Run-Time kontroluje přizpůsobení](/visualstudio/debugger/native-run-time-checks-customization).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_RTC_SetErrorFuncW**|\<rtcapi.h >|

Další informace najdete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Viz také

[_CrtDbgReport, _CrtDbgReportW](crtdbgreport-crtdbgreportw.md)<br/>
[Kontrola chyb za běhu](../../c-runtime-library/run-time-error-checking.md)<br/>
