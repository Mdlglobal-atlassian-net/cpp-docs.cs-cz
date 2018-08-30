---
title: localeconv | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- localeconv
apilocation:
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
apitype: DLLExport
f1_keywords:
- localeconv
dev_langs:
- C++
helpviewer_keywords:
- lconv type
- localeconv function
- locales, getting information on
ms.assetid: 7ecdb1f2-88f5-4037-a0e7-c754ab003660
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7c5f66975d8d9904d1a4a8f2d26d4fe98ecfdd40
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43223022"
---
# <a name="localeconv"></a>localeconv

Získá podrobné informace o nastavení národního prostředí.

## <a name="syntax"></a>Syntaxe

```C
struct lconv *localeconv( void );
```

## <a name="return-value"></a>Návratová hodnota

**localeconv** vrací ukazatel na objekt vyplněné typu [lconv – struktura](../../c-runtime-library/standard-types.md). Hodnoty obsažené v objektu jsou kopírovány z nastavení národního prostředí v místní úložiště vláken a může ji přepsat následných volání **localeconv**. Změny provedené na hodnoty v tomto objektu neprovádějte žádné změny nastavení národního prostředí. Volání [setlocale](setlocale-wsetlocale.md) s *kategorie* hodnoty **LC_ALL**, **LC_MONETARY**, nebo **LC_NUMERIC** přepište obsah struktury.

## <a name="remarks"></a>Poznámky

**Localeconv** funkce načte podrobné informace o formátování čísel pro aktuální národní prostředí. Tyto informace jsou uloženy v strukturu typu **lconv –**. **Lconv –** struktury definované v národním prostředí. H, obsahuje následující členy:

|Pole|Význam|
|-|-|
decimal_point –,<br/>_W_decimal_point|Ukazatel na znak pro neměnové množství desetinné čárky.
thousands_sep –,<br/>_W_thousands_sep|Ukazatel na znak, který odděluje skupiny číslic nalevo od desetinné čárky pro neměnové množství.
grouping|Ukazatel **char**– velikost celé číslo, které obsahuje velikost každé skupiny čísel v Neměnové množství.
int_curr_symbol,<br/>_W_int_curr_symbol|Ukazatel na symbol mezinárodní měny pro aktuální národní prostředí. První tři znaky zadat symbol měny mezinárodní, jak jsou definovány v *ISO 4217 kódy pro reprezentaci měn a fondů* standard. Čtvrtý (bezprostředně předcházející znak null) odděluje symbol měny mezinárodní od peněžních množství.
currency_symbol,<br/>_W_currency_symbol|Ukazatel na symbol místní měny pro aktuální národní prostředí.
mon_decimal_point,<br/>_W_mon_decimal_point|Ukazatel na znak pro peněžní množství desetinné čárky.
mon_thousands_sep,<br/>_W_mon_thousands_sep|Ukazatel na oddělovače skupin číslic nalevo od desetinné čárky v peněžní množství.
mon_grouping|Ukazatel **char**– velikost celé číslo, které obsahuje velikost každé skupiny čísel v peněžní množství.
positive_sign –,<br/>_W_positive_sign|Řetězec označující znaménko nezáporné peněžní množství.
negative_sign –,<br/>_W_negative_sign|Řetězec označující znaménko záporné peněžní množství.
int_frac_digits|Počet číslic vpravo od desetinné čárky v mezinárodním měřítku formátovaný peněžní množství.
frac_digits|Počet číslic vpravo od desetinné čárky v formátovaný peněžní množství.
p_cs_precedes|Nastavte na 1, pokud hodnota pro nezáporné formátovaný peněžní množství předchází symbol měny. Nastavte na hodnotu 0, pokud následuje symbol za hodnotou.
p_sep_by_space|Nastavte na 1, pokud je symbol měny z hodnoty pro nezáporné formátovaný peněžní množství odděleny mezerou. Nastavte na hodnotu 0, pokud neexistuje žádný prostor oddělení.
n_cs_precedes|Nastavte na 1, pokud hodnota záporná formátovaný peněžní množství předchází symbol měny. Nastavte na hodnotu 0, pokud symbol úspěšné hodnotu.
n_sep_by_space|Nastavte na 1, pokud je symbol měny z hodnoty pro záporné formátovaný peněžní množství odděleny mezerou. Nastavte na hodnotu 0, pokud neexistuje žádný prostor oddělení.
p_sign_posn|Pozice kladné znaménko v nezáporné ve formátu peněžní množství.
n_sign_posn|Pozice kladné znaménko v záporné hodnoty ve formátu peněžní množství.

S výjimkou případů zadaný, členem **lconv –** struktury, která má `char *` a `wchar_t *` verze jsou ukazatele na řetězce. Některé z těchto, které se rovná **""** (nebo **L ""** pro **wchar_t** <strong>\*</strong>) je buď nulovou délku, nebo se nepodporuje v aktuálním národní prostředí. Všimněte si, že **decimal_point –** a **_W_decimal_point** jsou vždy podporované a nenulovou délkou.

**Char** členy struktury jsou nezáporná čísly, nikoli znaky. Některé z těchto, které se rovná **CHAR_MAX** se nepodporuje v aktuálním národním prostředí.

Hodnoty **seskupení** a **mon_grouping** jsou interpretovány dle následujících pravidel:

- **CHAR_MAX** -nebude provádět žádné další seskupení.

- Pro každý zbývající číslice 0 – použijte předchozí prvek.

- *n* – počet číslic, které společně tvoří aktuální skupinu. Další prvek je prověřit, abyste zjistili velikost další skupiny číslic před aktuální skupinou.

Hodnoty pro **int_curr_symbol** jsou interpretovány dle následujících pravidel:

- První tři znaky zadat symbol měny mezinárodní, jak jsou definovány v *ISO 4217 kódy pro reprezentaci měn a fondů* standard.

- Čtvrtý znak (bezprostředně předchází znak null) odděluje symbol měny mezinárodní od peněžních množství.

Hodnoty pro **p_cs_precedes** a **n_cs_precedes** jsou interpretovány dle následujících pravidel ( **n_cs_precedes** pravidlo je v závorkách):

- 0 – symbol měny se řídí hodnota nezáporné (negativní) formátovaná peněžní hodnota.

- 1 - symbol měny předchází hodnotu nezáporné (negativní) formátovaná peněžní hodnota.

Hodnoty pro **p_sep_by_space** a **n_sep_by_space** jsou interpretovány dle následujících pravidel ( **n_sep_by_space** pravidlo je v závorkách):

- 0 – symbol měny je oddělená od hodnoty místo pro nezáporné (negativní) formátovaná peněžní hodnota.

- 1 – neexistuje žádný prostor oddělení mezi symbol měny a hodnota pro nezáporné (negativní) formátovaný peněžní hodnota.

Hodnoty pro **p_sign_posn** a **n_sign_posn** jsou interpretovány dle následujících pravidel:

- 0 – závorky před a za symbol množství a měny.

- 1 – přihlášení řetězec předchází symbol množství a měny.

- 2 – znak řetězec následuje symbol množství a měny.

- 3 – znak řetězec bezprostředně předchází symbol měny.

- 4 - sign řetězec bezprostředně následuje symbol měny.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**localeconv**|\<Locale.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Viz také:

[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[setlocale](../../preprocessor/setlocale.md)<br/>
[strcoll – funkce](../../c-runtime-library/strcoll-functions.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
