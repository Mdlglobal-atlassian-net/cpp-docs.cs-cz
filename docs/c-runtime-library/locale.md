---
title: Národní prostředí
ms.date: 04/11/2018
f1_keywords:
- c.international
helpviewer_keywords:
- localization, locale
- country information
- language information routines
- setlocale function
- locale routines
ms.assetid: 442f8112-9288-44d7-be3c-15d22652093a
ms.openlocfilehash: 89ff4b694137c7002ecb5f6a844c75ab403e6e2f
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57744379"
---
# <a name="locale"></a>Národní prostředí

*Národní prostředí* odkazuje na zemi/oblast a jazykové nastavení, které můžete použít k přizpůsobení aplikace. Některé kategorie závislé na národním prostředí patří formáty zobrazení pro data a peněžní hodnoty. Další informace najdete v tématu [kategorie národního prostředí](../c-runtime-library/locale-categories.md).

Použití [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) funkce změnit nebo dotazovat některé nebo všechny aktuální informace národního prostředí programu nebo vlákno při použití funkce bez **_l** příponu. Funkce se **_l** přípona se používá parametr národního prostředí předaného své informace o národních prostředích během provádění této konkrétní funkce. K vytvoření národního prostředí pro použití s funkcí s **_l** přípony, použijte [_create_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md). Chcete-li uvolnit toto národní prostředí, použijte [_free_locale –](../c-runtime-library/reference/free-locale.md). Chcete-li získat aktuální národní prostředí, použijte [_get_current_locale –](../c-runtime-library/reference/get-current-locale.md).

Použití [_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md) k řízení toho, jestli každé vlákno má svůj vlastní národní prostředí nebo sdílet stejné národní prostředí všech vláken v programu. Další informace najdete v tématu [národní prostředí a kódové stránky](../text/locales-and-code-pages.md).

Bezpečnější verze funkcí v následující tabulce jsou k dispozici, indikován **_Malá** příponu ("bezpečné"). Další informace najdete v tématu [funkce zabezpečení v CRT](../c-runtime-library/security-features-in-the-crt.md).

## <a name="locale-dependent-routines"></a>Rutiny závislé na národním prostředí

