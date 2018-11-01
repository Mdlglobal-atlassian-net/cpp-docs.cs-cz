---
title: Použití mapování obecného textu
ms.date: 11/04/2016
f1_keywords:
- _UNICODE
helpviewer_keywords:
- _TXCHAR type
- TINT type
- _TCHAR type
- TSCHAR type
- TEXT type
- TCHAR type
- TCHAR.H data types, mappings defined in
- generic-text data types
- _TINT type
- TUCHAR type
- _UNICODE constant
- TXCHAR type
- generic-text mappings
- _TSCHAR type
- T type
- mappings, generic-text
- _TUCHAR type
- MBCS data type
- _MBCS data type
- _TEXT type
- UNICODE constant
- _T type
ms.assetid: 2848121c-e51f-4b9b-a2e6-833ece4b0cb3
ms.openlocfilehash: b39e8563797ca0b57b54d2c85f851c8c45b29905
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50471445"
---
# <a name="using-generic-text-mappings"></a>Použití mapování obecného textu

**Specifické pro Microsoft**

Pro zjednodušení vývoje kódu pro různé mezinárodní trhy knihovny run-time Microsoft poskytuje specifické pro společnost Microsoft "obecného textu" mapování pro mnoho typů dat, rutiny a dalších objektů. Tato mapování jsou definovány v TCHAR. H. Tato mapování názvu můžete použít k zápisu obecný kód, který může být zkompilovány pro všechny tři druhy znakových sad: ASCII (SBCS), znakové sady MBCS a Unicode, v závislosti na konstanta manifestu, který definujete pomocí `#define` příkazu. Mapování obecného textu jsou rozšíření společnosti Microsoft, které nejsou kompatibilní ANSI.

### <a name="preprocessor-directives-for-generic-text-mappings"></a>Direktivy preprocesoru pro mapování obecného textu

|#define – direktiva|Kompilovaná verze|Příklad|
|--------------|----------------------|-------------|
|`_UNICODE`|Kódování Unicode (širokého znaku)|`_tcsrev` Mapuje se na `_wcsrev`|
|`_MBCS`|Vícebajtových znaků|`_tcsrev` Mapuje se na `_mbsrev`|
|None (výchozí: ani `_UNICODE` ani `_MBCS` definované)|SBCS (ASCII)|`_tcsrev` Mapuje se na `strrev`|

Například obecná textová funkce `_tcsrev`, definované v TCHAR. H, mapuje na `mbsrev` Pokud `MBCS` je definována v aplikaci nebo na `_wcsrev` Pokud `_UNICODE` byla definována. V opačném případě `_tcsrev` mapuje `strrev`.

Typ obecné textové datové `_TCHAR`také definované v TCHAR. H, mapuje na typ `char` Pokud `_MBCS` je definován na typ `wchar_t` Pokud `_UNICODE` je definována a zadejte `char` -li definována žádná konstanta. Tchar – jsou součástí jiné mapování datového typu. H ke zvýšení pohodlí programování, ale `_TCHAR` je typ, který je nejužitečnější.

### <a name="generic-text-data-type-mappings"></a>Mapování obecného textu datových typů

|Název typu obecné textové datové|SBCS (_UNICODE, _MBCS nejsou definovány)|_MBCS definováno|_UNICODE definováno|
|----------------------------------|--------------------------------------------|--------------------|-----------------------|
|`_TCHAR`|`char`|`char`|`wchar_t`|
|`_TINT`|`int`|`int`|`wint_t`|
|`_TSCHAR`|`signed char`|`signed char`|`wchar_t`|
|`_TUCHAR`|`unsigned char`|`unsigned char`|`wchar_t`|
|`_TXCHAR`|`char`|`unsigned char`|`wchar_t`|
|`_T` Nebo `_TEXT`|Žádný vliv (odebral preprocesoru)|Žádný vliv (odebral preprocesoru)|`L` (převede následující znak nebo řetězec k jeho protějšku Unicode)|

Úplný seznam mapování obecného textu rutiny, proměnných a dalších objektů, naleznete v tématu [mapování obecného textu](../c-runtime-library/generic-text-mappings.md).

Následující fragmenty kódu ukazují použití `_TCHAR` a `_tcsrev` mapování znakové sady MBCS, Unicode a knihovna SBCS modely.

```
_TCHAR *RetVal, *szString;
RetVal = _tcsrev(szString);
```

Pokud `MBCS` byl definován, preprocesor mapuje předchozí fragment v následujícím kódu:

```
char *RetVal, *szString;
RetVal = _mbsrev(szString);
```

Pokud `_UNICODE` byl definován, preprocesor mapuje stejného fragmentu v následujícím kódu:

```
wchar_t *RetVal, *szString;
RetVal = _wcsrev(szString);
```

Pokud ani `_MBCS` ani `_UNICODE` byl definován, preprocesor mapuje fragment kódu ASCII jednobajtové, následujícím způsobem:

```
char *RetVal, *szString;
RetVal = strrev(szString);
```

Můžete tak zapisovat, udržovat a kompilaci jednoho zdrojového kódu pro spuštění rutiny, které jsou specifické pro všechny tři druhy znakových sad.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Mapování obecného textu](../c-runtime-library/generic-text-mappings.md)<br/>
[Mapování datového typu](../c-runtime-library/data-type-mappings.md)<br/>
[Mapování konstant a globálních proměnných](../c-runtime-library/constant-and-global-variable-mappings.md)<br/>
[Mapování rutin](../c-runtime-library/routine-mappings.md)<br/>
[Ukázka programu obecného textu](../c-runtime-library/a-sample-generic-text-program.md)