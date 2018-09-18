---
title: vprintf – funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
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
dev_langs:
- C++
helpviewer_keywords:
- vprintf function
- formatted text [C++]
ms.assetid: 02ac7c51-eab1-4bf0-bf4c-77065e3fa744
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2da3abdb5139b6723e13a369117dd75038c3ad41
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074443"
---
# <a name="vprintf-functions"></a>vprintf – funkce

Každá z `vprintf` funkcí bere ukazatel na seznam argumentů a potom formátuje a zapisuje poskytnutá data do určitého cíle. Určuje, zda funkce přijímají široké provést ověření parametru nebo jednobajtové znakové řetězce, cíl výstupu a podporu pro určení pořadí, ve kterém jsou parametry použity ve formátovacím řetězci funkce se liší.

|||
|-|-|
|[_vcprintf – _vcwprintf –](../c-runtime-library/reference/vcprintf-vcprintf-l-vcwprintf-vcwprintf-l.md)|[vfprintf – vfwprintf –](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|
|[_vfprintf_p, _vfprintf_p_l, _vfwprintf_p, _vfwprintf_p_l](../c-runtime-library/reference/vfprintf-p-vfprintf-p-l-vfwprintf-p-vfwprintf-p-l.md)|[vfprintf_s, _vfprintf_s_l, vfwprintf_s, _vfwprintf_s_l](../c-runtime-library/reference/vfprintf-s-vfprintf-s-l-vfwprintf-s-vfwprintf-s-l.md)|
|[vprintf – vwprintf –](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)|[_vprintf_p, _vprintf_p_l, _vwprintf_p, _vwprintf_p_l](../c-runtime-library/reference/vprintf-p-vprintf-p-l-vwprintf-p-vwprintf-p-l.md)|
|[vprintf_s, _vprintf_s_l, vwprintf_s, _vwprintf_s_l](../c-runtime-library/reference/vprintf-s-vprintf-s-l-vwprintf-s-vwprintf-s-l.md)|[vsprintf – vswprintf –](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md)|
|[_vsprintf_p, _vsprintf_p_l, _vswprintf_p, _vswprintf_p_l](../c-runtime-library/reference/vsprintf-p-vsprintf-p-l-vswprintf-p-vswprintf-p-l.md)|[vsprintf_s, _vsprintf_s_l, vswprintf_s, _vswprintf_s_l](../c-runtime-library/reference/vsprintf-s-vsprintf-s-l-vswprintf-s-vswprintf-s-l.md)|
|[_vscprintf, _vscprintf_l, _vscwprintf, _vscwprintf_l](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|[_vsnprintf – _vsnwprintf –](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md)|

## <a name="remarks"></a>Poznámky

`vprintf` Funkce je podobný jako jejich protějšky funkcí, jak je uvedeno v následující tabulce. Nicméně každý `vprintf` funkce přijímá ukazatel na seznam argumentů, že každá z těchto funkcí protějšek přijímá seznam argumentů.

Tyto funkce formátování dat pro výstup do cílů následujícím způsobem.

|Funkce|Protějšek – funkce|Cíl výstupu|Ověřování parametru|Podpora pozičních parametrů více dopředu|
|--------------|--------------------------|------------------------|--------------------------|----------------------------------|
|`_vcprintf`|[_cprintf](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)|konzola|Zkontrolovat hodnoty null.|Ne|
|`_vcwprintf`|[_cwprintf](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)|konzola|Zkontrolovat hodnoty null.|Ne|
|`vfprintf`|[fprintf](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|*Stream*|Zkontrolovat hodnoty null.|Ne|
|**vfprintf_p –**|[fprintf_p –](../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)|*Stream*|Zkontrolujte hodnotu null a je platný formát.|Ano|
|`vfprintf_s`|[fprintf_s –](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|*Stream*|Zkontrolujte hodnotu null a je platný formát.|Ne|
|`vfwprintf`|[fwprintf –](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|*Stream*|Zkontrolovat hodnoty null.|Ne|
|**vfwprintf_p –**|[fwprintf_p –](../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)|*Stream*|Zkontrolujte hodnotu null a je platný formát.|Ano|
|`vfwprintf_s`|[fwprintf_s –](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|*Stream*|Zkontrolujte hodnotu null a je platný formát.|Ne|
|`vprintf`|[printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|`Stdout`|Zkontrolovat hodnoty null.|Ne|
|**vprintf_p –**|[printf_p –](../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)|`Stdout`|Zkontrolujte hodnotu null a je platný formát.|Ano|
|`vprintf_s`|[printf_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|`Stdout`|Zkontrolujte hodnotu null a je platný formát.|Ne|
|`vwprintf`|[wprintf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|`Stdout`|Zkontrolovat hodnoty null.|Ne|
|**vwprintf_p –**|[wprintf_p –](../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)|`Stdout`|Zkontrolujte hodnotu null a je platný formát.|Ano|
|`vwprintf_s`|[wprintf_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|`Stdout`|Zkontrolujte hodnotu null a je platný formát.|Ne|
|**vsprintf –**|[sprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)|paměť odkazované *vyrovnávací paměti*|Zkontrolovat hodnoty null.|Ne|
|**vsprintf_p –**|[sprintf_p –](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)|paměť odkazované *vyrovnávací paměti*|Zkontrolujte hodnotu null a je platný formát.|Ano|
|`vsprintf_s`|[sprintf_s](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|paměť odkazované *vyrovnávací paměti*|Zkontrolujte hodnotu null a je platný formát.|Ne|
|`vswprintf`|[swprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)|paměť odkazované *vyrovnávací paměti*|Zkontrolovat hodnoty null.|Ne|
|**vswprintf_p –**|[swprintf_p –](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)|paměť odkazované *vyrovnávací paměti*|Zkontrolujte hodnotu null a je platný formát.|Ano|
|`vswprintf_s`|[swprintf_s –](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|paměť odkazované *vyrovnávací paměti*|Zkontrolujte hodnotu null a je platný formát.|Ne|
|`_vscprintf`|[_vscprintf](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|paměť odkazované *vyrovnávací paměti*|Zkontrolovat hodnoty null.|Ne|
|`_vscwprintf`|[_vscwprintf](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|paměť odkazované *vyrovnávací paměti*|Zkontrolovat hodnoty null.|Ne|
|`_vsnprintf`|[_snprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)|paměť odkazované *vyrovnávací paměti*|Zkontrolovat hodnoty null.|Ne|
|`_vsnwprintf`|[_snwprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)|paměť odkazované *vyrovnávací paměti*|Zkontrolovat hodnoty null.|Ne|

`argptr` Argument je typu `va_list`, který je definován ve funkcích VARARGS. H a STDARG. H. `argptr` Proměnnou se musí inicializovat pomocí **va_start** a může opakování inicializace odběrů pomocí dalších `va_arg` volá; `argptr` pak odkazuje na začátku seznamu argumentů, které jsou převedena a přenosu pro výstup podle odpovídající specifikace v *formátu* argument. *Formát* má stejnou formu a funkci, jako *formátu* argument pro [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md). Žádná z těchto funkcí vyvolá `va_end`. Podrobnější popis každého `vprintf` fungovat, naleznete v popisu funkce jeho protějšek, jak je uvedeno v předchozí tabulce.

`_vsnprintf` se liší od **vsprintf –** , zapíše Ne více než *počet* bajtů, které mají *vyrovnávací paměti*.

Verze těchto funkcí s **w** vpony v názvu jsou širokoznaké verze odpovídající funkce bez **w** infix; v každém z těchto funkcí širokého znaku  *vyrovnávací paměť* a *formátu* jsou širokoznaké řetězce. V opačném případě každá funkce širokého znaku chová stejně jako jeho protějšek funkce SBCS.

Verze těchto funkcí s **_Malá** a **_p** přípony jsou bezpečnější verze. Tyto verze ověření formátu řetězců a vygeneruje výjimku, pokud formátovací řetězec nemá správný tvar (například pokud se používají neplatné formátovací znaky).

Verze těchto funkcí s **_p** přípona umožňují určit pořadí, ve kterém jsou nahrazeny zadaným argumentům ve formátovacím řetězci. Další informace najdete v tématu [printf_p – poziční parametry](../c-runtime-library/printf-p-positional-parameters.md).

Pro **vsprintf –**, `vswprintf`, `_vsnprintf` a `_vsnwprintf`, pokud ke kopírování dojde mezi řetězci, překrývají, chování není definováno.

> [!IMPORTANT]
>  Ujistěte se, že *formátu* není uživatelem definovaný řetězec. Další informace najdete v tématu [předcházení přetečení vyrovnávací paměti](/windows/desktop/SecBP/avoiding-buffer-overruns). Pokud používáte bezpečné verze těchto funkcí (buď **_Malá** nebo **_p** přípony), uživatelský formátovací řetězec může způsobit výjimku neplatného parametru, pokud obsahuje řetězec zadaný uživatelem Neplatné formátovací znaky.

## <a name="see-also"></a>Viz také

[Stream vstupně-výstupních operací](../c-runtime-library/stream-i-o.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf _sprintf_l –, swprintf, _swprintf_l –, \__swprintf_l –](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)