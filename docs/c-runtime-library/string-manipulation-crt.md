---
title: Zacházení s řetězci (CRT)
ms.date: 11/04/2016
f1_keywords:
- c.strings
helpviewer_keywords:
- strings [C++], manipulating
- string manipulation
- manipulating strings
ms.assetid: 6545861a-59e7-408d-9d29-2ec9134fc91a
ms.openlocfilehash: fce14ff3e7cd83be0414ccf3e9db7ba2171d0ca7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50464867"
---
# <a name="string-manipulation-crt"></a>Zacházení s řetězci (CRT)

Tyto rutiny pracovat zakončený hodnotou null jednobajtový znak širokoznaké a vícebajtové znakové řetězce. Použití rutin zacházení s vyrovnávací pamětí, je popsáno v [zacházení s vyrovnávací pamětí](../c-runtime-library/buffer-manipulation.md), pro práci s poli znaků, které nesmí končit znakem null.

## <a name="string-manipulation-routines"></a>Rutiny zacházení s řetězci

|Rutina|Použití|
|-------------|---------|
|[strcoll – wcscoll –, _mbscoll –, _strcoll_l –, _wcscoll_l –, _mbscoll_l](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md), [_stricoll – _wcsicoll –, _mbsicoll –, _stricoll_l –, _wcsicoll_l, _mbsicoll_l –](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md), [_strncoll – _wcsncoll –, _mbsncoll –, _strncoll_l –, _ wcsncoll_l – _mbsncoll_l –](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md), [_strnicoll – _wcsnicoll –, _mbsnicoll –, _strnicoll_l –, _wcsnicoll_l –, _mbsnicoll_l –](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|Porovná dva řetězce znaků pomocí informací o kódu stránky (**_mbsicoll –** a **_mbsnicoll –** rozlišují velikost písmen)|
|[_strdec, _wcsdec, _mbsdec, _mbsdec_l](../c-runtime-library/reference/strdec-wcsdec-mbsdec-mbsdec-l.md)|Přejít zpět o jeden znak řetězec ukazatele|
|[_strinc, _wcsinc, _mbsinc, _mbsinc_l](../c-runtime-library/reference/strinc-wcsinc-mbsinc-mbsinc-l.md)|Zálohy ukazatel řetězce o jeden znak|
|[_mbsnbcat – _mbsnbcat_l –](../c-runtime-library/reference/mbsnbcat-mbsnbcat-l.md), [_mbsnbcat_s – _mbsnbcat_s_l –](../c-runtime-library/reference/mbsnbcat-s-mbsnbcat-s-l.md)|Připojit, maximálně nejprve *n* bajtů řetězce o jeden znak do jiného|
|[_mbsnbcmp, _mbsnbcmp_l](../c-runtime-library/reference/mbsnbcmp-mbsnbcmp-l.md)|Porovnání první *n* bajtů dvou řetězců znaků|
|[_strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l](../c-runtime-library/reference/strncnt-wcsncnt-mbsnbcnt-mbsnbcnt-l-mbsnccnt-mbsnccnt-l.md)|Vrátí počet bajtů znaku v rámci počet zadaných znaků|
|[_mbsnbcpy _mbsnbcpy_l –](../c-runtime-library/reference/mbsnbcpy-mbsnbcpy-l.md), [_mbsnbcpy_s – _mbsnbcpy_s_l –](../c-runtime-library/reference/mbsnbcpy-s-mbsnbcpy-s-l.md)|Kopírování *n* bajtů řetězce|
|[_mbsnbicmp, _mbsnbicmp_l](../c-runtime-library/reference/mbsnbicmp-mbsnbicmp-l.md)|Porovnání *n* bajtů dva řetězce znaků bez rozlišování případů|
|[_mbsnbset, _mbsnbset_l](../c-runtime-library/reference/mbsnbset-mbsnbset-l.md)|Nastavte nejprve *n* bajtů řetězce znaků na zadaný znak|
|[_strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l](../c-runtime-library/reference/strncnt-wcsncnt-mbsnbcnt-mbsnbcnt-l-mbsnccnt-mbsnccnt-l.md)|Vrátí počet znaků v rámci zadané bajtů|
|[_strnextc, _wcsnextc, _mbsnextc, _mbsnextc_l](../c-runtime-library/reference/strnextc-wcsnextc-mbsnextc-mbsnextc-l.md)|Najít další znak v řetězci|
|[_strninc, _wcsninc, _mbsninc, _mbsninc_l](../c-runtime-library/reference/strninc-wcsninc-mbsninc-mbsninc-l.md)|Ukazatel na řetězec zálohy pomocí *n* znaků|
|[_strspnp, _wcsspnp, _mbsspnp, _mbsspnp_l](../c-runtime-library/reference/strspnp-wcsspnp-mbsspnp-mbsspnp-l.md)|Řetězec, který není v druhém zadaném řetězci zadaný návratový ukazatel na první znak v|
|[_scprintf, _scprintf_l, _scwprintf, _scwprintf_l](../c-runtime-library/reference/scprintf-scprintf-l-scwprintf-scwprintf-l.md)|Vrátí počet znaků v formátovaný řetězec|
|[_snscanf – _snscanf_l –, _snwscanf – _snwscanf_l –](../c-runtime-library/reference/snscanf-snscanf-l-snwscanf-snwscanf-l.md), [_snscanf_s – _snscanf_s_l –, _snwscanf_s – _snwscanf_s_l –](../c-runtime-library/reference/snscanf-s-snscanf-s-l-snwscanf-s-snwscanf-s-l.md)|Čtení formátovaných dat zadané délky ze standardního vstupního proudu.|
|[sscanf – _sscanf_l –, swscanf – _swscanf_l –](../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md), [sscanf_s – _sscanf_s_l –, swscanf_s – _swscanf_s_l –](../c-runtime-library/reference/sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)|Čtení formátovaných dat zadané délky ze standardního vstupního proudu.|
|[sprintf _sprintf_l –, swprintf, _swprintf_l –, \__swprintf_l –](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md), [sprintf_s – _sprintf_s_l –, swprintf_s – _swprintf_s_l –](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md), [_sprintf_p, _sprintf_p_l, _swprintf_p, _swprintf_p_l](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)|Zapište formátovaná data do řetězce|
|[strcat – wcscat –, _mbscat –](../c-runtime-library/reference/strcat-wcscat-mbscat.md), [strcat_s wcscat_s –, _mbscat_s –](../c-runtime-library/reference/strcat-s-wcscat-s-mbscat-s.md)|Připojit jeden řetězec do druhého|
|[strchr, wcschr, _mbschr, _mbschr_l](../c-runtime-library/reference/strchr-wcschr-mbschr-mbschr-l.md)|Najít první výskyt zadaného znaku v řetězci|
|[strcmp, wcscmp, _mbscmp](../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)|Porovnání dvou řetězců|[System::String::CompareOrdinal](https://msdn.microsoft.com/library/system.string.compareordinal.aspx)|
|[strcoll – wcscoll –, _mbscoll –, _strcoll_l –, _wcscoll_l –, _mbscoll_l](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md), [_stricoll – _wcsicoll –, _mbsicoll –, _stricoll_l –, _wcsicoll_l, _mbsicoll_l –](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md), [_strncoll – _wcsncoll –, _mbsncoll –, _strncoll_l –, _ wcsncoll_l – _mbsncoll_l –](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md), [_strnicoll – _wcsnicoll –, _mbsnicoll –, _strnicoll_l –, _wcsnicoll_l –, _mbsnicoll_l –](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|Porovná dva řetězce pomocí aktuálního národního prostředí informace o kódu stránky (**_stricoll –**, **_wcsicoll –**, **_strnicoll –**, a **_wcsnicoll –** jsou velká a malá písmena)|
|[strcpy – wcscpy –, _mbscpy –](../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md), [strcpy_s wcscpy_s –, _mbscpy_s –](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md)|Zkopírovat jeden řetězec do druhého|
|[strcspn, wcscspn, _mbscspn, _mbscspn_l](../c-runtime-library/reference/strcspn-wcscspn-mbscspn-mbscspn-l.md)|Najde první výskyt znaku v zadané znakové sady v řetězci|
|[_strdup – _wcsdup –, _mbsdup –](../c-runtime-library/reference/strdup-wcsdup-mbsdup.md), [_strdup_dbg – _wcsdup_dbg –](../c-runtime-library/reference/strdup-dbg-wcsdup-dbg.md)|Duplicitní řetězce|
|[strerror _strerror –, _wcserror –, \__wcserror –](../c-runtime-library/reference/strerror-strerror-wcserror-wcserror.md), [strerror_s – _strerror_s –, _wcserror_s –, \__wcserror_s –](../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md)|Mapování číslo chyby na řetězec zprávy|
|[strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)|Řetězec formátu data a času|
|[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)|Porovná dva řetězce bez ohledu na případ|
|[strlen wcslen –, _mbslen –, _mbslen_l –, _mbstrlen –, _mbstrlen_l –](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md), [strnlen – strnlen_s –, wcsnlen –, wcsnlen_s –, _mbsnlen –, _mbsnlen_l –, _mbstrnlen –, _mbstrnlen_l –](../c-runtime-library/reference/strnlen-strnlen-s.md)|Najít délku řetězce|
|[_strlwr _wcslwr –, _mbslwr –, _strlwr_l –, _wcslwr_l –, _mbslwr_l –](../c-runtime-library/reference/strlwr-wcslwr-mbslwr-strlwr-l-wcslwr-l-mbslwr-l.md), [_strlwr_s – _strlwr_s_l –, _mbslwr_s –, _mbslwr_s_l –, _wcslwr_s –, _wcslwr_s_l –](../c-runtime-library/reference/strlwr-s-strlwr-s-l-mbslwr-s-mbslwr-s-l-wcslwr-s-wcslwr-s-l.md)|Převod řetězce na malá písmena|
|[strncat – _strncat_l, wcsncat –, _wcsncat_l, _mbsncat –, _mbsncat_l –](../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md), [strncat_s – _strncat_s_l, wcsncat_s –, _wcsncat_s_l, _mbsncat_s –, _mbsncat_s_l –](../c-runtime-library/reference/strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)|Připojit znaků řetězce|
|[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)|Porovnání dvou řetězců znaků|
|[strncpy – _strncpy_l –, wcsncpy –, _wcsncpy_l –, _mbsncpy –, _mbsncpy_l –](../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md), [strncpy_s – _strncpy_s_l –, wcsncpy_s –, _wcsncpy_s_l –, _mbsncpy_s, _mbsncpy_s_l](../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)|Kopírování znaků jeden řetězec do druhého|
|[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)|Porovnání znaků dva řetězce bez ohledu na případ|
|[_strnset, _strnset_l, _wcsnset, _wcsnset_l, _mbsnset, _mbsnset_l](../c-runtime-library/reference/strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md)|Nastavte nejprve *n* znaky řetězce na zadaný znak|[System::String::Replace](https://msdn.microsoft.com/library/system.string.replace.aspx)|
|[strpbrk, wcspbrk, _mbspbrk, _mbspbrk_l](../c-runtime-library/reference/strpbrk-wcspbrk-mbspbrk-mbspbrk-l.md)|Najde první výskyt znaku z jednoho řetězce v jiném řetězci|
|[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)|Najít poslední výskyt zadaný znak v řetězci|
|[_strrev, _wcsrev, _mbsrev, _mbsrev_l](../c-runtime-library/reference/strrev-wcsrev-mbsrev-mbsrev-l.md)|Reverzní řetězec|
|[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)|Nastavte všechny znaky řetězce na zadaný znak|
|[strspn, wcsspn, _mbsspn, _mbsspn_l](../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)|Nalezení prvního výskytu v řetězci znaku, který nebyl nalezen v jiném řetězci|
|[strstr, wcsstr, _mbsstr, _mbsstr_l](../c-runtime-library/reference/strstr-wcsstr-mbsstr-mbsstr-l.md)|Najde první výskyt zadaného řetězce v jiném řetězci|
|[strtok – _strtok_l –, wcstok –, _wcstok_l –, _mbstok –, _mbstok_l –](../c-runtime-library/reference/strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md), [strtok_s – _strtok_s_l –, wcstok_s –, _wcstok_s_l –, _mbstok_s –, _mbstok_s_l –](../c-runtime-library/reference/strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md)|Najít další token v řetězci|
|[_strupr – _strupr_l –, _mbsupr –, _mbsupr_l –, _wcsupr_l –, _wcsupr –](../c-runtime-library/reference/strupr-strupr-l-mbsupr-mbsupr-l-wcsupr-l-wcsupr.md), [_strupr_s – _strupr_s_l –, _mbsupr_s –, _mbsupr_s_l –, _wcsupr_s –, _wcsupr_s_l –](../c-runtime-library/reference/strupr-s-strupr-s-l-mbsupr-s-mbsupr-s-l-wcsupr-s-wcsupr-s-l.md)|Převod řetězce na velká písmena|
|[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)|Transformace řetězce do by v kolaci formuláře na základě informací specifických pro národní prostředí|
|[vsprintf – _vsprintf_l –, vswprintf –, _vswprintf_l –, \__vswprintf_l –](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md), [vsprintf_s – _vsprintf_s_l –, vswprintf_s – _vswprintf_s_l –](../c-runtime-library/reference/vsprintf-s-vsprintf-s-l-vswprintf-s-vswprintf-s-l.md), [_vsprintf_p – _vsprintf_p_l –, _vswprintf_p – _ vswprintf_p_l –](../c-runtime-library/reference/vsprintf-p-vsprintf-p-l-vswprintf-p-vswprintf-p-l.md)|Zapíše formátovaný výstup pomocí ukazatele na seznam argumentů|
|[vsnprintf – _vsnprintf –, _vsnprintf_l –, _vsnwprintf –, _vsnwprintf_l –](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md), [vsnprintf_s – _vsnprintf_s –, _vsnprintf_s_l –, _vsnwprintf_s –, _vsnwprintf_s_l –](../c-runtime-library/reference/vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l.md)|Zapíše formátovaný výstup pomocí ukazatele na seznam argumentů|

## <a name="see-also"></a>Viz také

[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
