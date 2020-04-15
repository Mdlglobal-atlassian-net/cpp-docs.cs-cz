---
title: mbstowcs_s, _mbstowcs_s_l
ms.date: 4/2/2020
api_name:
- _mbstowcs_s_l
- mbstowcs_s
- _o__mbstowcs_s_l
- _o_mbstowcs_s
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-convert-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbstowcs_s_l
- mbstowcs_s
helpviewer_keywords:
- _mbstowcs_s_l function
- mbstowcs_s function
- mbstowcs_s_l function
ms.assetid: 2fbda953-6918-498f-b440-3e7b21ed65a4
ms.openlocfilehash: 07d694a7430f23e2f9600a5d2b147bcee2ef0e09
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338812"
---
# <a name="mbstowcs_s-_mbstowcs_s_l"></a>mbstowcs_s, _mbstowcs_s_l

Převede sekvenci vícebajtových znaků na odpovídající posloupnost širokých znaků. Verze [nástroje MBSTOWC, _mbstowcs_l](mbstowcs-mbstowcs-l.md) s vylepšeními zabezpečení popsanými v části Funkce zabezpečení v [crt](../../c-runtime-library/security-features-in-the-crt.md).

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
Počet převedených znaků.

*wcstr*<br/>
Adresa vyrovnávací paměti pro výsledný převedený řetězec celého znaku.

*sizeInWords*<br/>
Velikost vyrovnávací paměti *wcstr* ve slovech.

*mbstr*<br/>
Adresa posloupnosti nulových vícebajtových znaků.

*Počet*<br/>
Maximální počet širokých znaků pro uložení do vyrovnávací paměti *wcstr,* bez ukončující hodnoty null nebo [_TRUNCATE](../../c-runtime-library/truncate.md).

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu, kód chyby při selhání.

|Chybový stav|Vrácená hodnota a **chybné číslo**|
|---------------------|------------------------------|
|*wcstr* je **NULL** a *sizeInWords* > 0|**EINVAL**|
|*mbstr* je **null**|**EINVAL**|
|Cílová vyrovnávací paměť je příliš malá na to, aby obsahovala převedený řetězec (pokud není **_TRUNCATE** *počet;* viz poznámky níže)|**ERANGE**|
|*wcstr* není **NULL** a *sizeInWords* == 0|**EINVAL**|

Pokud dojde k některé z těchto podmínek, je vyvolána výjimka neplatného parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md) . Pokud je spuštění povoleno pokračovat, funkce vrátí kód chyby a nastaví **errno,** jak je uvedeno v tabulce.

## <a name="remarks"></a>Poznámky

Funkce **mbstowcs_s** převede řetězec vícebajtových znaků, na které se *vztahuje mbstr,* na široké znaky uložené ve vyrovnávací paměti, na kterou poukazuje *wcstr*. Převod bude pokračovat pro každý znak, dokud nebude splněna jedna z těchto podmínek:

- Je zjištěn vícebajtový znak null.

- Byl zjištěn neplatný vícebajtový znak.

- Počet širokých znaků uložených ve vyrovnávací paměti *wcstr* se rovná *počtu*.

Cílový řetězec je vždy ukončen nulou (i v případě chyby).

Pokud *count* je zvláštní hodnota [_TRUNCATE](../../c-runtime-library/truncate.md), **pak mbstowcs_s** převede tolik řetězce, jak se vejde do cílové vyrovnávací paměti, zatímco stále ponechává prostor pro zakončení null.

Pokud **mbstowcs_s** úspěšně převede zdrojový řetězec, vloží velikost v širokých znacích převedeného řetězce, včetně zakončení null, do *&#42;pReturnValue* (za předpokladu, že hodnota *pReturnValue* není **NULL).** K tomu dochází i v *případě, že wcstr* argument je **null** a poskytuje způsob, jak určit požadovanou velikost vyrovnávací paměti. Všimněte si, že pokud *wcstr* je **NULL**, *počet* je ignorována a *sizeInWords* musí být 0.

Pokud **mbstowcs_s** narazí na neplatný vícebajtový znak, vloží 0 v *&#42;pReturnValue*, nastaví cílovou vyrovnávací paměť na prázdný řetězec, nastaví **errno** na **EILSEQ**a vrátí **EILSEQ**.

Pokud se sekvence, na které se překrývají *mbstr* a *wcstr,* chování **mbstowcs_s** není definováno.

> [!IMPORTANT]
> Ujistěte se, že *wcstr* a *mbstr* se nepřekrývají a že *počet* správně odráží počet vícebajtových znaků převést.

**mbstowcs_s** používá aktuální národní prostředí pro jakékoli chování závislé na národním prostředí; **_mbstowcs_s_l** je totožný s tím rozdílem, že místo toho používá národní prostředí předané. Další informace naleznete v [tématu Locale](../../c-runtime-library/locale.md).

V jazyce C++ je použití těchto funkcí zjednodušeno přetížením šablony; přetížení lze odvodit délku vyrovnávací paměti automaticky (eliminuje potřebu zadat argument velikosti) a mohou automaticky nahradit starší, nezabezpečené funkce s jejich novější, bezpečné protějšky. Další informace naleznete [v tématu Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**mbstowcs_s**|\<stdlib.h>|
|**_mbstowcs_s_l**|\<stdlib.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