|Rutina|Použití|**setlocale** závislost na nastavení kategorie|
|-------------|---------|---------------------------------------------|
|[atof, _atof_l, _wtof, _wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|Převod znaků na hodnotu s plovoucí desetinnou čárkou|**LC_NUMERIC**|
|[atoi, _atoi_l, _wtoi, _wtoi_l](../c-runtime-library/reference/atoi-atoi-l-wtoi-wtoi-l.md)|Převod znaků na celočíselnou hodnotu|**LC_NUMERIC**|
|[_atoi64, _atoi64_l, _wtoi64, _wtoi64_l](../c-runtime-library/reference/atoi64-atoi64-l-wtoi64-wtoi64-l.md)|Převod znaků na 64bitové celé číslo|**LC_NUMERIC**|
|[atol, _atol_l, _wtol, _wtol_l](../c-runtime-library/reference/atol-atol-l-wtol-wtol-l.md)|Převod na dlouhou hodnotu znaku|**LC_NUMERIC**|
|[_atodbl, _atodbl_l, _atoldbl, _atoldbl_l, _atoflt, _atoflt_l](../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)|Převod znaků na hodnotu double long|**LC_NUMERIC**|
|[is Routines](../c-runtime-library/is-isw-routines.md)|Test pro konkrétní podmínky zadané celé číslo.|**LC_CTYPE**|
|[isleadbyte, _isleadbyte_l](../c-runtime-library/reference/isleadbyte-isleadbyte-l.md)|Test pro vedoucí bajt|**LC_CTYPE**|
|[localeconv](../c-runtime-library/reference/localeconv.md)|Přečtěte si příslušné hodnoty pro formátování číselných množství|`LC_MONETARY, LC_NUMERIC`|
|[MB_CUR_MAX](../c-runtime-library/mb-cur-max.md)|Maximální délka v bajtech libovolného vícebajtového znaku v aktuální národní prostředí (– makro definované v STDLIB. H)|**LC_CTYPE**|
|[_mbccpy, _mbccpy_l](../c-runtime-library/reference/mbccpy-mbccpy-l.md),[_mbccpy_s, _mbccpy_s_l](../c-runtime-library/reference/mbccpy-s-mbccpy-s-l.md)|Zkopírujte jeden vícebajtový znak|**LC_CTYPE**|
|[_mbclen, mblen, _mblen_l](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)|Ověření a vrátí počet bajtů ve vícebajtové znaky|**LC_CTYPE**|
|[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)|Pro vícebajtové znakové řetězce: ověření každý znak v řetězci; Vrátí délku řetězce|**LC_CTYPE**|
|[mbstowcs, _mbstowcs_l](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md),[mbstowcs_s, _mbstowcs_s_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|Převod sekvence vícebajtových znaků na odpovídající pořadí širokých znaků|**LC_CTYPE**|
|[mbtowc, _mbtowc_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)|Převést vícebajtový znak na odpovídající široké znaky|**LC_CTYPE**|
|[printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) funkce|Zapíše formátovaný výstup|**LC_NUMERIC** (Určuje výstup Číselná soustava znaků)|
|[scanf –](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) funkce|Čtení formátovaný vstup|**LC_NUMERIC** (určuje rozpoznávání znaku radix)|
|[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)|Vyberte národní prostředí pro program|Nelze použít|
|[strcoll, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|Porovnání dvou řetězců znaků|**LC_COLLATE**|
|[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)|Porovná dva řetězce bez ohledu na případ|**LC_CTYPE**|
|[_stricoll, _wcsicoll, _mbsicoll, _stricoll_l, _wcsicoll_l, _mbsicoll_l](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|Porovnání znaků dva řetězce (malých písmen)|**LC_COLLATE**|
|[_strncoll, _wcsncoll, _mbsncoll, _strncoll_l, _wcsncoll_l, _mbsncoll_l](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|Porovnání první **n** znaky ze dvou řetězců|**LC_COLLATE**|
|[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)|Porovnání znaků dva řetězce bez ohledu na případ.|**LC_CTYPE**|
|[_strnicoll, _wcsnicoll, _mbsnicoll, _strnicoll_l, _wcsnicoll_l, _mbsnicoll_l](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|Porovnání první **n** znaky ze dvou řetězců (malých písmen)|**LC_COLLATE**|
|[strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)|Zadaný formát hodnoty data a času podle **formátu** argument|**LC_TIME**|
|[_strlwr, _wcslwr, _mbslwr, _strlwr_l, _wcslwr_l, _mbslwr_l](../c-runtime-library/reference/strlwr-wcslwr-mbslwr-strlwr-l-wcslwr-l-mbslwr-l.md),[_strlwr_s, _strlwr_s_l, _mbslwr_s, _mbslwr_s_l, _wcslwr_s, _wcslwr_s_l](../c-runtime-library/reference/strlwr-s-strlwr-s-l-mbslwr-s-mbslwr-s-l-wcslwr-s-wcslwr-s-l.md)|Převést na místě, velká písmena v dle řetězce na malá písmena|**LC_CTYPE**|
|[strtod, _strtod_l, wcstod, _wcstod_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)|Převod řetězce znaků na **double** hodnota|**LC_NUMERIC** (určuje rozpoznávání znaku radix)|
|[strtol, wcstol, _strtol_l, _wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)|Převod řetězce znaků na **dlouhé** hodnota|**LC_NUMERIC** (určuje rozpoznávání znaku radix)|
|[strtoul, _strtoul_l, wcstoul, _wcstoul_l](../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)|Převod řetězce znaků na dlouhou hodnotu bez znaménka|**LC_NUMERIC** (určuje rozpoznávání znaku radix)|
|[_strupr, _strupr_l, _mbsupr, _mbsupr_l, _wcsupr_l, _wcsupr](../c-runtime-library/reference/strupr-strupr-l-mbsupr-mbsupr-l-wcsupr-l-wcsupr.md),[_strupr_s, _strupr_s_l, _mbsupr_s, _mbsupr_s_l, _wcsupr_s, _wcsupr_s_l](../c-runtime-library/reference/strupr-s-strupr-s-l-mbsupr-s-mbsupr-s-l-wcsupr-s-wcsupr-s-l.md)|Převést na místě každé malé písmeno v řetězci na velká písmena|**LC_CTYPE**|
|[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)|Transformace řetězce do formuláře by v kolaci podle národního prostředí|**LC_COLLATE**|
|[ToLower _tolower –, towlower –, _tolower_l –, _towlower_l –](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md),[_mbctolower – _mbctolower_l –, _mbctoupper – _mbctoupper_l –](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|Převést na zadaný znak na odpovídající znak malé písmeno|**LC_CTYPE**|
|[ToUpper _toupper –, towupper –, _toupper_l –, _towupper_l –](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md),[_mbctolower – _mbctolower_l –, _mbctoupper – _mbctoupper_l –](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|Převést na zadaný znak na odpovídající velké písmeno|**LC_CTYPE**|
|[wcstombs, _wcstombs_l](../c-runtime-library/reference/wcstombs-wcstombs-l.md),[wcstombs_s, _wcstombs_s_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|Převod sekvence širokých znaků na odpovídající sekvence vícebajtových znaků|**LC_CTYPE**|
|[wctomb, _wctomb_l](../c-runtime-library/reference/wctomb-wctomb-l.md),[wctomb_s, _wctomb_s_l](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|Převést na odpovídající vícebajtový znak širokého znaku|**LC_CTYPE**|

> [!NOTE]
> Pro vícebajtové rutiny, musí být ekvivalentní k nastavení s národního prostředí je vícebajtová znaková stránka [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md). [_setmbcp](../c-runtime-library/reference/setmbcp.md), s argumentem **_MB_CP_LOCALE** díky vícebajtové znakové stránce stejné jako **setlocale** znakovou stránku.

## <a name="see-also"></a>Viz také:

[Internacionalizace](../c-runtime-library/internationalization.md)<br/>
[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
