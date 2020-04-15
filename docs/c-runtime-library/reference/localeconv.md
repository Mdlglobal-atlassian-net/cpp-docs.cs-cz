---
title: localeconv
ms.date: 4/2/2020
api_name:
- localeconv
- _o_localeconv
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-locale-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- localeconv
helpviewer_keywords:
- lconv type
- localeconv function
- locales, getting information on
ms.assetid: 7ecdb1f2-88f5-4037-a0e7-c754ab003660
ms.openlocfilehash: a617980d60b3a12c06b30aab6cd457792a1aa770
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342146"
---
# <a name="localeconv"></a>localeconv

Získá podrobné informace o nastavení národního prostředí.

## <a name="syntax"></a>Syntaxe

```C
struct lconv *localeconv( void );
```

## <a name="return-value"></a>Návratová hodnota

**localeconv** vrátí ukazatel na vyplněný objekt typu [struct lconv](../../c-runtime-library/standard-types.md). Hodnoty obsažené v objektu jsou zkopírovány z nastavení národního prostředí v místním úložišti podprocesu a mohou být přepsány následnými voláními **localeconv**. Změny provedené v hodnotách v tomto objektu nemění nastavení národního prostředí. Volání [setlocale](setlocale-wsetlocale.md) s *hodnotami kategorií* **LC_ALL**, **LC_MONETARY**nebo **LC_NUMERIC** přepsat obsah struktury.

## <a name="remarks"></a>Poznámky

Funkce **localeconv** získá podrobné informace o číselném formátování pro aktuální národní prostředí. Tyto informace jsou uloženy ve struktuře typu **lconv**. **Struktura lconv,** definované v LOCALE. H, obsahuje následující členy:

|Pole|Význam|
|-|-|
decimal_point,<br/>_W_decimal_point|Ukazatel na znak desetinné čárky pro nepeněžní množství.
thousands_sep,<br/>_W_thousands_sep|Ukazatel na znak, který odděluje skupiny číslic doleva od desetinné čárky pro nepeněžní množství.
grouping|Ukazatel na **celé číslo velikosti znaku,** které obsahuje velikost každé skupiny číslic v nepeněžních množstvích.
int_curr_symbol,<br/>_W_int_curr_symbol|Ukazatel na symbol mezinárodní měny pro aktuální národní prostředí. První tři znaky určují abecední symbol mezinárodní měny, jak je definován v *normě ISO 4217 pro standard reprezentace měny a fondů.* Čtvrtý znak (bezprostředně předcházející znak null) odděluje symbol mezinárodní měny od peněžního množství.
currency_symbol,<br/>_W_currency_symbol|Ukazatel na symbol místní měny pro aktuální národní prostředí.
mon_decimal_point,<br/>_W_mon_decimal_point|Ukazatel na znak desetinné čárky pro peněžní množství.
mon_thousands_sep,<br/>_W_mon_thousands_sep|Ukazatel na oddělovač pro skupiny číslic doleva od desetinného místa v peněžních množstvích.
mon_grouping|Ukazatel na **celé číslo velikosti znaku,** které obsahuje velikost každé skupiny číslic v peněžních množstvích.
positive_sign,<br/>_W_positive_sign|Řetězec označující znaménko pro nezáporná peněžní množství.
negative_sign,<br/>_W_negative_sign|Řetězec označující znaménko pro záporná peněžní množství.
int_frac_digits|Počet číslic napravo od desetinné čárky v mezinárodně formátovaných peněžních množstvích.
frac_digits|Počet číslic vpravo od desetinné čárky ve formátovaných peněžních množstvích.
p_cs_precedes|Pokud symbol měny předchází hodnotě pro nezáporné formátované peněžní množství, je nastavena na hodnotu 1. Nastavte hodnotu 0, pokud symbol následuje za hodnotou.
p_sep_by_space|Nastavte na hodnotu 1, pokud je symbol měny oddělen mezerou od hodnoty pro nezáporné formátované peněžní množství. Nastavte 0, pokud neexistuje žádné oddělení prostoru.
n_cs_precedes|Pokud symbol měny předchází hodnotě pro záporné formátované peněžní množství, je nastavena na hodnotu 1. Pokud symbol uspěje, nastavte hodnotu 0.
n_sep_by_space|Nastavte na 1, pokud je symbol měny oddělen mezerou od hodnoty pro záporné formátované peněžní množství. Nastavte 0, pokud neexistuje žádné oddělení prostoru.
p_sign_posn|Pozice kladného znaménko v nenegative formátovaných peněžních veličinách.
n_sign_posn|Pozice kladného znaménku v záporných formátovaných peněžních veličinách.

S výjimkou, jak je uvedeno, členy `char *` `wchar_t *` **lconv** struktury, které mají a verze jsou ukazatele na řetězce. Všechny z nich, které se rovnají **""** (nebo **L""** pro **wchar_t** <strong>\*</strong>) je buď nulové délky nebo nejsou podporovány v aktuálním národním prostředí. Všimněte si, že **decimal_point** a **_W_decimal_point** jsou vždy podporovány a nenulové délky.

Char **char** členy struktury jsou malé nezáporná čísla, nikoli znaky. Všechny z nich, které se rovná **CHAR_MAX** není podporován v aktuálním národním prostředí.

Hodnoty **seskupování** a **mon_grouping** jsou interpretovány podle následujících pravidel:

- **CHAR_MAX** - Neprovádějte žádné další seskupování.

- 0 - Použijte předchozí prvek pro každou zbývající číslici.

- *n* - Počet číslic, které tvoří aktuální skupinu. Další prvek je zkoumán k určení velikosti další skupiny číslic před aktuální skupinou.

Hodnoty **int_curr_symbol** jsou interpretovány podle následujících pravidel:

- První tři znaky určují abecední symbol mezinárodní měny definovaný v *kódech ISO 4217 pro standard Reprezentace měny a fondů.*

- Čtvrtý znak (bezprostředně předcházející znaknull) odděluje symbol mezinárodní měny od peněžního množství.

Hodnoty pro **p_cs_precedes** a **n_cs_precedes** jsou interpretovány podle následujících pravidel (pravidlo **n_cs_precedes** je v závorce):

- 0 - Symbol měny následuje hodnotu pro nezápornou (zápornou) formátovanou peněžní hodnotu.

- 1 - Symbol měny předchází hodnotě pro nezápornou (zápornou) formátovanou peněžní hodnotu.

Hodnoty pro **p_sep_by_space** a **n_sep_by_space** jsou interpretovány podle následujících pravidel (pravidlo **n_sep_by_space** je v závorce):

- 0 - Symbol měny je oddělen od hodnoty mezerou pro nezápornou (zápornou) formátovanou peněžní hodnotu.

- 1 - Neexistuje žádné oddělení mezer mezi symbolem měny a hodnotou pro nezápornou (zápornou) formátovanou peněžní hodnotu.

Hodnoty pro **p_sign_posn** a **n_sign_posn** jsou interpretovány podle následujících pravidel:

- 0 - Závorky surround množství a symbol měny.

- 1 - Znakový řetězec předchází množství a symbol měny.

- 2 - Znakový řetězec následuje symbol množství a měny.

- 3 - Znakový řetězec bezprostředně předchází symbolu měny.

- 4 - Znakový řetězec bezprostředně následuje symbol měny.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**localeconv**|\<locale.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven c run-time](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Viz také

[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Setlocale](../../preprocessor/setlocale.md)<br/>
[strcoll – funkce](../../c-runtime-library/strcoll-functions.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
