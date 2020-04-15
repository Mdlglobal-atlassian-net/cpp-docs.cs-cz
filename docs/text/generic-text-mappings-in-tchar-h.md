---
title: Mapování obecného textu v souboru tchar.h
ms.date: 11/04/2016
helpviewer_keywords:
- mapping generic-text
- generic-text mappings [C++]
- character sets [C++], generic-text mappings
- Unicode [C++], generic-text mappings
- MBCS [C++], generic-text mappings
- TCHAR.H data types, mapping
- mappings [C++], TCHAR.H
ms.assetid: 01e1bb74-5a01-4093-8720-68b6c1fdda80
ms.openlocfilehash: bf872df2e6fb49e64a973e8799eef98dec1cb472
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361346"
---
# <a name="generic-text-mappings-in-tcharh"></a>Mapování obecného textu v souboru tchar.h

Pro zjednodušení přenosu kódu pro mezinárodní použití poskytuje knihovna microsoft run-time pro mnoho datových typů, rutin a dalších objektů mapování obecného textu specifické pro společnost Microsoft. Tato mapování, která jsou definována v souboru tchar.h, můžete použít k zápisu obecného kódu, který lze zkompilovat pro jednobajtové, vícebajtové nebo jednobajtové nebo unicode znakové sady, v závislosti na konstantě manifestu, kterou definujete pomocí příkazu. `#define` Mapování obecného textu jsou rozšíření společnosti Microsoft, která nejsou kompatibilní s rozhraním ANSI.

Pomocí souboru tchar.h můžete vytvářet jednobajtové, vícebajtové znakové sady (MBCS) a aplikace Unicode ze stejných zdrojů. tchar.h definuje makra (která `_tcs`mají předponu), která se správnými `str` `_mbs`definicemi `wcs` preprocesoru mapují podle potřeby na , nebo funkce. Chcete-li vytvořit sadu MBCS, definujte symbol `_MBCS`. Chcete-li vytvořit unicode, definujte symbol `_UNICODE`. Chcete-li vytvořit jednobajtovou aplikaci, nedefinujte ani jednobajtovou (výchozí). Ve výchozím `_UNICODE` nastavení je definována pro aplikace knihovny MFC.

Datový `_TCHAR` typ je definován podmíněně v souboru tchar.h. Pokud je `_UNICODE` symbol definován pro `_TCHAR` sestavení, je definován jako **wchar_t**; jinak pro jednobajtové a MBCS sestavení je definovánjako **char**. **(wchar_t**, základní datový typ unicode wide-character, je 16bitový protějšek 8bitového podepsaného **znaku**.) Pro mezinárodní aplikace `_tcs` použijte řadu funkcí, `_TCHAR` které pracují v jednotkách, nikoli v bajtech. Například `_tcsncpy` kopie `n` `_TCHARs`, `n` nikoli bajty.

Vzhledem k tomu, že některé funkce zpracování řetězců s `char*` jedním bajtem (SBCS) berou `_MBCS` (podepsané) parametry, výsledky upozornění kompilátoru neshody typů, když je definován. Toto upozornění lze vyhnout třem způsobům:

1. Použijte textově bezpečné funkce v souborech tchar.h. Toto je výchozí chování.

1. Pomocí přímých maker v souboru tchar.h definujte `_MB_MAP_DIRECT` na příkazovém řádku. Pokud tak učiníte, je nutné ručně odpovídat typy. Jedná se o nejrychlejší metodu, ale není typově bezpečná.

1. Použijte typově bezpečné staticky propojené funkce knihovny thunks v tchar.h. Chcete-li tak učinit, definujte konstantu `_NO_INLINING` na příkazovém řádku. Toto je nejpomalejší metoda, ale nejvíce typově bezpečná.

### <a name="preprocessor-directives-for-generic-text-mappings"></a>Direktivy preprocesoru pro mapování obecného textu

|# definovat|Zkompilovaná verze|Příklad|
|---------------|----------------------|-------------|
|`_UNICODE`|Unicode (široký znak)|`_tcsrev`mapy do`_wcsrev`|
|`_MBCS`|Vícebajtový znak|`_tcsrev`mapy do`_mbsrev`|
|Žádné (výchozí nastavení `_UNICODE` nemá `_MBCS` ani definováno)|SBCS (ASCII)|`_tcsrev`mapy do`strrev`|

Například `_tcsrev`funkce obecného textu , která je definována v `_mbsrev` souboru `_MBCS` tchar.h, se mapuje na if you defined in your program, or to `_wcsrev` if you defined `_UNICODE`. V `_tcsrev` opačném `strrev`případě mapuje na . Ostatní mapování datových typů jsou k dispozici v tchar.h pro programování pohodlí, ale `_TCHAR` je nejužitečnější.

### <a name="generic-text-data-type-mappings"></a>Mapování datových typů obecného textu

|Obecný text<br /> Název datového typu|_UNICODE &<br /> _MBCS není definováno|_mbcs<br /> Definovány|_unicode<br /> Definovány|
|--------------------------------------|----------------------------------------|------------------------|---------------------------|
|`_TCHAR`|**char**|**char**|**wchar_t**|
|`_TINT`|**int**|**unsigned int**|`wint_t`|
|`_TSCHAR`|**podepsaný znak**|**podepsaný znak**|**wchar_t**|
|`_TUCHAR`|**unsigned char**|**unsigned char**|**wchar_t**|
|`_TXCHAR`|**char**|**unsigned char**|**wchar_t**|
|`_T` nebo `_TEXT`|Žádný efekt (odstraněn preprocesorem)|Žádný efekt (odstraněn preprocesorem)|`L`(převede následující znak nebo řetězec na jeho protějšek Unicode)|

Seznam mapování obecného textu rutin, proměnných a dalších objektů naleznete v [tématu Mapování obecného textu](../c-runtime-library/generic-text-mappings.md) v odkazu knihovny run-time.

> [!NOTE]
> Nepoužívejte `str` rodinu funkcí s řetězci Unicode, které mohou obsahovat vložené nula bajtů. Podobně nepoužívejte `wcs` rodinu funkcí s řetězci MBCS (nebo SBCS).

Následující fragmenty kódu ilustrují použití `_TCHAR` a `_tcsrev` pro mapování na modely MBCS, Unicode a SBCS.

```cpp
_TCHAR *RetVal, *szString;
RetVal = _tcsrev(szString);
```

Pokud `_MBCS` byla definována, preprocesor mapuje tento fragment na tento kód:

```cpp
char *RetVal, *szString;
RetVal = _mbsrev(szString);
```

Pokud `_UNICODE` byla definována, preprocesor mapuje tento fragment na tento kód:

```cpp
wchar_t *RetVal, *szString;
RetVal = _wcsrev(szString);
```

Pokud ani `_MBCS` `_UNICODE` nebyly definovány, preprocesor mapuje fragment na jednobajtovský kód ASCII takto:

```cpp
char *RetVal, *szString;
RetVal = strrev(szString);
```

Proto můžete psát, udržovat a zkompilovat soubor kódu s jedním zdrojem ke spuštění s rutiny, které jsou specifické pro některý ze tří druhů znakových sad.

## <a name="see-also"></a>Viz také

[Text a řetězce](../text/text-and-strings-in-visual-cpp.md)<br/>
[Použití datových typů TCHAR.H s kódováním _MBCS](../text/using-tchar-h-data-types-with-mbcs-code.md)
