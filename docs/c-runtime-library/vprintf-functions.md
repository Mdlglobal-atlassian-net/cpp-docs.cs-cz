---
title: vprintf – funkce | Microsoft Docs
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
ms.openlocfilehash: d63e5da79b0f78e701f3ababaf54bef41fbf88a1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32418377"
---
# <a name="vprintf-functions"></a>vprintf – funkce
Každý z `vprintf` funkce má ukazatel na seznam argumentů, pak naformátuje a zapíše daná data na určitý cíl. Ověření parametru provést, jestli funkce trvat široké nebo znakovou řetězce, cíl výstupu a podpora pro určení pořadí, ve kterém se používají parametry v řetězec formátu funkce se liší.  
  
|||  
|-|-|  
|[_vcprintf –, _vcwprintf –](../c-runtime-library/reference/vcprintf-vcprintf-l-vcwprintf-vcwprintf-l.md)|[vfprintf –, vfwprintf –](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|  
|[_vfprintf_p, _vfprintf_p_l, _vfwprintf_p, _vfwprintf_p_l](../c-runtime-library/reference/vfprintf-p-vfprintf-p-l-vfwprintf-p-vfwprintf-p-l.md)|[vfprintf_s, _vfprintf_s_l, vfwprintf_s, _vfwprintf_s_l](../c-runtime-library/reference/vfprintf-s-vfprintf-s-l-vfwprintf-s-vfwprintf-s-l.md)|  
|[vprintf –, vwprintf –](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)|[_vprintf_p, _vprintf_p_l, _vwprintf_p, _vwprintf_p_l](../c-runtime-library/reference/vprintf-p-vprintf-p-l-vwprintf-p-vwprintf-p-l.md)|  
|[vprintf_s, _vprintf_s_l, vwprintf_s, _vwprintf_s_l](../c-runtime-library/reference/vprintf-s-vprintf-s-l-vwprintf-s-vwprintf-s-l.md)|[vsprintf –, vswprintf –](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md)|  
|[_vsprintf_p, _vsprintf_p_l, _vswprintf_p, _vswprintf_p_l](../c-runtime-library/reference/vsprintf-p-vsprintf-p-l-vswprintf-p-vswprintf-p-l.md)|[vsprintf_s, _vsprintf_s_l, vswprintf_s, _vswprintf_s_l](../c-runtime-library/reference/vsprintf-s-vsprintf-s-l-vswprintf-s-vswprintf-s-l.md)|  
|[_vscprintf, _vscprintf_l, _vscwprintf, _vscwprintf_l](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|[_vsnprintf –, _vsnwprintf –](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md)|  
  
## <a name="remarks"></a>Poznámky  
 `vprintf` Jsou podobné funkce jejich protějšku, jak je uvedeno v následující tabulce. Ale každý `vprintf` funkce přijímá ukazatel na seznam argumentů, zatímco každá z těchto funkcí protějšku přijímá seznam argumentů.  
  
 Tyto funkce tento formát dat pro výstup do cíle.  
  
|Funkce|Funkce protějšku|Cíl výstupu|Ověřování parametru|Podpora poziční parametr|  
|--------------|--------------------------|------------------------|--------------------------|----------------------------------|  
|`_vcprintf`|[_cprintf](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)|konzola|Zkontrolujte hodnotu null.|Ne|  
|`_vcwprintf`|[_cwprintf](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)|konzola|Zkontrolujte hodnotu null.|Ne|  
|`vfprintf`|[fprintf](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|*Stream*|Zkontrolujte hodnotu null.|Ne|  
|**vfprintf_p –**|[fprintf_p –](../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)|*Stream*|Zkontrolujte hodnotu null a platný formát.|Ano|  
|`vfprintf_s`|[fprintf_s –](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|*Stream*|Zkontrolujte hodnotu null a platný formát.|Ne|  
|`vfwprintf`|[fwprintf –](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|*Stream*|Zkontrolujte hodnotu null.|Ne|  
|**vfwprintf_p –**|[fwprintf_p –](../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)|*Stream*|Zkontrolujte hodnotu null a platný formát.|Ano|  
|`vfwprintf_s`|[fwprintf_s –](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|*Stream*|Zkontrolujte hodnotu null a platný formát.|Ne|  
|`vprintf`|[printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|`Stdout`|Zkontrolujte hodnotu null.|Ne|  
|**vprintf_p –**|[printf_p –](../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)|`Stdout`|Zkontrolujte hodnotu null a platný formát.|Ano|  
|`vprintf_s`|[printf_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|`Stdout`|Zkontrolujte hodnotu null a platný formát.|Ne|  
|`vwprintf`|[wprintf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|`Stdout`|Zkontrolujte hodnotu null.|Ne|  
|**vwprintf_p –**|[wprintf_p –](../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)|`Stdout`|Zkontrolujte hodnotu null a platný formát.|Ano|  
|`vwprintf_s`|[wprintf_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|`Stdout`|Zkontrolujte hodnotu null a platný formát.|Ne|  
|**vsprintf –**|[sprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)|paměť na kterou odkazuje *vyrovnávací paměti*|Zkontrolujte hodnotu null.|Ne|  
|**vsprintf_p –**|[sprintf_p –](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)|paměť na kterou odkazuje *vyrovnávací paměti*|Zkontrolujte hodnotu null a platný formát.|Ano|  
|`vsprintf_s`|[sprintf_s](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|paměť na kterou odkazuje *vyrovnávací paměti*|Zkontrolujte hodnotu null a platný formát.|Ne|  
|`vswprintf`|[swprintf –](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)|paměť na kterou odkazuje *vyrovnávací paměti*|Zkontrolujte hodnotu null.|Ne|  
|**vswprintf_p –**|[swprintf_p –](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)|paměť na kterou odkazuje *vyrovnávací paměti*|Zkontrolujte hodnotu null a platný formát.|Ano|  
|`vswprintf_s`|[swprintf_s –](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|paměť na kterou odkazuje *vyrovnávací paměti*|Zkontrolujte hodnotu null a platný formát.|Ne|  
|`_vscprintf`|[_vscprintf](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|paměť na kterou odkazuje *vyrovnávací paměti*|Zkontrolujte hodnotu null.|Ne|  
|`_vscwprintf`|[_vscwprintf](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|paměť na kterou odkazuje *vyrovnávací paměti*|Zkontrolujte hodnotu null.|Ne|  
|`_vsnprintf`|[_snprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)|paměť na kterou odkazuje *vyrovnávací paměti*|Zkontrolujte hodnotu null.|Ne|  
|`_vsnwprintf`|[_snwprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)|paměť na kterou odkazuje *vyrovnávací paměti*|Zkontrolujte hodnotu null.|Ne|  
  
 `argptr` Argument má typ `va_list`, která je definována v vararg. H a STDARG. H. `argptr` Proměnná musí být inicializován podle **va_start –,** a může být znovu inicializovány podle dalších `va_arg` volá; `argptr` pak odkazuje na začátku seznamu argumentů, které jsou převedeny a přenosu pro výstup podle odpovídající specifikací v *formát* argument. *Formát* má stejnou tvoří a fungovat jako *formátu* argument pro [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md). Žádná z těchto funkcí vyvolá `va_end`. Podrobnější popis jednotlivých `vprintf` fungovat, naleznete v popisu funkce jeho protějšku, jak je uvedeno v předchozí tabulce.  
  
 `_vsnprintf` se liší od **vsprintf –** v tom, že zapíše Ne víc než *počet* bajtů, které mají *vyrovnávací paměti*.  
  
 Verze tyto funkce s **w** zaváděcí v názvu jsou široká charakterová verzích odpovídající funkce bez **w** infix; v každé z těchto funkcí široká charakterová  *vyrovnávací paměť* a *formát* jsou široká charakterová řetězce. Jinak hodnota každý široká charakterová funkce se chová stejně jako jeho protějšku funkce SBCS.  
  
 Verze tyto funkce s **_Malá** a **_p** přípony jsou bezpečnější verze. Tyto verze ověřte řetězce formátu a vygeneruje výjimku, pokud řetězec formátu není ve správném formátu (například pokud se používají neplatné formátování znaky).  
  
 Verze tyto funkce s **_p** příponu umožňují určit pořadí, ve kterém jsou zadané argumenty nahrazena ve formátovacím řetězci. Další informace najdete v tématu [printf_p – poziční parametry](../c-runtime-library/printf-p-positional-parameters.md).  
  
 Pro **vsprintf –**, `vswprintf`, `_vsnprintf` a `_vsnwprintf`, případě kopírování mezi řetězce, překrývají, chování není definován.  
  
> [!IMPORTANT]
>  Ujistěte se, že *formát* není řetězec definovaný uživatelem. Další informace najdete v tématu [zabraňující způsobí přetečení vyrovnávací paměti](http://msdn.microsoft.com/library/windows/desktop/ms717795). Pokud používáte bezpečné verze těchto funkcí (buď **_Malá** nebo **_p** přípony), řetězec formátu uživatelem zadané může spustit výjimku neplatný parametr, pokud uživatel zadaný řetězec obsahuje formátování obsahuje neplatné znaky.  
  
## <a name="see-also"></a>Viz také  
 [Datový proud vstupně-výstupních operací](../c-runtime-library/stream-i-o.md)   
 [fprintf, _fprintf_l –, fwprintf –, _fwprintf_l –](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf, _printf_l –, wprintf, _wprintf_l –](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [sprintf, _sprintf_l –, swprintf –, _swprintf_l –, \__swprintf_l –](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [va_arg, va_copy, va_end, va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)