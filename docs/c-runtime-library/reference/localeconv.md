---
title: localeconv
ms.date: 11/04/2016
api_name:
- localeconv
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
ms.openlocfilehash: ca7113903e1ed6e9ffb94bef79beba41e09bfb71
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953361"
---
# <a name="localeconv"></a>localeconv

Získá podrobné informace o nastavení národního prostředí.

## <a name="syntax"></a>Syntaxe

```C
struct lconv *localeconv( void );
```

## <a name="return-value"></a>Návratová hodnota

**localeconv** vrací ukazatel na vyplněný objekt typu [struct lconv](../../c-runtime-library/standard-types.md). Hodnoty obsažené v objektu jsou zkopírovány z nastavení národního prostředí v místním úložišti vlákna a lze je přepsat následnými voláními **localeconv**. Změny provedené v hodnotách v tomto objektu nemění nastavení národního prostředí. Volání funkce [setlocale](setlocale-wsetlocale.md) s hodnotami *kategorie* **LC_ALL**, **LC_MONETARY**nebo **LC_NUMERIC** přepisují obsah struktury.

## <a name="remarks"></a>Poznámky

Funkce **localeconv** získá podrobné informace o číselném formátování pro aktuální národní prostředí. Tyto informace jsou uloženy ve struktuře typu **lconv**. Struktura **lconv** definovaná v národním prostředí. H obsahuje následující členy:

|Pole|Význam|
|-|-|
decimal_point,<br/>_W_decimal_point|Ukazatel na znak desetinné čárky pro nepeněžní množství.
thousands_sep,<br/>_W_thousands_sep|Ukazatel na znak, který odděluje skupiny číslic nalevo od desetinné čárky pro nepeněžní množství.
grouping|Ukazatel na celé číslo velikosti **znaků**, které obsahuje velikost každé skupiny číslic v nepeněžních množstvích.
int_curr_symbol,<br/>_W_int_curr_symbol|Ukazatel na symbol mezinárodní měny pro aktuální národní prostředí První tři znaky určují abecední symbol mezinárodní měny, jak je definovaný v *kódech ISO 4217 pro reprezentace standardu Currency a fondů* . Čtvrtý znak (bezprostředně předchozí znak null) odděluje mezinárodní symbol měny od peněžního množství.
currency_symbol,<br/>_W_currency_symbol|Ukazatel na symbol místní měny pro aktuální národní prostředí
mon_decimal_point,<br/>_W_mon_decimal_point|Ukazatel na znak desetinné čárky pro peněžní množství.
mon_thousands_sep,<br/>_W_mon_thousands_sep|Ukazatel na oddělovač pro skupiny číslic nalevo od desetinného místa v peněžních množstvích.
mon_grouping|Ukazatel na celé číslo velikosti **znaků**, které obsahuje velikost každé skupiny číslic v peněžních množstvích.
positive_sign,<br/>_W_positive_sign|Řetězec označující znaménko pro nezáporné peněžní množství.
negative_sign,<br/>_W_negative_sign|Řetězec označující znaménko pro záporné peněžní množství.
int_frac_digits|Počet číslic vpravo od desetinné čárky v mezinárodně formátovaných peněžních množství.
frac_digits|Počet číslic vpravo od desetinné čárky ve formátovaných peněžních množstvích.
p_cs_precedes|Nastavte na hodnotu 1, pokud symbol měny předchází hodnotě nezáporného naformátovaného peněžního množství. Nastavte na 0, pokud symbol sleduje hodnotu.
p_sep_by_space|Nastavte na hodnotu 1, pokud je symbol měny oddělen mezerou od hodnoty pro nezáporné naformátované peněžní množství. Nastavte na 0, pokud není odděleno místo.
n_cs_precedes|Nastavte na 1, pokud symbol měny předchází hodnotě pro záporné naformátované peněžní množství. Nastavte na hodnotu 0, pokud symbol uspěje.
n_sep_by_space|Nastavte na hodnotu 1, pokud je symbol měny oddělen mezerou od hodnoty pro záporné naformátované peněžní množství. Nastavte na 0, pokud není odděleno místo.
p_sign_posn|Pozice kladného přihlašování nezáporných peněžních množství.
n_sign_posn|Pozice kladného znaménka v záporném naformátovaném peněžním množství.

S výjimkou určení, členové struktury **lconv** , které mají `char *` a `wchar_t *` verze, jsou ukazatele na řetězce. Jakýkoli z nich, který se rovná **""** (nebo **L ""** pro **wchar_t** <strong>\*</strong>") má buď nulovou délku, nebo není v aktuálním národním prostředí podporován. Všimněte si, že **decimal_point** a **_W_decimal_point** jsou vždycky podporované a nenulovou délkou.

Členy **znaku** struktury jsou malá nezáporná čísla, nikoli znaky. Některé z těchto těch, které se rovnají **CHAR_MAX** , se v aktuálním národním prostředí nepodporují.

Hodnoty **seskupení** a **mon_grouping** jsou interpretovány podle následujících pravidel:

- **CHAR_MAX** – neprovádějte žádné další seskupení.

- 0 – použít předchozí prvek pro každou zbývající číslici.

- *n* -počet číslic, které tvoří aktuální skupinu. Další prvek je přezkoumán za účelem určení velikosti další skupiny číslic před aktuální skupinou.

Hodnoty pro **int_curr_symbol** se interpretují podle následujících pravidel:

- První tři znaky určují abecední symbol mezinárodní měny, jak je definován v *kódu ISO 4217 pro reprezentaci standardu Currency a fondů* .

- Čtvrtý znak (bezprostředně před znakem null) odděluje mezinárodní symbol měny od peněžního množství.

Hodnoty pro **p_cs_precedes** a **n_cs_precedes** se interpretují podle následujících pravidel (pravidlo **n_cs_precedes** je v závorkách):

- 0 – symbol měny následuje hodnota nezáporné (záporné) formátované peněžní hodnoty.

- 1 – symbol měny předchází hodnotě nezáporné (záporné) formátované peněžní hodnoty.

Hodnoty pro **p_sep_by_space** a **n_sep_by_space** se interpretují podle následujících pravidel (pravidlo **n_sep_by_space** je v závorkách):

- 0 – symbol měny je od hodnoty oddělen mezerou pro nezáporné (záporné) naformátovaná peněžní hodnota.

- 1 – mezi symbolem měny a hodnotou nezáporné (záporné) formátované peněžní hodnoty není žádné oddělení.

Hodnoty pro **p_sign_posn** a **n_sign_posn** se interpretují podle následujících pravidel:

- 0 – závorky jsou obklopené množství a symbol měny.

- 1 – řetězec znaménka předchází množství a symbolu měny.

- 2 – řetězec podepisuje podle množství a symbolu měny.

- 3 – znaménko řetězce bezprostředně před symbolem měny.

- 4 – podepište řetězec ihned po symbolu měny.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**localeconv**|\<locale. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Viz také:

[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[setlocale](../../preprocessor/setlocale.md)<br/>
[strcoll – funkce](../../c-runtime-library/strcoll-functions.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
