---
title: Převod dat | Microsoft Docs
ms.custom: ''
ms.date: 03/21/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- c.conversions
dev_langs:
- C++
helpviewer_keywords:
- data conversion routines [C++]
- converting data
ms.assetid: b15b5268-7467-49f1-bf95-5299b598f94c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a0260ebe37e0656f2078b247017d9f02ccc88474
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32392442"
---
# <a name="data-conversion"></a>Převod dat

Tyto rutiny převodu dat z jednoho formátu do druhého. Obecně tyto rutiny spouštět rychleji, než převody, které může zapsat. Každou rutinu, který začíná *k* předpona je implementovaný jako funkce a jako makra. V tématu [výběru mezi funkcemi a makry](../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md) informace o volbě implementace.

## <a name="data-conversion-routines"></a>Rutiny převodu dat

|Rutina|Použití|
|-------------|---------|
|[Abs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|Najít absolutní hodnota celé číslo|
|[atof –, _atof_l –](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|Převést řetězec na **float**|
|[atoi, _atoi_l](../c-runtime-library/reference/atoi-atoi-l-wtoi-wtoi-l.md)|Převést řetězec na **int**|
|[_atoi64, _atoi64_l](../c-runtime-library/reference/atoi64-atoi64-l-wtoi64-wtoi64-l.md)|Převést řetězec na **__int64** nebo **dlouho dlouho**|
|[Atol –, _atol_l –](../c-runtime-library/reference/atol-atol-l-wtol-wtol-l.md)|Převést řetězec na **dlouho**|
|[c16rtomb c32rtomb](../c-runtime-library/reference/c16rtomb-c32rtomb1.md)|Převést UTF-16 nebo UTF-32 znaků na ekvivalentní vícebajtových znaků|
|[_ecvt](../c-runtime-library/reference/ecvt.md), [_ecvt_s](../c-runtime-library/reference/ecvt-s.md)|Převést **dvojité** řetězec o zadané délce|
|[_fcvt](../c-runtime-library/reference/fcvt.md), [_fcvt_s](../c-runtime-library/reference/fcvt-s.md)|Převést **dvojité** na řetězec s zadaný počet číslic za desetinnou bodu|
|[_gcvt](../c-runtime-library/reference/gcvt.md), [_gcvt_s](../c-runtime-library/reference/gcvt-s.md)|Převést **dvojité** čísla na řetězec; řetězec uložit ve vyrovnávací paměti|
|[_itoa, _ltoa, _ultoa, _i64toa, _ui64toa, _itow, _ltow, ultow, _i64tow, _ui64tow](../c-runtime-library/reference/itoa-itow.md), [_itoa_s, _ltoa_s, _ultoa_s, _i64toa_s, _ui64toa_s, _itow_s, _ltow_s, _ultow_s, _i64tow_s, _ui64tow_s](../c-runtime-library/reference/itoa-s-itow-s.md)|Převést typy celých čísel na řetězec|
|[Labs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|Najít absolutní hodnotu **dlouho** celé číslo|
|[llabs –](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|Najít absolutní hodnotu **dlouho dlouho** celé číslo|
|[_mbbtombc, _mbbtombc_l](../c-runtime-library/reference/mbbtombc-mbbtombc-l.md)|Převod vícebajtových znaků 1bajtový na odpovídající 2bajtová vícebajtových znaků|
|[_mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l](../c-runtime-library/reference/mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)|Převést Japonsko oborový Standard (JIS) znak znak Japonsko Microsoft (JMS)|
|[_mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l](../c-runtime-library/reference/mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)|Převést JMS znaků JIS znak|
|[_mbctohira, _mbctohira_l, _mbctokata, _mbctokata_l](../c-runtime-library/reference/mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)|Převod vícebajtových znaků hiragana 1bajtový kódu|
|[_mbctohira, _mbctohira_l, _mbctokata, _mbctokata_l](../c-runtime-library/reference/mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)|Převod vícebajtových znaků katakana 1bajtový kódu|
|[_mbctombb, _mbctombb_l](../c-runtime-library/reference/mbctombb-mbctombb-l.md)|Převod vícebajtových znaků 2bajtová na odpovídající 1bajtový vícebajtových znaků|
|[mbrtoc16, mbrtoc32](../c-runtime-library/reference/mbrtoc16-mbrtoc323.md)|Převod vícebajtových znaků na ekvivalentní UTF-16 nebo UTF-32 znaků|
|[mbstowcs –, _mbstowcs_l –](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md), [mbstowcs_s –, _mbstowcs_s_l –](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|Převést pořadí více-bajtové znaky na odpovídající pořadí široké znaky|
|[mbtowc, _mbtowc_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)|Převést na odpovídající široká znaková vícebajtových znaků|
|[strtod, _strtod_l, wcstod, _wcstod_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)|Převést řetězec na **double**|
|[strtol, wcstol, _strtol_l, _wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)|Převést řetězec na **dlouho** celé číslo|
|[strtoul, _strtoul_l, wcstoul, _wcstoul_l](../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)|Převést řetězec na **nepodepsané dlouho** celé číslo|
|[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)|Transformace řetězců do řazená formulář založený na informace specifické pro národní prostředí|
|[toascii, __toascii](../c-runtime-library/reference/toascii-toascii.md)|Převod znaků ASCII kódu||
|[ToLower, _tolower –, towlower –, _tolower_l –, _towlower_l –](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md), [_mbctolower –, _mbctolower_l –, _mbctoupper –, _mbctoupper_l –](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|Testování znaků a převeden na malá písmena, pokud je aktuálně velká písmena|
|[tolower, _tolower, towlower, _tolower_l, _towlower_l](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md)|Převést znak, který má bezpodmínečně malá písmena|[System::String::ToLower](https://msdn.microsoft.com/en-us/library/system.string.tolower.aspx)|
|[ToUpper, _toupper –, towupper –, _toupper_l –, _towupper_l –](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md), [_mbctolower –, _mbctolower_l –, _mbctoupper –, _mbctoupper_l –](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|Testování znaků a převeden na velká písmena, pokud je aktuálně malá písmena|
|[toupper, _toupper, towupper, _toupper_l, _towupper_l](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md)|Převést znak na velká písmena bezpodmínečně|
|[wcstombs –, _wcstombs_l –](../c-runtime-library/reference/wcstombs-wcstombs-l.md), [wcstombs_s –, _wcstombs_s_l –](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|Převést na odpovídající pořadí více-bajtové znaky pořadí široké znaky|
|[wctomb, _wctomb_l](../c-runtime-library/reference/wctomb-wctomb-l.md), [wctomb_s, _wctomb_s_l](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|Převést široká znaková na odpovídající vícebajtových znaků|
|[_wtof, _wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|Převést řetězec široká charakterová **double**|
|[_wtoi, _wtoi_l](../c-runtime-library/reference/atoi-atoi-l-wtoi-wtoi-l.md)|Převést řetězec široká charakterová **int**|
|[_wtoi64, _wtoi64_l](../c-runtime-library/reference/atoi64-atoi64-l-wtoi64-wtoi64-l.md)|Převést řetězec široká charakterová **__int64** nebo **dlouho dlouho**|
|[_wtol, _wtol_l](../c-runtime-library/reference/atol-atol-l-wtol-wtol-l.md)|Převést řetězec široká charakterová **dlouho**|

## <a name="see-also"></a>Viz také

[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
