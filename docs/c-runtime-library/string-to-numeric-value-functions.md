---
title: "Funkce řetězců na číselné hodnoty | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apilocation:
- msvcr80.dll
- msvcr110.dll
- msvcr120.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr90.dll
apitype: DLLExport
f1_keywords:
- _tcstoui64
- _tcstoi64
dev_langs:
- C++
helpviewer_keywords:
- parsing, numeric strings
- string conversion, to numeric values
ms.assetid: 11cbd9ce-033b-4914-bf66-029070e7e385
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 68586bac573018bceb7dc982625ff6a859d18871
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="string-to-numeric-value-functions"></a>Funkce řetězců na numerické hodnoty
-   [strtod, _strtod_l, wcstod, _wcstod_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)  
  
-   [strtol, wcstol, _strtol_l, _wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)  
  
-   [strtoul, _strtoul_l, wcstoul, _wcstoul_l](../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)  
  
-   [_strtoi64, _wcstoi64, _strtoi64_l, _wcstoi64_l](../c-runtime-library/reference/strtoi64-wcstoi64-strtoi64-l-wcstoi64-l.md)  
  
-   [_strtoui64, _wcstoui64, _strtoui64_l, _wcstoui64_l](../c-runtime-library/reference/strtoui64-wcstoui64-strtoui64-l-wcstoui64-l.md)  
  
## <a name="remarks"></a>Poznámky  
 Jednotlivé funkce v **strtod –** rodiny převede na číselnou hodnotu řetězce ukončené hodnotou null. K dispozici funkce jsou uvedené v následující tabulce.  
  
