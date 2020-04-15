---
title: vprintf – funkce
ms.date: 11/04/2016
api_location:
- msvcr110.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr80.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- vprintf
helpviewer_keywords:
- vprintf function
- formatted text [C++]
ms.assetid: 02ac7c51-eab1-4bf0-bf4c-77065e3fa744
ms.openlocfilehash: db4927e983a27110e587dacd9acf909f0c735b87
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365681"
---
# <a name="vprintf-functions"></a>vprintf – funkce

Každá z `vprintf` funkcí přejde na seznam argumentů, pak naformátuje a zapíše daná data do určitého cíle. Funkce se liší v ověření parametru provádí, zda funkce trvat široký nebo jednobajtový znak řetězce, výstupní cíl a podporu pro určení pořadí, ve kterém jsou použity parametry ve formátu řetězce.

|||
|-|-|
|[_vcprintf, _vcwprintf](../c-runtime-library/reference/vcprintf-vcprintf-l-vcwprintf-vcwprintf-l.md)|[vfprintf, vfwprintf](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|
|[_vfprintf_p, _vfprintf_p_l, _vfwprintf_p, _vfwprintf_p_l](../c-runtime-library/reference/vfprintf-p-vfprintf-p-l-vfwprintf-p-vfwprintf-p-l.md)|[vfprintf_s, _vfprintf_s_l, vfwprintf_s, _vfwprintf_s_l](../c-runtime-library/reference/vfprintf-s-vfprintf-s-l-vfwprintf-s-vfwprintf-s-l.md)|
|[vprintf, vwprintf](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)|[_vprintf_p, _vprintf_p_l, _vwprintf_p, _vwprintf_p_l](../c-runtime-library/reference/vprintf-p-vprintf-p-l-vwprintf-p-vwprintf-p-l.md)|
|[vprintf_s, _vprintf_s_l, vwprintf_s, _vwprintf_s_l](../c-runtime-library/reference/vprintf-s-vprintf-s-l-vwprintf-s-vwprintf-s-l.md)|[vsprintf, vswprintf](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md)|
|[_vsprintf_p, _vsprintf_p_l, _vswprintf_p, _vswprintf_p_l](../c-runtime-library/reference/vsprintf-p-vsprintf-p-l-vswprintf-p-vswprintf-p-l.md)|[vsprintf_s, _vsprintf_s_l, vswprintf_s, _vswprintf_s_l](../c-runtime-library/reference/vsprintf-s-vsprintf-s-l-vswprintf-s-vswprintf-s-l.md)|
|[_vscprintf, _vscprintf_l, _vscwprintf, _vscwprintf_l](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|[_vsnprintf, _vsnwprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md)|

## <a name="remarks"></a>Poznámky

Funkce `vprintf` jsou podobné jejich protějšku funkce uvedené v následující tabulce. Každá `vprintf` funkce však přijímá ukazatel na seznam argumentů, zatímco každá funkce protějšku přijímá seznam argumentů.

Tyto funkce formátovat data pro výstup do cíle takto.

|Funkce|Protějšek funkce|Výstupní cíl|Ověřování parametru|Podpora pozičních parametrů|
|--------------|--------------------------|------------------------|--------------------------|----------------------------------|
|`_vcprintf`|[_cprintf](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)|konzola|Zkontrolujte hodnotu null.|ne|
|`_vcwprintf`|[_cwprintf](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)|konzola|Zkontrolujte hodnotu null.|ne|
|`vfprintf`|[fprintf](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|*Datový proud*|Zkontrolujte hodnotu null.|ne|
|**vfprintf_p**|[fprintf_p](../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)|*Datový proud*|Zkontrolujte, zda není k onomu formátu null a platný.|ano|
|`vfprintf_s`|[fprintf_s](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|*Datový proud*|Zkontrolujte, zda není k onomu formátu null a platný.|ne|
|`vfwprintf`|[fwprintf](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|*Datový proud*|Zkontrolujte hodnotu null.|ne|
|**vfwprintf_p**|[fwprintf_p](../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)|*Datový proud*|Zkontrolujte, zda není k onomu formátu null a platný.|ano|
|`vfwprintf_s`|[fwprintf_s](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|*Datový proud*|Zkontrolujte, zda není k onomu formátu null a platný.|ne|
|`vprintf`|[Printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|`Stdout`|Zkontrolujte hodnotu null.|ne|
|**vprintf_p**|[printf_p](../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)|`Stdout`|Zkontrolujte, zda není k onomu formátu null a platný.|ano|
|`vprintf_s`|[printf_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|`Stdout`|Zkontrolujte, zda není k onomu formátu null a platný.|ne|
|`vwprintf`|[wprintf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|`Stdout`|Zkontrolujte hodnotu null.|ne|
|**vwprintf_p**|[wprintf_p](../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)|`Stdout`|Zkontrolujte, zda není k onomu formátu null a platný.|ano|
|`vwprintf_s`|[wprintf_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|`Stdout`|Zkontrolujte, zda není k onomu formátu null a platný.|ne|
|**vsprintf**|[sprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)|paměť, na kterou ukazuje *vyrovnávací paměť*|Zkontrolujte hodnotu null.|ne|
|**vsprintf_p**|[sprintf_p](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)|paměť, na kterou ukazuje *vyrovnávací paměť*|Zkontrolujte, zda není k onomu formátu null a platný.|ano|
|`vsprintf_s`|[sprintf_s](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|paměť, na kterou ukazuje *vyrovnávací paměť*|Zkontrolujte, zda není k onomu formátu null a platný.|ne|
|`vswprintf`|[swprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)|paměť, na kterou ukazuje *vyrovnávací paměť*|Zkontrolujte hodnotu null.|ne|
|**vswprintf_p**|[swprintf_p](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)|paměť, na kterou ukazuje *vyrovnávací paměť*|Zkontrolujte, zda není k onomu formátu null a platný.|ano|
|`vswprintf_s`|[swprintf_s](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|paměť, na kterou ukazuje *vyrovnávací paměť*|Zkontrolujte, zda není k onomu formátu null a platný.|ne|
|`_vscprintf`|[_vscprintf](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|paměť, na kterou ukazuje *vyrovnávací paměť*|Zkontrolujte hodnotu null.|ne|
|`_vscwprintf`|[_vscwprintf](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|paměť, na kterou ukazuje *vyrovnávací paměť*|Zkontrolujte hodnotu null.|ne|
|`_vsnprintf`|[_snprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)|paměť, na kterou ukazuje *vyrovnávací paměť*|Zkontrolujte hodnotu null.|ne|
|`_vsnwprintf`|[_snwprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)|paměť, na kterou ukazuje *vyrovnávací paměť*|Zkontrolujte hodnotu null.|ne|

Argument `argptr` má `va_list`typ , který je definován v příkazu VARARGS. H a STDARG. H. Proměnná `argptr` musí být inicializována **va_start** a `va_arg` může být znovu inicializována následnými voláními; `argptr` pak odkazuje na začátek seznamu argumentů, které jsou převedeny a přenášeny pro výstup podle odpovídajícíspecifikace v *argumentu formátu.* *formát* má stejný tvar a funkci jako argument *formátu* pro [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md). Žádná z těchto `va_end`funkcí vyvolá . Podrobnější popis jednotlivých `vprintf` funkcí naleznete v popisu její funkce protějšku uvedené v předchozí tabulce.

`_vsnprintf`se liší od **vsprintf** v tom, že nezapíše více než *počet* bajtů do *vyrovnávací paměti*.

Verze těchto funkcí s **infix w** v názvu jsou širokoznakové verze odpovídajících funkcí bez **w** infix; v každé z těchto širokoúhlých funkcí jsou *vyrovnávací paměť* a *formát* řetězce s širokými znaky. V opačném případě se každá funkce wide-character chová stejně jako jeho funkce protějšku SBCS.

Verze těchto funkcí s **_s** a **_p** přípony jsou bezpečnější verze. Tyto verze ověřují formátovací řetězce a vygenerují výjimku, pokud formátovací řetězec není dobře tvarovaný (například pokud jsou použity neplatné formátovací znaky).

Verze těchto funkcí s **příponou _p** poskytují možnost určit pořadí, ve kterém jsou zadané argumenty nahrazeny ve formátovacím řetězci. Další informace naleznete [v tématu printf_p polohové parametry](../c-runtime-library/printf-p-positional-parameters.md).

Pro **vsprintf** `_vsnprintf` , `_vsnwprintf` `vswprintf`a , pokud dojde ke kopírování mezi řetězci, které se překrývají, chování není definováno.

> [!IMPORTANT]
> Ujistěte se, že *formát* není uživatelem definovaný řetězec. Další informace naleznete v [tématu Zabránění přetečení vyrovnávací paměti](/windows/win32/SecBP/avoiding-buffer-overruns). Pokud používáte zabezpečené verze těchto funkcí **(_s** nebo **_p** přípony), může formátovací řetězec dodaný uživatelem vyvolat neplatnou výjimku parametrů, pokud řetězec dodaný uživatelem obsahuje neplatné formátovací znaky.

## <a name="see-also"></a>Viz také

[I/O proudu](../c-runtime-library/stream-i-o.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, \__swprintf_l, _swprintf_l](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)
