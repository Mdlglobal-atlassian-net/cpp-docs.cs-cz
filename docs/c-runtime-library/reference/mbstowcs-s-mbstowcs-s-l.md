---
title: mbstowcs_s, _mbstowcs_s_l
ms.date: 11/04/2016
apiname:
- _mbstowcs_s_l
- mbstowcs_s
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _mbstowcs_s_l
- mbstowcs_s
helpviewer_keywords:
- _mbstowcs_s_l function
- mbstowcs_s function
- mbstowcs_s_l function
ms.assetid: 2fbda953-6918-498f-b440-3e7b21ed65a4
ms.openlocfilehash: 1caedc7e68bf080a5bad52a19ea6be2259a45264
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50646989"
---
# <a name="mbstowcss-mbstowcssl"></a>mbstowcs_s, _mbstowcs_s_l

Převede sekvence vícebajtových znaků na odpovídající pořadí širokých znaků. Verze [mbstowcs _mbstowcs_l –](mbstowcs-mbstowcs-l.md) s rozšířeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t mbstowcs_s(
   size_t *pReturnValue,
   wchar_t *wcstr,
   size_t sizeInWords,
   const char *mbstr,
   size_t count
);
errno_t _mbstowcs_s_l(
   size_t *pReturnValue,
   wchar_t *wcstr,
   size_t sizeInWords,
   const char *mbstr,
   size_t count,
   _locale_t locale
);
template <size_t size>
errno_t mbstowcs_s(
   size_t *pReturnValue,
   wchar_t (&wcstr)[size],
   const char *mbstr,
   size_t count
); // C++ only
template <size_t size>
errno_t _mbstowcs_s_l(
   size_t *pReturnValue,
   wchar_t (&wcstr)[size],
   const char *mbstr,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parametry

*pReturnValue*<br/>
Počet znaků, převodu.

*wcstr*<br/>
Adresa vyrovnávací paměti pro výsledný řetězec převedený širokého znaku.

*sizeInWords*<br/>
Velikost *wcstr* vyrovnávací paměti ve slovech.

*mbstr*<br/>
Adresa sekvence NULL byl ukončen vícebajtových znaků.

*Počet*<br/>
Maximální počet širokých znaků k ukládání *wcstr* vyrovnávací paměti, bez ukončujícího znaku null, nebo [_TRUNCATE](../../c-runtime-library/truncate.md).

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu, při selhání kód chyby.

|Chybový stav|Vrátí hodnotu a **errno**|
|---------------------|------------------------------|
|*wcstr* je **NULL** a *sizeInWords* > 0|**EINVAL**|
|*mbstr* je **NULL**|**EINVAL**|
|Cílová vyrovnávací paměť je příliš malá tak, aby obsahovala převedený řetězec (není-li *počet* je **_TRUNCATE**; viz poznámky níže)|**ERANGE**|
|*wcstr* není **NULL** a *sizeInWords* == 0|**EINVAL**|

Pokud některá z těchto podmínek dojde k je vyvolána výjimku neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md) . Pokud smí provádění pokračovat, funkce vrátí chybový kód a nastaví **errno** jak je uvedeno v tabulce.

## <a name="remarks"></a>Poznámky

**Mbstowcs_s** funkce převede řetězec vícebajtových znaků, na které odkazuje *mbstr* do široké znaky, které jsou uloženy ve vyrovnávací paměti, na které odkazuje *wcstr*. Převod bude pokračovat pro jednotlivé znaky, dokud nebude splněna jedna z těchto podmínek:

- Zjistil se vícebajtový znak null

- Zjistil se neplatný vícebajtový znak

- Počet širokých znaků, které jsou uložené v *wcstr* vyrovnávací paměti je rovno *počet*.

Cílový řetězec je vždy zakončený (i v případě chyby).

Pokud *počet* je zvláštní hodnota [_TRUNCATE](../../c-runtime-library/truncate.md), pak **mbstowcs_s** převede největší část řetězce, jako se vejde do cílové vyrovnávací paměti a stále ponechají prostor s hodnotou Null ukončovací znak.

Pokud **mbstowcs_s** úspěšně převede zdrojový řetězec uloží velikost v široké znaky převedený řetězec, včetně ukončovacího znaku null, do  *&#42;pReturnValue* (k dispozici *pReturnValue* není **NULL**). K tomu dojde i v případě, *wcstr* argument je **NULL** a poskytuje způsob, jak určit velikost požadované vyrovnávací paměti. Všimněte si, že pokud *wcstr* je **NULL**, *počet* se ignoruje, a *sizeInWords* musí být 0.

Pokud **mbstowcs_s** zaznamená platný vícebajtový znak, uloží je 0  *&#42;pReturnValue*, nastaví cílové vyrovnávací paměti na prázdný řetězec, nastaví **errno** k  **EILSEQ**a vrátí **EILSEQ**.

Pokud sekvence odkazované *mbstr* a *wcstr* překrývají, chování **mbstowcs_s** není definován.

> [!IMPORTANT]
> Ujistěte se, že *wcstr* a *mbstr* nepřekrývají a že *počet* správně odráží číslo k převodu vícebajtových znaků.

**mbstowcs_s** používá aktuální národní prostředí pro všechna závislá chování; **_mbstowcs_s_l –** je stejná s tím rozdílem, že používá národní prostředí předané. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

V jazyce C++ je použití těchto funkcí zjednodušeno díky přetížení šablon; přetížení mohou odvodit délku vyrovnávací paměti automaticky (tím eliminuje nutnost zadat argument velikosti) a dokážou automaticky nahradit starší, nezabezpečené funkce jejími novějšími, zabezpečené protějšky. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**mbstowcs_s –**|\<stdlib.h>|
|**_mbstowcs_s_l**|\<stdlib.h>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[MultiByteToWideChar](/windows/desktop/api/stringapiset/nf-stringapiset-multibytetowidechar)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
