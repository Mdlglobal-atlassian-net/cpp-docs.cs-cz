---
title: Převod dat
ms.date: 03/21/2018
f1_keywords:
- c.conversions
helpviewer_keywords:
- data conversion routines [C++]
- converting data
ms.assetid: b15b5268-7467-49f1-bf95-5299b598f94c
ms.openlocfilehash: 070949d064d1835970c1f671cf0e5337342fdca1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50547386"
---
# <a name="data-conversion"></a>Převod dat

Tyto rutiny převodu dat z jeden formulář do jiného. Tyto rutiny obvykle provádějí rychleji než převody, které můžete například napsat. Každá rutina, která začíná *k* předpona je implementována jako funkce a jako makro. Zobrazit [výběru mezi funkcemi a makry](../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md) informace o volbě implementace.

## <a name="data-conversion-routines"></a>Rutiny převodu dat

|Rutina|Použití|
|-------------|---------|
|[Abs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|Najít absolutní hodnotu celého čísla|
|[atof – _atof_l –](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|Převod řetězce na **plovoucí desetinnou čárkou**|
|[atoi, _atoi_l](../c-runtime-library/reference/atoi-atoi-l-wtoi-wtoi-l.md)|Převod řetězce na **int**|
|[_atoi64, _atoi64_l](../c-runtime-library/reference/atoi64-atoi64-l-wtoi64-wtoi64-l.md)|Převod řetězce na **__int64** nebo **long long**|
|[Atol – _atol_l –](../c-runtime-library/reference/atol-atol-l-wtol-wtol-l.md)|Převod řetězce na **dlouhý**|
|[c16rtomb c32rtomb](../c-runtime-library/reference/c16rtomb-c32rtomb1.md)|Převést na ekvivalentní vícebajtové znakové kódování UTF-16 nebo UTF-32 znaků|
|[_ecvt](../c-runtime-library/reference/ecvt.md), [_ecvt_s](../c-runtime-library/reference/ecvt-s.md)|Převést **double** řetězce zadané délky|
|[_fcvt](../c-runtime-library/reference/fcvt.md), [_fcvt_s](../c-runtime-library/reference/fcvt-s.md)|Převést **double** na řetězec s zadaný počet číslic za desítkové bodu|
|[_gcvt](../c-runtime-library/reference/gcvt.md), [_gcvt_s](../c-runtime-library/reference/gcvt-s.md)|Převést **double** číslo na řetězec, řetězec uložit ve vyrovnávací paměti|
|[_itoa, _ltoa, _ultoa, _i64toa, _ui64toa, _itow, _ltow, ultow, _i64tow, _ui64tow](../c-runtime-library/reference/itoa-itow.md), [_itoa_s, _ltoa_s, _ultoa_s, _i64toa_s, _ui64toa_s, _itow_s, _ltow_s, _ultow_s, _i64tow_s, _ui64tow_s](../c-runtime-library/reference/itoa-s-itow-s.md)|Převést na řetězec typy celých čísel|
|[Praktická cvičení](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|Najít absolutní hodnota **dlouhé** celé číslo|
|[llabs –](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|Najít absolutní hodnota **long long** celé číslo|
|[_mbbtombc, _mbbtombc_l](../c-runtime-library/reference/mbbtombc-mbbtombc-l.md)|Převést na odpovídající 2 bajt vícebajtového znaku 1 bajt vícebajtového znaku.|
|[_mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l](../c-runtime-library/reference/mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)|Převést znak Japonsko průmyslové normy (JIS) na znak Japan Microsoft (JMS)|
|[_mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l](../c-runtime-library/reference/mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)|Převést JMS znak JIS na znak|
|[_mbctohira, _mbctohira_l, _mbctokata, _mbctokata_l](../c-runtime-library/reference/mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)|Převést vícebajtový znak na 1bajtových hiragana kódu|
|[_mbctohira, _mbctohira_l, _mbctokata, _mbctokata_l](../c-runtime-library/reference/mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)|Převést vícebajtový znak na 1bajtových katakana kódu|
|[_mbctombb, _mbctombb_l](../c-runtime-library/reference/mbctombb-mbctombb-l.md)|Převést na odpovídající 1 bajt vícebajtového znaku 2 bajt vícebajtového znaku.|
|[mbrtoc16, mbrtoc32](../c-runtime-library/reference/mbrtoc16-mbrtoc323.md)|Převod vícebajtových znaků na ekvivalentní znaků UTF-16 nebo UTF-32|
|[mbstowcs _mbstowcs_l –](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md), [mbstowcs_s _mbstowcs_s_l –](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|Převod sekvence vícebajtových znaků na odpovídající pořadí širokých znaků|
|[mbtowc, _mbtowc_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)|Převést vícebajtový znak na odpovídající široké znaky|
|[strtod, _strtod_l, wcstod, _wcstod_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)|Převod řetězce na **double**|
|[strtol, wcstol, _strtol_l, _wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)|Převod řetězce na **dlouhé** celé číslo|
|[strtoul, _strtoul_l, wcstoul, _wcstoul_l](../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)|Převod řetězce na **unsigned long** celé číslo|
|[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)|Transformace řetězce do by v kolaci formuláře na základě informací specifických pro národní prostředí|
|[toascii, __toascii](../c-runtime-library/reference/toascii-toascii.md)|Převod znaků ASCII kódu||
|[ToLower _tolower –, towlower –, _tolower_l –, _towlower_l –](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md), [_mbctolower – _mbctolower_l –, _mbctoupper – _mbctoupper_l –](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|Testování znaků a převést na malá písmena, pokud aktuálně velká písmena|
|[tolower, _tolower, towlower, _tolower_l, _towlower_l](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md)|Převod znaků na malá písmena bezpodmínečně|[System::String::ToLower](https://msdn.microsoft.com/library/system.string.tolower.aspx)|
|[ToUpper _toupper –, towupper –, _toupper_l –, _towupper_l –](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md), [_mbctolower – _mbctolower_l –, _mbctoupper – _mbctoupper_l –](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|Testování znaků a převést na velká písmena, pokud aktuálně malá písmena|
|[toupper, _toupper, towupper, _toupper_l, _towupper_l](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md)|Převod znaků na velká písmena bezpodmínečně|
|[wcstombs – _wcstombs_l –](../c-runtime-library/reference/wcstombs-wcstombs-l.md), [wcstombs_s – _wcstombs_s_l –](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|Převod sekvence širokých znaků na odpovídající sekvence vícebajtových znaků|
|[wctomb, _wctomb_l](../c-runtime-library/reference/wctomb-wctomb-l.md), [wctomb_s, _wctomb_s_l](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|Převést na odpovídající vícebajtový znak širokého znaku|
|[_wtof, _wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|Převod řetězce širokého znaku na **double**|
|[_wtoi, _wtoi_l](../c-runtime-library/reference/atoi-atoi-l-wtoi-wtoi-l.md)|Převod řetězce širokého znaku na **int**|
|[_wtoi64, _wtoi64_l](../c-runtime-library/reference/atoi64-atoi64-l-wtoi64-wtoi64-l.md)|Převod řetězce širokého znaku na **__int64** nebo **long long**|
|[_wtol, _wtol_l](../c-runtime-library/reference/atol-atol-l-wtol-wtol-l.md)|Převod řetězce širokého znaku na **dlouhý**|

## <a name="see-also"></a>Viz také:

[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