|Funkce|Popis|  
|--------------|-----------------|  
|`strtod`|Převést řetězec na dvojitou přesností s pohyblivou desetinnou čárkou|  
|`strtol`|Převést řetězec na dlouhé celé číslo|  
|`strtoul`|Převést řetězec na celé číslo bez znaménka dlouho|  
|`_strtoi64`|Převést řetězec na 64-bit `__int64` celé číslo|  
|`_strtoui64`|Převést řetězec na nepodepsané 64-bit `__int64` celé číslo|  
  
 `wcstod`, `wcstol`, `wcstoul`, a `_wcstoi64` jsou verze široká charakterová `strtod`, `strtol`, `strtoul`, a `_strtoi64`, v uvedeném pořadí. Argument řetězce pro každou z těchto funkcí široká charakterová je řetězec široká charakterová; jednotlivé funkce se chová stejně jako k jeho protějšku jedním znaková jinak.  
  
 `strtod` Funkce přebírá dva argumenty: vstupní řetězec je první a druhý a ukazatel na znak, který končí procesu převodu. `strtol`, `strtoul`, **_strtoi64 –** a **_strtoui64 –** trvat třetí argument jako základní číslo k použití v procesu převodu.  
  
 Vstupní řetězec je posloupnost znaků, které lze interpretovat jako hodnotu zadaného typu. Jednotlivé funkce zastaví čtení řetězce u prvního znaku, který nelze rozpoznat jako součást číslo. To může být ukončující znak hodnoty null. Pro `strtol`, `strtoul`, `_strtoi64`, a `_strtoui64`, tento ukončující znak může být také první číselné znak větší než nebo rovna hodnotě základní uživatelem zadané číslo.  
  
 Pokud uživatel zadal ukazatel na znakem end převod není nastaven na **NULL** během volání, ukazatel na znak, který zastavena kontroly se uloží existuje místo. Pokud žádný převod lze provést (nebyly nalezeny žádné platné číslice nebo byl zadán neplatný základní), hodnota ukazatele řetězec je uložena na této adrese.  
  
 `strtod`očekává řetězec v následujícím formátu:  
  
 [*prázdné*] [*přihlašovací*] [`digits`] [**.** `digits`] [{**d** &#124; **D** &#124; **e** &#124; **E**} [*přihlašovací*]`digits`]  
  
 A *prázdné* může obsahovat místa nebo kartě znaků, které se mají ignorovat; *přihlašovací* je buď plus (**+**) nebo minus (**-**); a `digits` jsou jeden nebo více desetinných míst. Pokud před základ – znak, který se zobrazí žádné číslice, alespoň jeden musí být uvedena za základ – znak. Desetinných míst může následovat exponentem, který se skládá z úvodní písmeno (**d**, **D**, **e**, nebo **E**) a volitelně číslo se znaménkem. Pokud exponentu část ani základ – znak zobrazí, předpokládá se základ – znak podle poslední číslice v řetězci. První znak, který se nevejde tento formulář zastaví kontroly.  
  
 `strtol`, `strtoul`, `_strtoi64`, A `_strtoui64` funkce očekávat řetězec v následujícím formátu:  
  
 [*prázdné*] [{ **+**  &#124;  **-** }] [**0** [{ **x** &#124; **X** }]] [`digits`]  
  
 Pokud je základní argumentem mezi 2 a 36, se používá jako základní číslo. Pokud je 0, počáteční znaky odkazuje ukazatele end převod se používají k určení ve znalostní bázi. Pokud první znak je 0 a druhý znak není 'x' nebo 'X', řetězec interpretována jako osmičková celé číslo. jinak je interpretován jako s desetinným číslem. Pokud první znak je '0' a druhá znak je písmeno "x" nebo "X", řetězec interpretována jako hexadecimální celé číslo. Pokud je první znak ' 1' přes ' 9', řetězec interpretována jako desítkové celé číslo. Písmena 'a' do 'z' (nebo 'A' až 'Z') jsou přiřazeny hodnoty 10 až 35; pouze písmena, jejichž přiřazené hodnoty jsou menší než *základní* jsou povoleny. `strtoul`a `_strtoui64` povolit znaménkem plus (**+**) nebo minus (**-**) přihlašovací předpony – úvodní znaménka minus označuje, že je Negované návratovou hodnotu.  
  
 Výstupní hodnota je ovlivňován nastavením `LC_NUMERIC` kategorie nastavení národního prostředí; viz [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) Další informace. Verze tyto funkce bez **_l** příponu využívání aktuální národní prostředí pro toto chování závislých na národním prostředí, verze s **_l** příponu jsou shodné s tím rozdílem, že používají parametr národního prostředí Místo toho předaná.  
  
 Při hodnotě vrácené tyto funkce by způsobilo přetečení nebo podtečení aplikace, nebo při převodu není možné, speciální případu hodnoty jsou vráceny, jak je znázorněno:  
  
|Funkce|Podmínka|Hodnota vrácená|  
|--------------|---------------|--------------------|  
|`strtod`|Přetečení|+/- `HUGE_VAL`|  
|`strtod`|Podtečení nebo žádný převod|0|  
|`strtol`|+ Přetečení|**LONG_MAX –**|  
|`strtol`|-Přetečení|**LONG_MIN –**|  
|`strtol`|Podtečení nebo žádný převod|0|  
|`_strtoi64`|+ Přetečení|**_I64_MAX**|  
|`_strtoi64`|-Přetečení|**_I64_MIN**|  
|`_strtoi64`|Žádný převod|0|  
|`_strtoui64`|Přetečení|**_UI64_MAX**|  
|`_strtoui64`|Žádný převod|0|  
  
 **_I64_MAX**, _**I64_MIN**, a **_UI64_MAX** jsou definovány v omezení. H.  
  
 `wcstod`, `wcstol`, `wcstoul`, `_wcstoi64`, a `_wcstoui64` jsou verze široká charakterová `strtod`, `strtol`, `strtoul`, `_strtoi64`, a `_strtoui64`, respektive; má ukazatel na argument end převod na každou z těchto funkcí široká charakterová je řetězec znaků celou. Jinak každá z těchto funkcí široká charakterová se chová stejně k jeho protějšku jedním znaková.  
  
## <a name="see-also"></a>Viz také  
 [Převod dat](../c-runtime-library/data-conversion.md)   
 [Národní prostředí](../c-runtime-library/locale.md)   
 [Výklad sekvencí vícebajtových znaků](../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [Podpora plovoucí desetinné čárky](../c-runtime-library/floating-point-support.md)   
 [atof, _atof_l, _wtof, _wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)