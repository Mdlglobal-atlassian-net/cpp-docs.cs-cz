---
title: vprintf – funkce
ms.date: 11/04/2016
apilocation:
- msvcr110.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr80.dll
apitype: DLLExport
f1_keywords:
- vprintf
helpviewer_keywords:
- vprintf function
- formatted text [C++]
ms.assetid: 02ac7c51-eab1-4bf0-bf4c-77065e3fa744
ms.openlocfilehash: eb8a2829540876936f6c57745fb56e7d19f16394
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498876"
---
# <a name="vprintf-functions"></a>vprintf – funkce

Každá z `vprintf` funkcí bere ukazatel na seznam argumentů a potom formátuje a zapisuje daná data do konkrétního cíle. Funkce se liší v provedených ověřeních parametrů, ať už funkce přebírají řetězce znaků, které mají formát, a podporu pro určení pořadí, ve kterém jsou parametry použity ve formátovacím řetězci.

|||
|-|-|
|[_vcprintf, _vcwprintf](../c-runtime-library/reference/vcprintf-vcprintf-l-vcwprintf-vcwprintf-l.md)|[vfprintf, vfwprintf](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|
|[_vfprintf_p, _vfprintf_p_l, _vfwprintf_p, _vfwprintf_p_l](../c-runtime-library/reference/vfprintf-p-vfprintf-p-l-vfwprintf-p-vfwprintf-p-l.md)|[vfprintf_s, _vfprintf_s_l, vfwprintf_s, _vfwprintf_s_l](../c-runtime-library/reference/vfprintf-s-vfprintf-s-l-vfwprintf-s-vfwprintf-s-l.md)|
|[vprintf –, vwprintf](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)|[_vprintf_p, _vprintf_p_l, _vwprintf_p, _vwprintf_p_l](../c-runtime-library/reference/vprintf-p-vprintf-p-l-vwprintf-p-vwprintf-p-l.md)|
|[vprintf_s, _vprintf_s_l, vwprintf_s, _vwprintf_s_l](../c-runtime-library/reference/vprintf-s-vprintf-s-l-vwprintf-s-vwprintf-s-l.md)|[vsprintf, vswprintf](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md)|
|[_vsprintf_p, _vsprintf_p_l, _vswprintf_p, _vswprintf_p_l](../c-runtime-library/reference/vsprintf-p-vsprintf-p-l-vswprintf-p-vswprintf-p-l.md)|[vsprintf_s, _vsprintf_s_l, vswprintf_s, _vswprintf_s_l](../c-runtime-library/reference/vsprintf-s-vsprintf-s-l-vswprintf-s-vswprintf-s-l.md)|
|[_vscprintf, _vscprintf_l, _vscwprintf, _vscwprintf_l](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|[_vsnprintf, _vsnwprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md)|

## <a name="remarks"></a>Poznámky

`vprintf` Funkce jsou podobné jejich funkcím, jak je uvedeno v následující tabulce. Každá `vprintf` funkce však přijímá ukazatel na seznam argumentů, zatímco každá z funkcí protějšku přijímá seznam argumentů.

Tyto funkce naformátují data pro výstup do cílových umístění následujícím způsobem.

|Funkce|Funkce protějšek|Cíl výstupu|Ověřování parametru|Podpora pozice parametrů|
|--------------|--------------------------|------------------------|--------------------------|----------------------------------|
|`_vcprintf`|[_cprintf](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)|konzola|Kontrolovat hodnotu null.|Ne|
|`_vcwprintf`|[_cwprintf](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)|konzola|Kontrolovat hodnotu null.|Ne|
|`vfprintf`|[fprintf –](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|*Stream*|Kontrolovat hodnotu null.|Ne|
|**vfprintf_p**|[fprintf_p](../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)|*Stream*|Ověřte hodnotu null a platný formát.|ano|
|`vfprintf_s`|[fprintf_s](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|*Stream*|Ověřte hodnotu null a platný formát.|Ne|
|`vfwprintf`|[fwprintf](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|*Stream*|Kontrolovat hodnotu null.|Ne|
|**vfwprintf_p**|[fwprintf_p](../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)|*Stream*|Ověřte hodnotu null a platný formát.|ano|
|`vfwprintf_s`|[fwprintf_s](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|*Stream*|Ověřte hodnotu null a platný formát.|Ne|
|`vprintf`|[printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|`Stdout`|Kontrolovat hodnotu null.|Ne|
|**vprintf_p**|[printf_p](../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)|`Stdout`|Ověřte hodnotu null a platný formát.|ano|
|`vprintf_s`|[printf_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|`Stdout`|Ověřte hodnotu null a platný formát.|Ne|
|`vwprintf`|[wprintf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|`Stdout`|Kontrolovat hodnotu null.|Ne|
|**vwprintf_p**|[wprintf_p](../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)|`Stdout`|Ověřte hodnotu null a platný formát.|ano|
|`vwprintf_s`|[wprintf_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|`Stdout`|Ověřte hodnotu null a platný formát.|Ne|
|**vsprintf**|[sprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)|paměť, na kterou ukazuje *vyrovnávací paměť*|Kontrolovat hodnotu null.|Ne|
|**vsprintf_p**|[sprintf_p](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)|paměť, na kterou ukazuje *vyrovnávací paměť*|Ověřte hodnotu null a platný formát.|ano|
|`vsprintf_s`|[sprintf_s](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|paměť, na kterou ukazuje *vyrovnávací paměť*|Ověřte hodnotu null a platný formát.|Ne|
|`vswprintf`|[swprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)|paměť, na kterou ukazuje *vyrovnávací paměť*|Kontrolovat hodnotu null.|Ne|
|**vswprintf_p**|[swprintf_p](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)|paměť, na kterou ukazuje *vyrovnávací paměť*|Ověřte hodnotu null a platný formát.|ano|
|`vswprintf_s`|[swprintf_s](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|paměť, na kterou ukazuje *vyrovnávací paměť*|Ověřte hodnotu null a platný formát.|Ne|
|`_vscprintf`|[_vscprintf](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|paměť, na kterou ukazuje *vyrovnávací paměť*|Kontrolovat hodnotu null.|Ne|
|`_vscwprintf`|[_vscwprintf](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|paměť, na kterou ukazuje *vyrovnávací paměť*|Kontrolovat hodnotu null.|Ne|
|`_vsnprintf`|[_snprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)|paměť, na kterou ukazuje *vyrovnávací paměť*|Kontrolovat hodnotu null.|Ne|
|`_vsnwprintf`|[_snwprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)|paměť, na kterou ukazuje *vyrovnávací paměť*|Kontrolovat hodnotu null.|Ne|

Argument má typ `va_list`, který je definován v vararg. `argptr` H a STDARG. Y. Proměnná musí být inicializována pomocí **va_start** a může být znovu inicializována následnými `va_arg` voláními; `argptr` následně odkazuje na začátek seznamu argumentů, které jsou převedeny a přeneseny pro výstup podle odpovídajících specifikací v argumentu *formát.* `argptr` *Formát* má stejnou formu a funkci jako argument *Format* pro [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md). Žádná z těchto funkcí nevyvolává `va_end`. Podrobnější popis jednotlivých `vprintf` funkcí najdete v popisu její funkce protějšků, jak je uvedeno v předchozí tabulce.

`_vsnprintf`se liší od **vsprintf** v tom, že zapisuje do *vyrovnávací paměti*více než *počet* bajtů.

Verze těchto funkcí s **w** vpony v názvu jsou verze odpovídajících funkcí bez vpony s w. v každé z těchto velkých znakových funkcí jsou *vyrovnávací paměť* a *Formát* řetězce s velkým počtem znaků. V opačném případě se každá funkce s velkým znakem chová stejně jako její funkce SBCS.

Verze těchto funkcí s příponami **_s** a **_p** jsou bezpečnější verze. Tyto verze ověřují řetězce formátu a vygenerují výjimku, pokud řetězec formátu není správně vytvořen (například pokud jsou použity neplatné znaky formátování).

Verze těchto funkcí s příponou **_p** poskytují možnost zadat pořadí, ve kterém jsou zadané argumenty nahrazeny řetězcem formátu. Další informace najdete v tématu [Printf_p pozičních parametrů](../c-runtime-library/printf-p-positional-parameters.md).

Pro **vsprintf**, `vswprintf`, `_vsnprintf` a `_vsnwprintf`Pokud probíhá kopírování mezi řetězci, které se překrývají, chování není definováno.

> [!IMPORTANT]
>  Ujistěte se, že *Formát* není uživatelem definovaný řetězec. Další informace najdete v tématu [předcházení přetečení vyrovnávací paměti](/windows/win32/SecBP/avoiding-buffer-overruns). Používáte-li zabezpečené verze těchto funkcí (přípony **_s** nebo **_p** ), může uživatelsky zadaný řetězec formátu aktivovat výjimku neplatného parametru, pokud uživatelem zadaný řetězec obsahuje neplatné znaky formátování.

## <a name="see-also"></a>Viz také:

[Vstup/výstup datového proudu](../c-runtime-library/stream-i-o.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)
