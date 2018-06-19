---
title: localeconv – | Microsoft Docs
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
ms.openlocfilehash: fe3cc75430dfa9bb2f4c5513f4b2ba5a2fd1c4c9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405247"
---
# <a name="localeconv"></a>localeconv

Získá podrobné informace o nastavení národního prostředí.

## <a name="syntax"></a>Syntaxe

```C
struct lconv *localeconv( void );
```

## <a name="return-value"></a>Návratová hodnota

**localeconv –** vrací ukazatel na objekt vyplněné typu [lconv – struktura](../../c-runtime-library/standard-types.md). Hodnoty obsažené v objektu, se zkopírují z nastavení národního prostředí v místní úložiště vláken a může ji přepsat následující volání **localeconv –**. Změny provedené na hodnoty v tomto objektu neměňte nastavení národního prostředí. Volání [setlocale](setlocale-wsetlocale.md) s *kategorie* hodnoty **LC_ALL**, **lc_monetary –**, nebo **lc_numeric –** přepište obsah struktury.

## <a name="remarks"></a>Poznámky

**Localeconv –** funkce získá podrobné informace o formátování čísel pro aktuální národní prostředí. Tyto informace jsou uloženy ve struktuře typu **lconv –**. **Lconv –** struktuře, definované v národním prostředí. H, obsahuje následující členy:

|Pole|Význam|
|-|-|
decimal_point –,<br/>_W_decimal_point|Ukazatel na desetinnou znak Neměnové počty.
thousands_sep –,<br/>_W_thousands_sep|Ukazatel na znak, který odděluje skupiny číslic nalevo od desetinné čárky Neměnové počty.
grouping|Ukazatel na **char**– velikost celé číslo, které obsahuje velikost každé skupiny číslic v Neměnové počty.
int_curr_symbol,<br/>_W_int_curr_symbol|Ukazatel na symbol mezinárodní měna pro aktuální národní prostředí. Prvních tří znaků zadejte symbol abecedním mezinárodní měny, jak jsou definovány v *ISO 4217 kódy pro reprezentaci měny a fondy* standardní. Čtvrtý (poslední znak hodnoty null) odděluje symbol mezinárodní měny od peněžní množství.
currency_symbol,<br/>_W_currency_symbol|Ukazatel na místní měně symbol pro aktuální národní prostředí.
mon_decimal_point,<br/>_W_mon_decimal_point|Ukazatel na desetinnou znak peněžní počty.
mon_thousands_sep,<br/>_W_mon_thousands_sep|Ukazatel na oddělovač pro skupiny číslic nalevo od desetinné čárky v peněžním počty.
mon_grouping|Ukazatel na **char**– velikost celé číslo, které obsahuje velikost každé skupiny číslic v peněžním počty.
positive_sign –,<br/>_W_positive_sign|Řetězec představující přihlašovací nezáporné peněžní počty.
negative_sign –,<br/>_W_negative_sign|Řetězec představující přihlašovací záporné peněžní počty.
int_frac_digits|Počet číslic vpravo od desetinné čárky v mezinárodní úrovni formátovaný peněžní počty.
frac_digits|Počet číslic vpravo od desetinné čárky v formátovaný peněžní počty.
p_cs_precedes|Nastavte na hodnotu 1, pokud hodnota pro nezáporné formátovaný peněžní množství předchází symbolu měny. Nastavte na hodnotu 0, pokud symbol dodržuje hodnotu.
p_sep_by_space|Pokud symbolu měny je oddělená místo z hodnoty pro množství nezáporné formátovaný peněžní nastavena na 1. Nastavte na hodnotu 0, pokud neexistuje žádné místo oddělení.
n_cs_precedes|Nastavte na hodnotu 1, pokud hodnota záporné formátovaný peněžní množství předchází symbolu měny. Nastavte na hodnotu 0, pokud symbol je úspěšné hodnotu.
n_sep_by_space|Nastavte na hodnotu 1, pokud symbolu měny je oddělená místo z hodnoty pro záporné formátovaný peněžní množství. Nastavte na hodnotu 0, pokud neexistuje žádné místo oddělení.
p_sign_posn|Pozice kladné znaménko v nezáporné ve formátu peněžní počty.
n_sign_posn|Pozice kladné znaménko v záporná formátovaný peněžní množství.

S výjimkou jako zadaný, členy **lconv –** struktury, která má `char *` a `wchar_t *` verze jsou ukazatele na řetězce. Některý z těchto, které se rovná **""** (nebo **L ""** pro **wchar_t \*** ) je buď nulovou délku nebo není podporována v aktuální národní prostředí. Všimněte si, že **decimal_point –** a **_W_decimal_point** jsou podporované vždycky a délky nenulové hodnoty.

**Char** členů struktury jsou malé nezáporné čísla, není znaků. Některý z těchto, které se rovná **char_max –** není podporována v aktuální národní prostředí.

Hodnoty **seskupení** a **mon_grouping** se interpretují podle následujících pravidel:

- **Char_max –** -Neprovádět další seskupení.

- 0 – pomocí předchozí elementu pro každý zbývající číslic.

- *n* -počet číslic, které tvoří aktuální skupiny. Další prvek je ověřuje velikosti další skupiny číslic před aktuální skupiny.

Hodnoty pro **int_curr_symbol** se interpretují podle následujících pravidel:

- Prvních tří znaků zadejte symbol abecedním mezinárodní měny, jak jsou definovány v *ISO 4217 kódy pro reprezentaci měny a fondy* standardní.

- Čtvrtý znak (bezprostředně předcházející znak hodnoty null) odděluje symbol mezinárodní měny od peněžní množství.

Hodnoty pro **p_cs_precedes** a **n_cs_precedes** se interpretují podle následujících pravidel ( **n_cs_precedes** pravidlo je v závorkách):

- 0 – symbolu měny řídí hodnota nezáporné (záporná) formátovaný peněžní hodnota.

- 1 - symbol měny předchází hodnotu nezáporné (záporná) formátovaný peněžní hodnota.

Hodnoty pro **p_sep_by_space** a **n_sep_by_space** se interpretují podle následujících pravidel ( **n_sep_by_space** pravidlo je v závorkách):

- 0 – symbolu měny je oddělená od hodnoty místa pro nezáporné (záporná) formátovaný peněžní hodnota.

- 1 - neexistuje žádné místo oddělení mezi symbolu měny a hodnotu nezáporné (záporná) formátovaný peněžní hodnota.

Hodnoty pro **p_sign_posn** a **n_sign_posn** se interpretují podle následujících pravidel:

- 0 – závorkách obklopit symbol množství a měny.

- 1 - přihlašovací řetězec předchází symbol množství a měny.

- 2 – přihlašovací řetězec následuje symbol množství a měny.

- 3 - řetězec přihlašovací okamžitě předchází symbolu měny.

- 4 - přihlašovací řetězec okamžitě symbolu měny způsobem.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**localeconv**|\<Locale.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Viz také

[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[setlocale](../../preprocessor/setlocale.md)<br/>
[strcoll – funkce](../../c-runtime-library/strcoll-functions.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
